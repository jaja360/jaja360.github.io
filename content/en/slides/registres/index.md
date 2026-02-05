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

{{< slide background-image="figs/zen4.png" background-size="contain" background-position="center" background-repeat="no-repeat" >}}

---

{{< slide background-image="figs/RAT.svg" background-size="contain" background-position="center" background-repeat="no-repeat" >}}


---

RCX:&nbsp;&nbsp;$P_0$

| Instruction |  Dest  |  Src  |
|:-----------:|-------:|------:|
|  add rcx, 1 |        |       |
|  add rcx, 1 |        |       |
|  add rcx, 1 |        |       |
|  add rcx, 1 |        |       |
|     ...     |        |       |

---

RCX:&nbsp;&nbsp;$\cancel{P_0},~P_1$

| Instruction |  Dest  |  Src  |
|:-----------:|-------:|------:|
|  add rcx, 1 | $P_1$  | $P_0$ |
|  add rcx, 1 |        |       |
|  add rcx, 1 |        |       |
|  add rcx, 1 |        |       |
|     ...     |        |       |

---

RCX:&nbsp;&nbsp;$\cancel{P_0},~\cancel{P_1},~P_2$

 | Instruction   | Dest                                     | Src                                      |
 | :-----------: | -------:                                 | ------:                                  |
 | add rcx, 1    | <span style="color:#445fe8">$P_1$</span> | $P_0$                                    |
 | add rcx, 1    | $P_2$                                    | <span style="color:#445fe8">$P_1$</span> |
 | add rcx, 1    |                                          |                                          |
 | add rcx, 1    |                                          |                                          |
 | ...           |                                          |                                          |

---

RCX:&nbsp;&nbsp;$\cancel{P_0},~\cancel{P_1},$&nbsp;&nbsp;$\cancel{P_2},~P_3$

 | Instruction   | Dest                                     | Src                                      |
 | :-----------: | -------:                                 | ------:                                  |
 | add rcx, 1    | <span style="color:#445fe8">$P_1$</span> | $P_0$                                    |
 | add rcx, 1    | <span style="color:#fcaa67">$P_2$</span> | <span style="color:#445fe8">$P_1$</span> |
 | add rcx, 1    | $P_3$                                    | <span style="color:#fcaa67">$P_2$</span> |
 | add rcx, 1    |                                          |                                          |
 | ...           |                                          |                                          |

---

RCX:&nbsp;&nbsp;$\cancel{P_0}$,&nbsp;&nbsp;$\cancel{P_1}$,&nbsp;&nbsp;$\cancel{P_2}$,&nbsp;&nbsp;$\cancel{P_3},~P_4$

 | Instruction   | Dest                                     | Src                                      |
 | :-----------: | -------:                                 | ------:                                  |
 | add rcx, 1    | <span style="color:#445fe8">$P_1$</span> | $P_0$                                    |
 | add rcx, 1    | <span style="color:#fcaa67">$P_2$</span> | <span style="color:#445fe8">$P_1$</span> |
 | add rcx, 1    | <span style="color:#b0413e">$P_3$</span> | <span style="color:#fcaa67">$P_2$</span> |
 | add rcx, 1    | $P_4$                                    | <span style="color:#b0413e">$P_3$</span> |
 | ...           | ...                                      | ...                                      |

---

RAX:&nbsp;&nbsp;$P_0$&nbsp;&nbsp;&nbsp;&nbsp;RCX:&nbsp;&nbsp;$\ast$

 | Instruction  | Dest     | Src     |
 | :----------- | -------: | ------: |
 | mov rcx, rax |          |         |
 | add rcx, 1   |          |         |
 | mov rcx, rax |          |         |
 | add rcx, 1   |          |         |
 | ...          |          |         |

---

RAX:&nbsp;&nbsp;$P_0$&nbsp;&nbsp;&nbsp;&nbsp;RCX:&nbsp;&nbsp;$\cancel{\ast},~P_1$

 | Instruction  | Dest     | Src     |
 | :----------- | -------: | ------: |
 | mov rcx, rax | $P_1$    | $P_0$   |
 | add rcx, 1   |          |         |
 | mov rcx, rax |          |         |
 | add rcx, 1   |          |         |
 | ...          |          |         |

