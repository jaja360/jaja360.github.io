---

title: "INF4170: Table d'alias des registres"
summary: "Introduction à la table d'alias des registres"
authors: []
tags: [INF4170]
categories: []
date: '2025-04-01T00:00:00Z'
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: black
  highlight_style: dracula
  reveal_options:
    slide_number: c/t
    mouse_wheel: true
    pdf_separate_fragments: false

---

## Table d'alias des registres
### INF4170: Architecture des ordinateurs

---

### Comparaison de performance

```c++
#include "ibp.hpp"
constexpr uint64_t Count = 1024 * 1024 * 1024;  // 1 GiO

extern "C" void FctAdd(uint64_t Count);
extern "C" void FctMovAdd(uint64_t Count);

int main() {
  ibp::comparisonTester({
      {"FctAdd",    [&]() { FctAdd(Count); }},
      {"FctMovAdd", [&]() { FctMovAdd(Count); }}
  }, Count, Count, 1);
}
```

---

```asm
FctAdd:
align 64
.loop:
    add rcx, 1
    add rcx, 1
    dec rdi
    jnz .loop
    ret
```

```asm
FctMovAdd:
align 64
.loop:
    mov rcx, rax
    add rcx, 1
    mov rcx, rax
    add rcx, 1
    dec rdi
    jnz .loop
    ret
```

---

### Quiz

Quelle fonction est la plus rapide?

1. `FctAdd` est plus rapide
2. `FctMovAdd` est plus rapide
3. Les deux fonctions ont la même vitesse

---

### Évaluation empirique

```csv
    Label   AvgCycles  GB/s  Cycles/item  Speedup
   FctAdd  1679822459  2.62         1.56    1.00x
FctMovAdd   840759587  5.23         0.78    2.00x
```

Qu'est-ce qui explique la différence de performance?

---

{{< slide background-image="./figs/zen4.png" background-size="contain" background-position="center" background-repeat="no-repeat" >}}

---

{{< slide background-image="./figs/RAT.svg" background-size="35%" background-position="center" background-repeat="no-repeat" >}}

---
