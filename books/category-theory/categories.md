---
title: 圏
---

# 射

- **圏 (catogory)**
  - **対象 (object)** と **射 (morphism, arrow)**
    - 2つの射の間に「等しさ」が定義される
        - 対象の「等しさ」の定義は要求しない
    - 対象の集まり，射の集まりは集合でなくてもよい
  - **域 (domain)** と **余域 (codomain)**
    - 任意の射は，域，余域と呼ばれる対象をただ一つずつもつ
      - 域が矢印の始点，余域が終点
      - **自己射 (endomorphism)**: 域と余域が同じである射
    - 表記
      - $\text{morphism}:\text{domain}\to\text{codomain}$
      - $\text{domain}\xrightarrow{\text{morphism}}\text{codomain}$
      - ex. $f:A\to B,\ A\xrightarrow{f}B$
  - **合成 (composition)** と **結合律 (associative law)**
    - 射 $f:A\to B$ と $g:B\to C$ について合成射 $g\circ f$ が存在する
    - 合成に関して結合律が成り立つ
      - $(h\circ g)\circ f=h\circ(g\circ f)$
  - **恒等射 (identity)** と **単位律 (identity law)**
    - 任意の対象 $A$ は恒等射 $1_A:A\to A$ をただ一つもつ
    - 任意の恒等射について単位律が成り立つ
      - $1_A\circ f=f\circ 1_B=f$
    - 対象と恒等射を同一視し，射のみで圏を定義することもできる
- **同型射 (isomorphism)** と **同型 (isomorphic)**
  - 射 $f$ について以下を満たす射 $f^{-1}$ を $f$ の **逆射 (inverse)** という
    - $f^{-1}\circ f=1_A\wedge f\circ f^{-1}=1_B$
  - 逆射が存在する射を **同型射 (isomorphism)** という
  - 2つの対象の間に同型射が存在するとき，それらは **同型 (isomorphic)** であるという
    - 「同型」$=$ 対象の「本質的な等しさ」
- **双対圏 (dual category)**
  - 圏 $\mathcal{C}$ の任意の射の域と余域を入れ替えた圏 $\mathcal{C}^\mathrm{op}$ を $\mathcal{C}$ の双対圏という

- 圏の例
    - **空圏 (empty category)**
      - 対象も射ももたない圏
    - **局所小圏 (locally small category)**
      - $\mathrm{Hom}_{\mathcal{C}}(A,B)$: 圏 $\mathcal{C}$ の対象 $A$ から $B$ への射の集まり
      - $\mathcal{C}$ が局所小圏 $\iff$ $\mathcal{C}$ の任意の対象 $A,B$ について $\mathrm{Hom}_{\mathcal{C}}(A,B)$ が集合
    - **自由圏 (free category)**
    - **モノイド (monoid)**
      - 対象をただひとつもつ圏
      - 集合論におけるモノイドと一致する
        - 対象を集合，射をその要素，合成を二項演算，恒等射を単位元とみなす
    - **群 (group)**
      - 任意の射が同型射であるモノイド
      - これも集合論における群 ( $=$ 可逆モノイド) と一致する
    - **集合圏 (set category)**
      - 任意の集合を対象，任意の写像を射とする圏
      - $\mathrm{Set}$ と表記

# 関手

- **関手 (functor)**
    - 圏 $\mathcal{C}$ の対象と射を圏 $\mathcal{D}$ の対象と射へ写す対応 $F:\mathcal{C}\to\mathcal{D}$ のうち，以下を満たすもの
      - 域と余域を保存
        - $F(f:X\to Y):F(X)\to F(Y)$
      - 合成を保存
        - $F(g\circ f)=F(g)\circ F(f)$
      - 恒等射を保存
        - $F(1_X)=1_{F(X)}$
  - 「圏の圏」の射とみなすこともできる
  - **反変関手 (contravariant category)**
    - 双対圏 $\mathcal{C}^{\mathrm{op}}$ からの関手を $\mathcal{C}$ からの反変関手という
      - 反変関手と区別する目的で，単なる関手を共変関手と呼ぶことがある

# 自然変換

- **自然変換 (natural transformation)**
    - 関手 $F,G:\mathcal{C}\to\mathcal{D}$ に対して， $\mathcal{C}$ の対象 $X$ を $\mathcal{D}$ の射 $t_X:F(X)\to G(X)$ に写す対応 $t$ のうち，以下を満たすもの
      - 関手の構造を保存
        - $G(f)\circ t_X=t_Y\circ F(f)$
    - 自然変換 $t$ は射の束とも捉えられる
            
- **関手圏 (functor category)** $\operatorname{Fun}(\mathcal{C},\mathcal{D})$
    - 2つの圏の間の関手を対象，自然変換を射と捉える
    - **自然同値 (natural equivalence)**
        - 関手圏の射として同型射となる自然変換を自然同値という
    - **圏同値 (categorically eqivalent)**
        - 関手 $F:\mathcal{C}\to\mathcal{D}$ および $G:\mathcal{D}\to\mathcal{C}$ のうち、$G\circ F\cong\operatorname{id}_\mathcal{C},\ F\circ G\cong\operatorname{id}_\mathcal{D}$ となるものが存在するとき、圏 $\mathcal{C},\ \mathcal{D}$ は圏同値であるという
            - つまり行って戻ってきたときに恒等関手と自然同値であればよい