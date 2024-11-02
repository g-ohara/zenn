---
title: "極限と余極限"
---

- 手書きノート
    
    [limit.pdf](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/c80ce0e6-a59b-4883-b834-032410610c1d/limit.pdf)
    

# コンマ圏

- 圏の見方を根本から変えてみよう
    - 2つの特別な圏を用意する
        - 圏 $1$ : 1つの対象とその恒等射のみをもつ圏
        - 圏 $2$ : 2つの対象とそれぞれの恒等射、一方から他方への1つの射のみをもつ圏
    - 圏 $\mathcal{C}$ の対象は圏 $1$ から $\mathcal{C}$ への関手、射は圏 $2$ から $\mathcal{C}$ への関手とみなせる
- **射圏 (morphism category)**
    - 圏 $\mathcal{C}$ の射を対象とする圏、すなわち関手圏 $\operatorname{Fun}(2,\mathcal{C})$
    - 射圏における射は自然変換、すなわち $\mathcal{C}$ の2つの射を結ぶ可換図式
- **コンマ圏 (comma category)**
    
    ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/4b6eff08-4514-4756-b8c8-fb1bd030a6d1/image.png)
    
    - $\langle D,E,f\rangle,\langle D',E',f'\rangle$ を対象とし、上の図式を可換にする $\langle d,e\rangle$ を射とする圏
    - $(F\downarrow G)$ と表記
    - 射圏の一般化 (他の圏からの作用を取り込めるように)
        - 射圏は特殊なコンマ圏 $(\operatorname{id}_{\mathcal{C}}\downarrow\operatorname{id}_{\mathcal{C}})$
            - 上の図式で $\mathbf{D},\mathbf{E}$ として $\mathbf{C}$ をとり、$F=G=\operatorname{id}_{\mathcal{C}}$ とした場合
- **$\mathcal{J}$ 型の図式 ($\mathcal{J}$-type diagram)** : 圏 $\mathcal{J}$ から圏 $\mathcal{C}$ への関手
    - $\mathcal{J}$ を **添字圏 (index category)** という
        
        ![圏 $\mathcal{C}$ の図式を、ある適当な圏 $\mathcal{J}$ からの関手とみなす](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/9e12c69a-555e-4e75-a1d6-47102367a6db/image.png)
        
        圏 $\mathcal{C}$ の図式を、ある適当な圏 $\mathcal{J}$ からの関手とみなす
        
- **定関手 (constant functor)** : 圏 $\mathcal{J}$ の任意の射を圏 $\mathcal{C}$ の一つの恒等射 $1_X$ に写す関手
- 極限と余極限の定義 1
    - **錐 (cone)** : 対象 $C\in\mathcal{C}$ と、定関手 $1_C$ から $\mathcal{J}$ 型の図式 $D$ への自然変換 $c$ の組 $(C,c)$
        - 錐の圏 $\operatorname{Cone}(D)$ : $D$ の任意の錐を対象とし、射 $\theta:(C,c)\to(C',c')$ は任意の $j\in\mathcal{J}$ について以下の図式を可換にする
            - $c'_j\circ\theta=c_j$
    - 極限 : 錐の圏 $\operatorname{Cone}(D)$ における終対象
    - 余極限 : 余錐の圏 $\operatorname{Cocone}(D)$ における始対象
- 極限と余極限の定義 2
    - **対角関手 (diagonal functor)** : 圏 $\mathcal{C}$ の対象 $X$ に、$X$ への定関手を対応させる、$\mathcal{C}$ から $\operatorname{Fun}(\mathcal{J},\mathcal{C})$ への関手 $\Delta$
        
        ![$\Delta(f)$ は関手 $\Delta(X),\Delta(Y)$ の間の自然変換であり、 $\mathcal{J}$ の任意の対象に $f$ を対応させる](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8555476-16af-4c38-9dc1-3d664a66589f/fe1be0f5-4550-4461-9e26-15794250d6a2/image.png)
        
        $\Delta(f)$ は関手 $\Delta(X),\Delta(Y)$ の間の自然変換であり、 $\mathcal{J}$ の任意の対象に $f$ を対応させる
        
    - $\mathcal{J}$ 型の図式 **$D$** は $\operatorname{Fun}(\mathcal{J},\mathcal{D})$
     の対象
    - **$D$** を圏 $1$ から $\operatorname{Fun}(\mathcal{J},\mathcal{D})$ への関手とみなすことで、コンマ圏 $(\Delta\to D)$ を考える
        - **極限 (limit)** : $(\Delta\to D)$ の終対象
        - **余極限 (colimit)** : $(\Delta\to D)$ の始対象
        - 特に圏 $\mathcal{J}$ の対象と射が有限個の場合は **有限極限 (finite limit)** と **有限余極限 (finite colimit)**
