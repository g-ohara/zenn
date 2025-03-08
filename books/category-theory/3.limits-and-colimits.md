---
title: "極限と余極限"
---

# 図式

- **$\mathscr{J}$ 型の図式 ($\mathscr{J}$-type diagram)** : 関手 $\mathscr{J}\to\mathscr{C}$
  - $\mathscr{J}$ を **添字圏 (index category)** という
- **対角関手 (diagonal functor)** : 関手 $\Delta:\mathscr{C}\to\mathscr{C}^\mathscr{J}$
  - $\Delta(C):\mathscr{J}\to\mathscr{C}$ は $\mathscr{J}$ の任意の対象を $C$ に，任意の射を $1_C$ に写す

# 錐と余錐

## 錐

- 図式 $D:\mathscr{J}\to\mathscr{C}$ に対して， $\mathscr{C}$ の対象 $C$ および自然変換 $c:\Delta(C)\to D$ の組 $(C,c)$ を $D$ への **錐 (cone)** という
- 図式 $D:\mathscr{J}\to\mathscr{C}$ に対して，以下によって構成される圏を $\operatorname{Cone}(D)$ と表記する
  - 対象は $D$ への錐
  - 射 $\theta:(C,c)\to(C',c')$ は， $\forall j\in\mathscr{J};\ c'_j\circ\theta=c_j$ を満たす $\mathscr{C}$ の射 $\theta:C\to C'$

## 余錐

- 図式 $D:\mathscr{J}\to\mathscr{C}$ に対して， $\mathscr{C}$ の対象 $C$ および自然変換 $c:D\to\Delta(C)$ の組 $(C,c)$ を $D$ からの **余錐 (cocone)** という
- 図式 $D:\mathscr{J}\to\mathscr{C}$ に対して，以下によって構成される圏を $\operatorname{Cocone}(D)$ と表記する
  - 対象は $D$ からの余錐
  - 射 $\theta:(C,c)\to(C',c')$ は， $\forall j\in\mathscr{J};\ \theta\circ c_j=c'_j$ を満たす $\mathscr{C}$ の射 $\theta:C\to C'$

# 極限と余極限

- **極限 (limit)** : 錐の圏 $\operatorname{Cone}(D)$ における終対象
- **余極限 (colimit)** : 余錐の圏 $\operatorname{Cocone}(D)$ における始対象
- 特に圏 $\mathscr{J}$ が有限の場合は， **有限極限 (finite limit)** と **有限余極限 (finite colimit)** という

