---
title: 圏
---

# 射

- **圏 (catogory)**
    - **対象 (object)** と **射 (arrow, morphism)**
        - 2つの射の間に「等しさ」を定義できる
            - 対象の間の「等しさ」は要求しない →「同型」の概念
    - **域 (domain)** と **余域 (codomain)**
    - **合成 (composition)** と **結合律 (associative law)**
        - $(h\circ g)\circ f=h\circ(g\circ f)$
    - **恒等射 (identity)** と **単位律 (identity law)**
        - 対象と恒等射を同一視することも → 主役は射
- 同型
    - **逆射 (inverse)** が存在する射 = **可逆 (invertible)** な射 = **同型射 (isomorphism)**
    - 同型射が存在する = 2つの対象は **同型 (isomorphic)**
    - 対象の「本質的な等しさ」
- いろいろな圏
    - **空圏 (empty category)**
        - 対象も射ももたない圏
    - **自由圏 (free category)**
    - モノイド (monoid)
        - 集合論 → 結合律 + 単位元の存在
        - 圏論 → 対象がひとつ (単対象圏)
        - $(G,\cdot)$ → 対象は $G$，射は $g\in G$，射の合成は $g_1\cdot g_2$，恒等射は単位元 $1$
    - 群 (group) = 可逆モノイド
        - 集合論 → 任意の元に逆元が存在
        - 圏論 → 任意の射に逆射が存在

# 関手

- **関手 (functor)**
    - 圏から圏へ，対象と射の間の対応 $F$
        - 全射でなくてもいい
    - $f:X\to Y$ が $F(f):F(X)\to F(Y)$ に対応
    - 合成を保存
    - 恒等射を保存
- 「圏の圏」の射
    - 前者の圏における射を後者の圏における対象とみたとき

# 自然変換

- **自然変換 (natural transformation)**
    - 関手 $F$ を $G$ に対応させる $t$
    - 対象 $X$ を射$X$$t_X:F(X)\to G(X)$ に対応させる
      - 自然変換 $t$ は，各対象に対するこれらの射を束ねたもの，というイメージ
    - 関手の構造を保存: $G(f)\circ t_X=t_Y\circ F(f)$
      - i.e. 以下の図式が可換
        ![](https://cdn-ak.f.st-hatena.com/images/fotolife/t/tobita_yoshiki/20210526/20210526184446.png)
            
- **関手圏 (functor category)** $\operatorname{Fun}(\mathcal{C},\mathcal{D})$
    - 2つの圏の間の関手を対象，自然変換を射と捉える
    - **自然同値 (natural equivalence)**
        - 関手圏の射として同型射となる自然変換を自然同値という
    - **圏同値 (categorically eqivalent)**
        - 関手 $F:\mathcal{C}\to\mathcal{D}$ および $G:\mathcal{D}\to\mathcal{C}$ のうち、$G\circ F\cong\operatorname{id}_\mathcal{C},\ F\circ G\cong\operatorname{id}_\mathcal{D}$ となるものが存在するとき、圏 $\mathcal{C},\ \mathcal{D}$ は圏同値であるという
            - つまり行って戻ってきたときに恒等関手と自然同値であればよい
- 米田の補題と米田埋め込み
    - 準備
        - **反変関手 (contravariant category)** : 双対圏 $\mathcal{C}^{\mathrm{op}}$ からの関手
        - **局所的に小さな圏 (locally small category)**
            - $\mathrm{Hom}_{\mathcal{C}}(A,B)$: 圏 $\mathcal{C}$ の対象 $A$ から $B$ への射の集まり
            - $\mathcal{C}$ が局所的に小さな圏 $\iff$ $\mathcal{C}$ の任意の対象 $A,B$ について $\mathrm{Hom}_{\mathcal{C}}(A,B)$ が集合
        - **集合圏 (set category)**
            - 全ての集合を対象，集合間の全ての写像を射とする
        - **hom 関手 (hom functor)**
            - 局所的に小さな圏 $\mathcal{C}$ の対象 $A$ について定められる，$\mathcal{C}$ から集合圏 $\mathrm{Set}$ への関手
                - 対象 $X$ を $\mathrm{Hom}_{\mathcal{C}}(A,X)$ に対応させる
                - 射 $f:X\to Y$ を $\mathrm{Hom}_{\mathcal{C}}(A,X)\ni x\mapsto f\circ x\in\mathrm{Hom}_{\mathcal{C}}(A,Y)$ に対応させる
            - 客観的な世界を、ある対象からみた主観的な世界に変換
        - 充満 (faithful) ・忠実 (full) ・充満忠実 (fully faithful)
            - 局所的に小さな圏 $\mathcal{C,D}$ と $\mathcal{C}$ から $\mathcal{D}$ への関手 $F$
            - $\mathrm{Hom}_{\mathcal{C}}(A,B)$ から $\mathrm{Hom}_{\mathcal{D}}(F(A),F(B))$ への写像が
                - 全射 $\longrightarrow$ $F$ は充満
                - 単射 $\longrightarrow$ $F$ は忠実
                - 全単射 $\longrightarrow$ $F$ は充満忠実
            - 関手が充満忠実なら、ふたつの圏の間で射の集合は同型
                - 行先の圏の中に元の圏と同じ世界が再現される → 埋め込み (embedding)
    - **米田の補題 (Yoneda’s lemma)**
        - 内容
            - $F$ を局所的に小さな圏 $\mathcal{C}$ から集合圏 $\mathrm{Set}$ への関手とする
            - $\mathcal{C}$ の任意の対象 $A$ について，hom 関手 $h_A$ から $F$ への自然変換と $F(A)$ の要素とは一対一に対応する
                - $^{()}h(X)={^Xh}$ なる対応 $^{()}h$ は、$\mathcal{C}$ から $\mathrm{Fun}(\mathcal{C}^{\mathrm{op}},\mathrm{Set})$ への充満忠実関手、すなわち埋め込みになる → **米田埋め込み (Yoneda embedding)**
                - 対象は関手に、射は自然変換になる
