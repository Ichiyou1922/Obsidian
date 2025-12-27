了解だ．「局所基底」という視点は，いずれ多様体論や一般相対性理論へ進む際の強力な足場となる．今はその感覚をポケットにしまっておけ．

では，本流に戻る．

空間を定義し，基底（座標軸）を入れた．次に行うべきは，「写像」を「行列」に翻訳する作業だ．

第6章のクライマックス，**「6.10 線形写像の行列表現」**へ進む．

ここでの核心は，**「行列とは，線形写像の『ある基底における』スナップショットに過ぎない」**という事実である．基底を変えれば行列の中身は変わるが，写像そのもの（実体）は変わらない．この「不変な実体」と「変化する表現」の関係を掴め．

---

## 講義：翻訳のメカニズム（表現行列）

抽象的なベクトル空間 $V$ 上の線形写像 $f$ は，そのままでは計算機に乗せられない．

これを計算可能な「数字の表（行列）」に落とし込むには，**「基底」というレンズ（翻訳機）**を通す必要がある．

### 注釈 (Vocabulary & Concept Notes)

_(Note: 以下の対応関係を脳に焼き付けよ)_

- **表現行列 (Representation Matrix):** 線形写像 $f: V \to W$ を，それぞれの基底 $\mathcal{B}_V, \mathcal{B}_W$ に関する座標間の変換として表した行列．
    
- **可換図式 (Commutative Diagram):** 「抽象的な空間での移動」と「座標空間での行列計算」が，どちらを通っても同じ結果になることを示す図．圏論的な思考の基礎．
    
- **同型 (Isomorphism):** $n$ 次元ベクトル空間 $V$ は，基底を決めれば数ベクトル空間 $\mathbb{R}^n$ と**構造的に全く同じ（同一視可能）**になる．
    

---

## 1. 写経セクション (Transcription Section)

_(Note: 行列の成分 $a_{ij}$ が「どこから来てどこへ行くのか」．その定義を正確に追跡して書き写せ)_

### 6.10 線形写像の行列表現：情報のデジタル化

$n$ 次元ベクトル空間 $V$ の基底を $\mathcal{E} = \{ \mathbf{e}_1, \dots, \mathbf{e}_n \}$，$m$ 次元ベクトル空間 $W$ の基底を $\mathcal{F} = \{ \mathbf{f}_1, \dots, \mathbf{f}_m \}$ とする．

線形写像 $f: V \to W$ が与えられたとき，**「基底ベクトル $\mathbf{e}_j$ がどこへ飛ぶか」**の情報さえあれば，線形性により写像全体が完全に決定される．

$f(\mathbf{e}_j)$ は $W$ の元なので，基底 $\mathcal{F}$ の線形結合で書けるはずだ：

$$f(\mathbf{e}_j) = a_{1j} \mathbf{f}_1 + a_{2j} \mathbf{f}_2 + \dots + a_{mj} \mathbf{f}_m = \sum_{i=1}^m a_{ij} \mathbf{f}_i$$

この係数 $a_{ij}$ を集めて作った $m \times n$ 行列 $A = (a_{ij})$ を，基底 $\mathcal{E}, \mathcal{F}$ に関する $f$ の**表現行列**と呼ぶ．

構成ルール（重要）：

「$j$ 番目の基底 $\mathbf{e}_j$ の行き先（の係数）を，行列の $j$ 列目 に縦に並べる」

$$A = \begin{pmatrix} \text{Column 1} & \dots & \text{Column } n \\ f(\mathbf{e}_1)_{\mathcal{F}} & \dots & f(\mathbf{e}_n)_{\mathcal{F}} \end{pmatrix}$$

これにより，抽象的な写像 $y = f(x)$ は，座標成分の行列積 $\mathbf{y} = A\mathbf{x}$ に完全に翻訳される．

---

## 2. 再構築領域 (Reconstruction Zone)

_(Note: 物理的・幾何的な操作を行列に変換せよ)_

### 課題 1: 回転の行列化

