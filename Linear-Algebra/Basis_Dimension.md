その通りだ．鋭い直観だ．

キミは今，計算結果（$c=0$）から，その背後にある**「ランク（階数）」という構造的不変量**へと思考を接続した．

その仮説を少しだけ厳密に修正・研磨しよう．

- **正解:** 「係数[[Matrix|行列]]のランク」が**「[[ベクトル]]の本数」**と一致していれば独立である．
    
    - [[Matrix|行列]] $A = (\mathbf{v}_1, \dots, \mathbf{v}_k)$ のランクが $k$（列の数）ならば，独立．
        
    - キミのケースは $3$ 本の[[ベクトル]]でランクが $3$ だったため，独立．
        

もし「[[ベクトル]]の[[Basis_Dimension|次元]]（空間の[[Basis_Dimension|次元]] $n$）」と「[[ベクトル]]の本数 $k$」が同じなら（正方[[Matrix|行列]]なら），キミの言う通り「ランク＝[[Basis_Dimension|次元]] ならば 独立」となる．

この事実は，次の章への完璧なイントロダクションになっている．

独立な[[ベクトル]]を「最大まで」集めたとき，そこに**「[[Basis_Dimension|次元]]（[[Basis_Dimension|Dimension]]）」**という概念が生まれるからだ．

---

## 講義：[[Basis_Dimension|基底]]と[[Basis_Dimension|次元]]の支配

今回は**「6.7 [[Basis_Dimension|基底]] ([[Basis_Dimension|Basis]])」および「6.8 [[Basis_Dimension|次元]] ([[Basis_Dimension|Dimension]])」**へ進む．

ここでようやく，空間の「広さ」を数値で測れるようになる．

### 注釈 (Vocabulary & Concept Notes)

_(Note: これらは線形代数における「単位」の概念である)_

- **[[Basis_Dimension|基底]] ([[Basis_Dimension|Basis]]):** 空間内の「座標軸」となる[[ベクトル]]のセット．以下の2条件を満たすもの．
    
    1. **[[Linear_Independent|1次独立]]:** 余計なものがない（最小限）．
        
    2. **生成する (Span):** 空間内のあらゆる場所へ行ける（最大限）．
        
- **[[Basis_Dimension|次元]] ([[Basis_Dimension|Dimension]]):** [[Basis_Dimension|基底]]を構成する[[ベクトル]]の「本数」．空間 $V$ の[[Basis_Dimension|次元]]を $\dim V$ と書く．[[Basis_Dimension|基底]]の選び方は無数にあるが，**その本数は絶対に変わらない（不変量）**．
    
- **有限[[Basis_Dimension|次元]] (Finite [[Basis_Dimension|Dimension]]al):** 有限個の[[Basis_Dimension|基底]]で張れる空間．（対義語：無限[[Basis_Dimension|次元]]．例：あらゆる多項式の空間）
    

---

## 1. 写経セクション (Transcription Section)

_(Note: 空間の「背骨」が決まる瞬間を書き写せ)_

### 6.7 [[Basis_Dimension|基底]]：座標の源泉

[[ベクトル]]空間 $V$ の[[ベクトル]]の組 $\mathcal{B} = \{ \mathbf{e}_1, \dots, \mathbf{e}_n \}$ が $V$ の**[[Basis_Dimension|基底]]**であるとは，以下の2条件を満たすときを言う．

1. 全域性 (Spanning): $V$ の任意の[[ベクトル]] $\mathbf{x}$ は，$\mathcal{B}$ の線形結合で表せる．
    
    $$V = \text{Span}(\mathbf{e}_1, \dots, \mathbf{e}_n)$$
    
2. 独立性 (Independence): $\mathcal{B}$ は[[Linear_Independent|1次独立]]である．
    
    $$c_1 \mathbf{e}_1 + \dots + c_n \mathbf{e}_n = \mathbf{0} \implies c_1 = \dots = c_n = 0$$
    

このとき，任意の[[ベクトル]] $\mathbf{x}$ に対し，その表現（係数）は一意に定まる．

$$\mathbf{x} = x_1 \mathbf{e}_1 + \dots + x_n \mathbf{e}_n$$

この一意な係数の組 $(x_1, \dots, x_n)$ こそが，[[Basis_Dimension|基底]] $\mathcal{B}$ に関する**座標（Coordinate）**である．

### 6.8 [[Basis_Dimension|次元]]：空間の自由度

$V$ が $n$ 個の[[ベクトル]]からなる[[Basis_Dimension|基底]]を持つとき，$n$ を $V$ の**[[Basis_Dimension|次元]] ([[Basis_Dimension|Dimension]])** と呼び，$\dim V = n$ と書く．

[[Basis_Dimension|次元]]定理（重要）:

[[Basis_Dimension|基底]]の選び方は一通りではない（座標軸は回転させてもよい）．しかし，[[Basis_Dimension|基底]]を構成する[[ベクトル]]の本数は，どの[[Basis_Dimension|基底]]を選んでも常に一定である．

