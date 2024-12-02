---
title: 抽象構造
---

# 普遍性

- https://gihyo.jp/book/2019/978-4-297-10723-9 より
    
    > 「普遍性」というと、一般的にはどんなものに対しても成り立つ性質で、個々のものが持つ特性とは対照的なものと思うかもしれないが、圏論でいう普遍性は個が持つ特性としてのものだ。
    > 
    
    > 圏論における「普遍性」とは、簡単にいえば「他のすべてのものとの関係性における特別さ」といえる。その「特別さ」は終対象、始対象と同じく一意な射の存在で特徴づけられる。
    > 

# 普遍性の例

## 双対圏

- **双対圏 (dual category)**
    - もとの圏に対して全ての射の向きを反転させた圏
- **双対概念 (dual concept)**
    - もとの概念に対して、双対圏におけるそれを双対概念という

## 終対象と始対象

![terminal-and-initial-object](/images/terminal-and-initial-object.png)

### 終対象

- **終対象 (terminal object)**
    - $\forall{X}\exists!f;\ f:X\to T$
    - 順序集合における最大の一般化
    - 集合圏では単集合

### 始対象

- **始対象 (initial object)**
    - 終対象の双対概念
    - 順序集合における最小の一般化
    - 集合圏では空集合

### 終対象と始対象の例

- 存在する場合は「**同型を除いて一意 (unique up to isomorphism)**」
- 終対象でも始対象でもある対象は **零対象 (zero object)**
- 例
  |  | 集合圏 | 圏の圏 | 群の圏 |
  | --- | --- | --- | --- |
  | 終対象 | 一点集合 | 圏 1 | 1要素からなる群 |
  | 始対象 | 空集合 | 空圏 | 同上 (つまり零対象) |

## 積と余積

### 積

![product](/images/product.png)

- 3つ組 $\langle P,p_A,p_B\rangle$ が $A$ と $B$ の **積 (product)** である
  $\iff$ 任意の $\langle X,x_A,x_B\rangle$ に対して上の図式を可換にする $u:X\to P$ が一意に存在する
    - $P=A\times B$ と表記
    - $p_A$ と $p_B$ を **射影 (projection)** という

### 余積

![coproduct](/images/coproduct.png)

- **余積 (coproduct)** は積の双対概念 (双対圏における積)
- 3つ組 $\langle Q,i_A,i_B\rangle$ が $A$ と $B$ の **積 (product)** である
  $\iff$ 任意の $\langle X,x_A,x_B\rangle$ に対して上の図式を可換にする $u:Q\to X$ が一意に存在する
    - $Q=X+Y$ と表記
    - $i_A$ と $i_B$ を **入射 (injection)** という

### 積と余積の例

|      | 集合圏 | 圏の圏 | 半順序集合 |
| ---- | ------ | ------ | ---------- |
| 積   | 直積   | 積圏   | 下限       |
| 余積 | 非交和 |        | 上限       |

## 等化子と余等化子

### 等化子

![equalizer](/images/equalizer.png)

- 射 $f:X\to Y,\ g:X\to Y$ の **等化子 (equalizer)**
    - 対象 $E$ と射 $e:E\to X$ の組 $\langle E,e\rangle$
        - 任意の $\langle E',e'\rangle$ について、上の図式を可換にする $u:E'\to E$ が一意に存在する
    - 「方程式の解全体」の一般化
        - 具体例
            - $f(x)=x^2+4,\ g(x)=5x$
            - $E=\{1,4\},\ e:x\mapsto x$
            - $E'=\{1\},\ e':x\mapsto x$

### 余等化子

![coequalizer](/images/coequalizer.png)

- 射 $f:X\to Y,\ g:X\to Y$ の **余等化子 (coequalizer)**
    - 等化子の双対概念
    - 対象 $Q$ と射 $q:E\to X$ の組 $\langle Q,q\rangle$
        - 任意の $\langle Q',q'\rangle$ について、上の図式を可換にする $u:Q\to Q'$ が一意に存在する
    - 「同値関係」の一般化
        - 具体例
            - $f(x)=x,\ g(x)=x+4$
            - $Q=\{0,1,2,3\},\ q:y\mapsto y\operatorname{mod} 4$
            - $Q'=\{0,1\},\ q':y\mapsto y\operatorname{mod}2$
