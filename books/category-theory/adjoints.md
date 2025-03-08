---
title: 随伴
---

# 定理

## 右随伴は極限を保存する (RAPL)

- $F:\mathscr{C}\rightleftarrows\mathscr{D}:U$ が随伴 $F\dashv U$ であるとする．任意の図式 $D:\mathscr{J}\to\mathscr{D}$ に対して，極限 $\varprojlim D$ が存在するならば
  $$U(\varprojlim D)\cong\varprojlim(UD).$$

### 証明

任意の $X\in\mathscr{C}$ について

$$
\begin{aligned}
\mathscr{C}(X,U(\varprojlim D))
&\cong\mathscr{D}(F(X),\varprojlim D)\\
&\cong\varprojlim\mathscr{D}(F(X),D(\cdot))\\
&\cong\varprojlim\mathscr{C}(X,UD(\cdot))\\
&\cong\mathscr{C}(X,\varprojlim UD).
\end{aligned}
$$

ただし 2 行目および 4 行目の推論では，表現可能関手が全ての極限を保存することを用いた．