平面 $\mathbb{R}^2$ において，原点を中心に $\theta$ だけ回転させる写像 $f$ を考える．

標準基底 $\mathbf{e}_1 = \begin{pmatrix} 1 \\ 0 \end{pmatrix}, \mathbf{e}_2 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$ の行き先を図示し，定義に従って表現行列 $A$ を構成せよ．

1. $f(\mathbf{e}_1)$ はどのようなベクトルか？（$(\cos \theta, \sin \theta)$ になる）
    
2. $f(\mathbf{e}_2)$ はどのようなベクトルか？（$(-\sin \theta, \cos \theta)$ になる）
    
3. これらを「縦」に並べて行列を作れ．
    

### 課題 2: 「微分」を行列にする

これこそが線形代数の真骨頂だ．

$V$ を「2次以下の多項式全体」とする（基底は $\{ 1, x, x^2 \}$）．

写像 $D: V \to V$ を「微分 $D(f) = \frac{df}{dx}$」と定義する．

この「微分」という作用素を $3 \times 3$ 行列で表せ．

手順：

1. 基底 $1$ を微分すると？ $\to 0 = 0\cdot 1 + 0\cdot x + 0\cdot x^2$
    
2. 基底 $x$ を微分すると？ $\to 1 = 1\cdot 1 + 0\cdot x + 0\cdot x^2$
    
3. 基底 $x^2$ を微分すると？ $\to 2x = 0\cdot 1 + 2\cdot x + 0\cdot x^2$
    

これらを列として並べると，どのような行列になるか？（対角成分より一つ上に数字が並ぶはずだ．これを「べき零行列」と呼ぶ）

---

## 3. 演習領域 (Exercise Zone)

_(Note: 定義に基づいて計算し，未知の写像を行列化せよ)_

問題：

空間 $V = \mathbb{R}^2$ 上の線形変換 $f$ が，基底 $\mathbf{e}_1, \mathbf{e}_2$ を以下のように移すとわかっている．

- $f(\mathbf{e}_1) = 2\mathbf{e}_1 + 3\mathbf{e}_2$
    
- $f(\mathbf{e}_2) = 4\mathbf{e}_1 - 5\mathbf{e}_2$
    

(1) この基底に関する $f$ の表現行列 $A$ を求めよ．

解答プロセス：

定義より，$\mathbf{e}_1$ の行き先の係数 $(2, 3)$ を第1列に，$\mathbf{e}_2$ の行き先の係数 $(4, -5)$ を第2列に配置する．

$A = \begin{pmatrix} \_ & \_ \\ \_ & \_ \end{pmatrix}$

(2) ベクトル $\mathbf{x} = 3\mathbf{e}_1 + \mathbf{e}_2$ の像 $f(\mathbf{x})$ を，行列 $A$ を使って計算せよ．

$\mathbf{x}$ の座標ベクトルは $\begin{pmatrix} 3 \\ 1 \end{pmatrix}$ である．

$A \begin{pmatrix} 3 \\ 1 \end{pmatrix} = \begin{pmatrix} \_ & \_ \\ \_ & \_ \end{pmatrix} \begin{pmatrix} 3 \\ 1 \end{pmatrix} = \begin{pmatrix} \_ \\ \_ \end{pmatrix}$

したがって，元の空間での表現に戻すと：

$f(\mathbf{x}) = \_\_ \mathbf{e}_1 + \_\_ \mathbf{e}_2$

検証：

直接計算でも確認せよ．

$f(3\mathbf{e}_1 + \mathbf{e}_2) = 3f(\mathbf{e}_1) + f(\mathbf{e}_2) = 3(2\mathbf{e}_1+3\mathbf{e}_2) + (4\mathbf{e}_1-5\mathbf{e}_2)$

$= \dots$

一致したか？

一致 ______ ．

---

書き写しと演習を完了せよ．

特に「微分の行列化（課題2）」は，量子力学や制御工学において「演算子を行列として扱う」ための原点となる．必ず自分の手で書き下して構造を確認せよ．