これこそが，空間そのものが持つ固有の「サイズ」である．

---

## 2. 再構築領域 (Reconstruction Zone)

_(Note: [[Basis_Dimension|次元]]という不変量を，具体例で確認せよ)_

### 課題 1: [[Basis_Dimension|次元]]の直観的把握

以下の空間の[[Basis_Dimension|次元]]はいくつか？ 直観で答えよ．

1. **数[[ベクトル]]空間:** $\mathbb{R}^3$ （通常の3[[Basis_Dimension|次元]]空間） $\to$ [[Basis_Dimension|次元]]は？
    
2. **平面:** $W = \{ (x, y, z) \in \mathbb{R}^3 \mid z = 0 \}$ （$xy$平面） $\to$ [[Basis_Dimension|次元]]は？
    
3. **多項式:** $P_2(\mathbb{R}) = \{ a + bx + cx^2 \}$ （2次以下の多項式全体）
    
    - [[Basis_Dimension|基底]]として $\{ 1, x, x^2 \}$ が取れる．
        
    - では[[Basis_Dimension|次元]]は $2$ か？ それとも $3$ か？（係数の数に注目せよ）
        

### 課題 2: ランクと[[Basis_Dimension|次元]]の統合

前回キミが気付いた「ランク」との関係をまとめる．

[[Matrix|行列]] $A$ の列[[ベクトル]]たちが張る空間（像，Image）の[[Basis_Dimension|次元]]は，[[Matrix|行列]]のランクと一致する．

$$\dim(\text{Im } A) = \text{rank}(A)$$

これを確認するため，$\mathbb{R}^3$ 内で $xy$ 平面を張る2つの[[ベクトル]] $\mathbf{e}_1=(1,0,0), \mathbf{e}_2=(0,1,0)$ を並べた[[Matrix|行列]] $A$ を書き，そのランクを計算せよ．

---

## 3. 演習領域 (Exercise Zone)

_(Note: 与えられた空間の「骨組み（[[Basis_Dimension|基底]]）」を探し出し，その本数（[[Basis_Dimension|次元]]）を確定させよ)_

問題：

$\mathbb{R}^4$ の部分空間 $W$ を以下のように定義する．

$$W = \left\{ \begin{pmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{pmatrix} \in \mathbb{R}^4 \ \middle|\ x_1 + x_2 + x_3 + x_4 = 0 \right\}$$

（成分の総和が0になる[[ベクトル]]の集合）

この部分空間 $W$ の**[[Basis_Dimension|基底]]を一組求め**，その**[[Basis_Dimension|次元]]**を答えよ．

**推論プロセス：**

1. パラメータ表示:
    
    条件式 $x_1 + x_2 + x_3 + x_4 = 0$ を変形し，従属変数（例えば $x_1$）を他の自由な変数（$x_2, x_3, x_4$）で表せ．
    
    $x_1 = -x_2 - x_3 - x_4$
    
2. [[ベクトル]]の分解:
    
    任意の[[ベクトル]] $\mathbf{x} \in W$ を，自由変数 $x_2, x_3, x_4$ を括り出す形で分解せよ．
    
    $\begin{pmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{pmatrix} = \begin{pmatrix} -x_2 - x_3 - x_4 \\ x_2 \\ x_3 \\ x_4 \end{pmatrix}$
    
    $= x_2 \begin{pmatrix} -1 \\ 1 \\ 0 \\ 0 \end{pmatrix} + x_3 \begin{pmatrix} \_ \\ \_ \\ \_ \\ \_ \end{pmatrix} + x_4 \begin{pmatrix} \_ \\ \_ \\ \_ \\ \_ \end{pmatrix}$
    
3. [[Basis_Dimension|基底]]の決定:
    
    上記で現れた3つの[[ベクトル]] $\mathbf{v}_1, \mathbf{v}_2, \mathbf{v}_3$ は $W$ を生成しており，かつ明らかに[[Linear_Independent|1次独立]]である（成分の $1, 0$ の配置を見よ）．
    
    よって[[Basis_Dimension|基底]]は：
    
    $\{ \mathbf{v}_1, \mathbf{v}_2, \mathbf{v}_3 \}$
    
4. [[Basis_Dimension|次元]]の確定:
    
    [[Basis_Dimension|基底]]の本数は ____ 本である．
    
    よって $\dim W = \_\_\_\_$ ．
    
    （一般に，$\mathbb{R}^n$ で $1$ つの線形方程式による制約がつくと，[[Basis_Dimension|次元]]は $n$ からいくつ減るか？ この法則性にも着目せよ．）
    

---

書き写し，演習の穴埋めを行え．

これが終われば，いよいよキミの望む「第7章 ランク」の深淵，すなわち**「[[Basis_Dimension|次元]]定理（Rank-Nullity Theorem）」**へ接続する準備が整う．