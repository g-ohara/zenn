---
title: 冪
---

# 冪

- **冪 (exponential)**
    - 「写像全体の集合」の一般化
    - $A$ から $B$ への冪 $B^A$ : コンマ圏 $(A\times()\to B)$ の終対象
        
        ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/18f31529-95aa-4f95-94f8-7894fb645c03/image.png)
        
        - **カリー化 (currying)** : 多変数関数から一変数関数へ
        - **アンカリー化 (uncurrying)** : 一変数関数から多変数関数へ
    - 集合 $A$ の部分集合は、$A$ から集合 $2$ (2個の要素をもつ集合) への写像と同一視できる
        
        → $A$ の冪集合 ($A$ の部分集合の全体) は $2^A$
        
- **カルテジアン閉圏 (cartesian closed category; CCC)**
    - 関数やプログラムのはたらきを記述するための圏
    - 定義: 終対象をもち、任意の対象について積と冪をもつ圏
- **Lawvere の不動点定理 (Lawvere's fixed-point theorem)**
    - 準備
        - $f:A\to X$ が **点全射 (point-surjective)**
            
            $\xLeftrightarrow{\ \mathrm{def}\ } \forall x:1\to X;\ \exists a:1\to X;\ x=f\circ a$
            
        - $g:A\times B\to X$ のカリー化 $\tilde{g}:B\to X^A$ が **弱点全射 (weakly point-surjective)**
            
            $\xLeftrightarrow{\ \mathrm{def}\ } \forall h:A\to X;\ \exists b:1\to B;\ \forall a:1\to A;\ g\circ(a\times b)=h\circ a$
            
    - 定理
        - 前提
            - 圏 $\mathcal{C}$ は CCC
            - $f:A\times A\to X$ のカリー化 $\tilde{f}:A\to X^A$ が弱点全射
        - 結論
            - $\forall g:X\to X;\ \exists x:1\to X;\ g\circ x=x$
    - 証明
        - 弱点全射の定義において $h=g\circ f\circ(1_A\times 1_A)$ とすれば $f\circ(a\times a)$ が不動点になる
    - 帰結
        - Cantor の定理
            - 「冪集合は元の集合よりも真に大きい」すなわち「全射 $A\to 2^A$ は存在しない」
            - 全射 $\tilde{f}:A\to 2^A$ を仮定すると、任意の $g:2\to 2$ に不動点が存在することになる
        - Russell のパラドックス
        - Gödel の不完全性定理

