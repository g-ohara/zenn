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

## 終対象と始対象

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/fe28fe27-44a1-4cf3-bf33-6147f8f76891/f78ed2fe-e220-48b0-824e-5ea9a074118a.png)

- **終対象 (terminal object)**
    - $\forall{X}\exists!f;\ f:X\to T$
    - 順序集合における最大の一般化
    - 集合圏では単集合
- **始対象 (initial object)**
    - 終対象の双対概念
    - 順序集合における最小の一般化
    - 集合圏では空集合
- 存在する場合は「**同型を除いて一意 (unique up to isomorphism)**」
- 終対象でも始対象でもある対象は **零対象 (zero object)**
- 例
    
    
    |  | 集合圏 | 圏の圏 | 群の圏 |
    | --- | --- | --- | --- |
    | 終対象 | 一点集合 | 圏 1 | 1要素からなる群 |
    | 始対象 | 空集合 | 空圏 | 同上 (つまり零対象) |

## 積と余積

- 3つ組 $\langle P,p,q\rangle$ が $X$ と $Y$ の **積 (product)** である $\iff$任意の3つ組 $\langle A,f,g\rangle$ に対して上の図式を可換にする射 $h:A\to P$ がただ一つ存在する
    
    ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/4a54b4cd-c9c1-4c55-9182-2fdfbe2aa98d/image.png)
    
    - $P=X\times Y,\ h=f\times g$ と表記し、$p$ と $q$ を **射影 (projection)** という
- **余積 (coproduct)** は積の双対概念 (双対圏における積)
    - $P=X+Y,\ h=f+g$ と表記し、$p$ と $q$ を **入射 (injection)** という
- 存在する場合は「**同型を除いて一意 (unique up to isomorphism)**」
- 積，余積の例
    
    
    |  | 集合圏 | 圏の圏 | 半順序集合 |
    | --- | --- | --- | --- |
    | 積 | 直積 | 積圏 | 下限 |
    | 余積 | 非交和 |  | 上限 |

## 積関手

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/38a0f42b-7dcc-488c-b553-646a14b5da0a/image.png)

- **積関手 (product functor)** $F_A$ :「$A$ との積をつくる」という自己関手
- 対象 $X$ に射影 $p_X:A\times X\to X$ を対応させる変換 $p$ は、$F_A$ から恒等関手への自然変換になる

## 量圏

- **零射 (zero morphism)** : 零対象を経由した合成射 $0_{X,Y}:X\to Y$
    - 任意の対象の組について一意に定まる
- 零射を用いると余積から積への射を構成できる
    - 同型のとき、余積または積を **直和 (direct sum)** といい、$A\oplus B$ と表記
- 零射と直和をもつ圏を **量圏** (一般的な用語ではない) という
- 量圏は線形代数を展開するための土台になる

## 等化子と余等化子

- 射 $f:X\to Y,\ g:X\to Y$ の **等化子 (equalizer)**
    - 対象 $E$ と射 $eq:E\to X$ の組 $\langle E,eq\rangle$
        - $f\circ eq=g\circ eq$
        - 上の条件を満たす任意の組 $\langle O,m\rangle$ について、次の図式を可換にする $u:O\to E$ がただ一つ存在する:
            
            ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/b099bed8-f04d-48bf-8758-b0bf106f6ed9/image.png)
            
    - 「方程式の解全体」の一般化
        - 具体例
            - $f(x)=x^2+4,\ g(x)=5x$
            - $E=\{1,4\},\ eq:x\mapsto x$
            - $X=\{1\},\ m:x\mapsto x$
- 射 $f:X\to Y,\ g:X\to Y$ の **余等化子 (coequalizer)**
    - 等化子の双対概念
        
        ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/baf48d5e-4382-4b8f-875e-3474c4de14e7/image.png)
        
    - 「同値関係」の一般化
        - 具体例
            - $f(x)=x,\ g(x)=x+4$
            - $Q=\{0,1,2,3\},\ q:y\mapsto y\operatorname{mod} 4$
            - $Q'=\{0,1\},\ q':y\mapsto y\operatorname{mod}2$

## 引き戻しと押し出し

