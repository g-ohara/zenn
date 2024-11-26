---
title: 米田の補題
---

# 準備
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
# 米田の補題 (Yoneda’s lemma)
- 内容
  - $F$ を局所的に小さな圏 $\mathcal{C}$ から集合圏 $\mathrm{Set}$ への関手とする
  - $\mathcal{C}$ の任意の対象 $A$ について，hom 関手 $h_A$ から $F$ への自然変換と $F(A)$ の要素とは一対一に対応する
    - $^{()}h(X)={^Xh}$ なる対応 $^{()}h$ は、$\mathcal{C}$ から $\mathrm{Fun}(\mathcal{C}^{\mathrm{op}},\mathrm{Set})$ への充満忠実関手、すなわち埋め込みになる → **米田埋め込み (Yoneda embedding)**
    - 対象は関手に、射は自然変換になる