---

RAX:&nbsp;&nbsp;$P_0$&nbsp;&nbsp;&nbsp;&nbsp;RCX:&nbsp;&nbsp;$\cancel{\ast},~\cancel{P_1},~P_2$

 | Instruction  | Dest                                     | Src                                      |
 | :----------- | -------:                                 | ------:                                  |
 | mov rcx, rax | <span style="color:#445fe8">$P_1$</span> | $P_0$                                    |
 | add rcx, 1   | $P_2$                                    | <span style="color:#445fe8">$P_1$</span> |
 | mov rcx, rax |                                          |                                          |
 | add rcx, 1   |                                          |                                          |
 | ...          |                                          |                                          |

---

RAX:&nbsp;&nbsp;$P_0$&nbsp;&nbsp;&nbsp;&nbsp;RCX:&nbsp;&nbsp;$\cancel{\ast},~\cancel{P_1}$,&nbsp;&nbsp;$\cancel{P_2},~P_3$

 | Instruction  | Dest                                     | Src                                      |
 | :----------- | -------:                                 | ------:                                  |
 | mov rcx, rax | <span style="color:#445fe8">$P_1$</span> | $P_0$                                    |
 | add rcx, 1   | $P_2$                                    | <span style="color:#445fe8">$P_1$</span> |
 | mov rcx, rax | $P_3$                                    | $P_0$                                    |
 | add rcx, 1   |                                          |                                          |
 | ...          |                                          |                                          |

---

RAX:&nbsp;&nbsp;$P_0$&nbsp;&nbsp;&nbsp;&nbsp;RCX:&nbsp;&nbsp;$\cancel{\ast},~\cancel{P_1}$,&nbsp;&nbsp;$\cancel{P_2}$,&nbsp;&nbsp;$\cancel{P_3}$,&nbsp;&nbsp;$P_4$

 | Instruction  | Dest                                     | Src                                      |
 | :----------- | -------:                                 | ------:                                  |
 | mov rcx, rax | <span style="color:#445fe8">$P_1$</span> | $P_0$                                    |
 | add rcx, 1   | $P_2$                                    | <span style="color:#445fe8">$P_1$</span> |
 | mov rcx, rax | <span style="color:#b0413e">$P_3$</span> | $P_0$                                    |
 | add rcx, 1   | $P_4$                                    | <span style="color:#b0413e">$P_3$</span> |
 | ...          |                                          |                                          |

---

### Optimisation: élimination des `MOV`

 | Instruction  | Dest                                     | Src                                      |
 | :----------- | -------:                                 | ------:                                  |
 | mov rcx, rax | <span style="color:#445fe8">$P_0$</span> | $P_0$                                    |
 | add rcx, 1   | $P_1$                                    | <span style="color:#445fe8">$P_0$</span> |
 | mov rcx, rax | <span style="color:#b0413e">$P_0$</span> | $P_0$                                    |
 | add rcx, 1   | $P_2$                                    | <span style="color:#b0413e">$P_0$</span> |
 | ...          |                                          |                                          |

---

{{< slide background-image="figs/zen4.png" background-size="contain" background-position="center" background-repeat="no-repeat" >}}

---

### Cas d'application

{{% fragment %}}
```asm
R1 ← mem[1]
R1 ← R1 + 1
mem[1] ← R1
R1 ← mem[10]
R1 ← R1 + 4
mem[11] ← R1
```
{{% /fragment %}}

{{% fragment %}}
```asm
R1a ← mem[1]
R1b ← R1a + 1
mem[1] ← R1b
R1c ← mem[10]
R1d ← R1c + 4
mem[11] ← R1d
```
{{% /fragment %}}

{{% fragment %}}
```asm
R1a ← mem[1]   &  R1c ← mem[10]
R1b ← R1a + 1  &  R1d ← R1c + 4
mem[1] ← R1b   &  mem[11] ← R1d
```
{{% /fragment %}}

---

### En résumé

- $16$ registres architecturaux (x86-64).
- Au moins $120$ registres physiques.
- Table d'alias des registres (RAT): registres architecturaux $\to$ registres physiques.
- La RAT élimine les fausses dépendances.

---
