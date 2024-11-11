---
title: "モナドと代数"
---

# モナド

- **モナド (monad)**
    - ずばり
        - 自己関手圏におけるモノイド対象
    - 定義
        - 圏 $\mathcal{C}$ における自己関手 $T:\mathcal{C}\to\mathcal{C}$ と、自然変換 $\mu:TT\Rightarrow T$ および $u:\mathrm{id}_\mathcal{C}\Rightarrow T$
        - 3つ組 $(T,\mu,u)$ がモナド $\iff$ 以下の図式が可換
    - 計算効果とモナド
        - モナドなし
            - 失敗するかもしれない計算 $f:C\to C\cup\{\mathrm{Nothing}\}$
            - $f$ の結果を入力とする、失敗するかもしれない計算 $g:C\to C\cup\{\mathrm{Nothing}\}$
                
                $\tilde{g}\circ f(x)=\begin{cases}g(x)&(x\neq\mathrm{Nothing}) \\\mathrm{Nothing}&(x=\mathrm{Nothing})\end{cases}$
                
                - $g$ の中にも分岐があるので、合成が伸びると入れ子が深くなっていく
        - モナドあり
            - Maybe モナド
                - 型 $C$ を $T(C)=C\cup\{\mathrm{Nothing}\}$ に写す
                - プログラム $g:A\to T(B)$ を $T(g):T(A)\to T(B)$ に写す
