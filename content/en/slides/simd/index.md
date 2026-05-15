---
title: "INF5171: Instructions SIMD"
summary: "Introduction au parallélisme de données par instructions SIMD"
authors:
  - me
tags: [INF5171]
categories: []
date: '2026-05-14'
slides:
  theme: black
  highlight_style: dracula
  diagram: true
  reveal_options:
    slide_number: c/t
    mouse_wheel: true
    pdf_separate_fragments: false
  branding:
    title:
      show: true
      position: "bottom-left"
    author:
      show: true
      position: "bottom-center"

---

## Instructions SIMD
### INF5171: Programmation concurrente et parallèle

---

### Plan de cours

- Introduction et rappels
- Parallélisme de tâches
- Parallélisme de données
- Hiérarchie de mémoire
- **Instructions SIMD**
- Calcul distribué
- Mesures de performance
- Vérification des programmes parallèles
- Calcul sur processeurs graphiques (GPU)

---

### Version scalaire

Hypothèse: `a`, `b` et `c` sont des tableaux de `float` distincts.

```c++
for (uint64_t i = 0; i < n; ++i) {
  c[i] = a[i] + b[i];
}
```

<div class="data-parallel-note">
  <ul>
    <li>Chaque itération est indépendante</li>
    <li>On peut faire les additions en parallèle</li>
  </ul>
  <div>
    Parallélisme<br>de données
  </div>
</div>

- Déjà vu: découper le tableau en morceaux et les traiter séparément
- Aujourd'hui: paralléliser en utilisant un seul fil d'exécution

---

{{< slide background-image="figs/zen4.png" background-size="contain" background-position="center" background-repeat="no-repeat" >}}

---

### Fausse bonne idée matérielle

- Ajoutons plus d'unités flottantes scalaires dans le coeur.

```mermaid
flowchart LR
  L1i["Cache d'instructions"] -->|"32 o/c; 4 i/c"| Decode["Décodage"]
  Decode -->|"6 µops/c"| Schedule["Ordonnancement"]
  Schedule --> FPU["Unités flottantes calcul/mémoire"]
```

{{% fragment %}}
- Il faut décoder/planifier/exécuter plus d'instructions par cycle.
- Il faut aussi charger `a[i]`, charger `b[i]`, puis écrire `c[i]`.
- Le débit du flot d'instructions est un goulot d'étranglement.
{{% /fragment %}}

---

### Un registre, plusieurs valeurs

```text
Registre scalaire 32 bits

[        float        ]
```

{{% fragment %}}
```text
Registre vectoriel 256 bits

[ float ][ float ][ float ][ float ][ float ][ float ][ float ][ float ]
```
{{% /fragment %}}

---

### Une instruction, plusieurs opérations

- Augmenter le travail fait **par instruction**.
- **Une seule instruction** effectue plusieurs opérations indépendantes.

<div class="code-columns simd-idea">
<div>

```text
        [a0 a1 a2 a3 a4 a5 a6 a7] // ymm0
      + [b0 b1 b2 b3 b4 b5 b6 b7] // ymm1
      ---------------------------
        [c0 c1 c2 c3 c4 c5 c6 c7] // ymm2
```

</div>
<div>

```asm
vaddps ymm2, ymm0, ymm1
```

- `ps`: *packed single-precision*
- `ymm`: registre vectoriel 256 bits

</div>
</div>

---

### Registres x86-64

<table class="register-table">
  <thead>
    <tr>
      <th>Vue</th>
      <th>Taille</th>
      <th>Extension</th>
      <th>Année</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>al</code></td>
      <td><span class="register-meter"><span class="register-bar" style="--w: 1"></span><span class="register-size">1 o</span></span></td>
      <td>Intel 8086</td>
      <td>1978</td>
    </tr>
    <tr>
      <td><code>ax</code></td>
      <td><span class="register-meter"><span class="register-bar" style="--w: 2"></span><span class="register-size">2 o</span></span></td>
      <td>Intel 8086</td>
      <td>1978</td>
    </tr>
    <tr>
      <td><code>eax</code></td>
      <td><span class="register-meter"><span class="register-bar" style="--w: 4"></span><span class="register-size">4 o</span></span></td>
      <td>IA-32 (i386)</td>
      <td>1985</td>
    </tr>
    <tr>
      <td><code>rax</code></td>
      <td><span class="register-meter"><span class="register-bar" style="--w: 8"></span><span class="register-size">8 o</span></span></td>
      <td>x86-64</td>
      <td>2003</td>
    </tr>
    <tr class="register-vector-start">
      <td><code>xmm0</code></td>
      <td><span class="register-meter"><span class="register-bar vector" style="--w: 16"></span><span class="register-size">16 o</span></span></td>
      <td>SSE</td>
      <td>1999</td>
    </tr>
    <tr>
      <td><code>ymm0</code></td>
      <td><span class="register-meter"><span class="register-bar vector" style="--w: 32"></span><span class="register-size">32 o</span></span></td>
      <td>AVX</td>
      <td>2011</td>
    </tr>
    <tr>
      <td><code>zmm0</code></td>
      <td><span class="register-meter"><span class="register-bar vector" style="--w: 64"></span><span class="register-size">64 o</span></span></td>
      <td>AVX-512</td>
      <td>2016</td>
    </tr>
  </tbody>
</table>

<div class="register-note">
  <span><strong>Scalaires</strong><br> 16 registres généraux 64 bits</span>
  <span><strong>SSE/AVX/AVX2</strong><br> 16 registres vectoriels</span>
  <span><strong>AVX-512</strong><br> 32 registres vectoriels</span>
</div>

---

### Version SIMD (vectorielle)

<div class="code-columns">
<div>

Pseudo-C++

```c++
for (uint64_t i = 0; i < n; i += 8) {
  // c[i] = a[i] + b[i]
  va = load8(&a[i]);
  vb = load8(&b[i]);
  vc = add8(va, vb);
  store8(&c[i], vc);
}
```

</div>
<div>

Pseudo-assembleur x86-64 équivalent

```asm
.Lloop:
vmovups ymm0, [a + 4*i]
vmovups ymm1, [b + 4*i]
vaddps  ymm2, ymm0, ymm1
vmovups [c + 4*i], ymm2
add     i, 8
cmp     i, n
jl      .Lloop
```

</div>
</div>

---

### Ce que SIMD change

| Scalaire                          | SIMD                                          |
| :--------:                        | :----:                                        |
| 1 addition par instruction        | jusqu'à 16 opérations `float` par instruction |
| Plusieurs instructions identiques | Une instruction vectorielle                   |
| Peu de données par instruction    | Plus de travail par instruction               |

---

### En pratique

- Applications typiques:
    - filtres image/audio, compression, simulation, apprentissage machine.
- Pour les boucles simples, le compilateur peut générer des instructions SIMD automatiquement.
    - Options utiles: `-O3 -march=native`.
    - Condition: prouver l'absence de dépendances entre itérations.
- Sinon: réécriture du code, [OpenMP SIMD](https://www.openmp.org/spec-html/5.0/openmpsu42.html)
  ou [*intrinsics*](https://www.intel.com/content/www/us/en/docs/intrinsics-guide/index.html).

---

### À retenir

- SIMD est du parallélisme de données à l'intérieur d'un coeur.
- Il exploite des opérations identiques sur des données indépendantes.
- Il réduit la pression sur le flot d'instructions.
- Le gain réel dépend aussi des accès mémoire.
- Il complète les fils d'exécution, il ne les remplace pas.
