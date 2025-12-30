Phase 1の主眼は，**「実数世界の直観（普通の距離・角度）」を「複素数世界（信号の世界）」へ安全に移植すること**にある．

信号処理において，信号は複素数で扱われる（振幅と位相を持つため）．

しかし，我々が知る「長さ（ノルム）」は常に実数でなければならない．「長さが $3 + 2i$ メートル」などという物理量は存在しないからだ．

この矛盾を解決する装置こそが，**「エルミート内積（Hermitian Inner Product）」**である．

---

# Phase 1 Lecture: The Geometry of Complex Signals

> Theme: From Euclidean to Hermitian (ユークリッドからエルミートへ)
> 
> Focus: なぜ「共役（Conjugate）」をとるのか？ その必然性を構造から理解する．

## 1. 写経セクション (Transcription Section)

以下の定義と論理をノート（またはMarkdown）に転写せよ．

### 1.1 複素ベクトル空間 $\mathbb{C}^N$

信号処理における「デジタル信号」とは，複素数を成分に持つ $N$ 次元ベクトルである．

$$\mathbf{x} = \begin{pmatrix} x_0 \\ x_1 \\ \vdots \\ x_{N-1} \end{pmatrix} \in \mathbb{C}^N$$

ここで各成分 $x_n$ は $a + bi$ の形をしている．

### 1.2 エルミート内積 (Hermitian Inner Product)

実ベクトル空間では，内積は $( \mathbf{x}, \mathbf{y} ) = \mathbf{x}^T \mathbf{y}$ であった．

複素空間では，これを以下のように修正する．

定義:

2つの複素ベクトル $\mathbf{x}, \mathbf{y}$ の内積 $\langle \mathbf{x}, \mathbf{y} \rangle$ を以下で定義する．

$$\langle \mathbf{x}, \mathbf{y} \rangle = \sum_{n=0}^{N-1} x_n \overline{y_n} = \mathbf{x}^T \overline{\mathbf{y}} \quad (\text{あるいは } \mathbf{y}^H \mathbf{x} \text{ と定義する流儀もある})$$

ここで $\overline{y_n}$ は $y_n$ の複素共役 (Complex Conjugate) である．

（※物理・工学分野では，右側のベクトルを共役にするのが一般的だが，数学書では左側を共役にする場合もある．本プロジェクトでは**「右側（相手）を共役にする」**で統一する．）

### 1.3 なぜ共役が必要か？ (The Necessity of Conjugation)

もし共役をとらずに $\sum x_n y_n$ と定義してしまうと，自分自身との内積（ノルムの2乗）が破綻する．

例：$\mathbf{x} = (i)$ のとき，単純な積和では $i \cdot i = -1$ となり，「長さの2乗がマイナス」という致命的なバグが発生する．

共役をとることで：

$$\langle \mathbf{x}, \mathbf{x} \rangle = \sum x_n \overline{x_n} = \sum |x_n|^2 \ge 0$$

となり，「長さ（エネルギー）」が常に正の実数になることが保証される．これを正定値性と呼ぶ．

### 1.4 性質：共役対称性 (Conjugate Symmetry)

実内積のように「入れ替えても同じ」ではない．入れ替えると共役になる．

$$\langle \mathbf{y}, \mathbf{x} \rangle = \overline{\langle \mathbf{x}, \mathbf{y} \rangle}$$

---

## 2. 再構築領域 (Reconstruction Zone)

この数学的構造を，Rustの型システムとして実装するための設計図を描く．

以下の仕様を満たすコードを src/main.rs (あるいはモジュール) に実装せよ．

### 構造体設計

1. **`Complex` 構造体**:
    
    - フィールド: `re: f64`, `im: f64`
        
    - メソッド `conjugate(&self) -> Complex`: 虚部の符号を反転した新しい複素数を返す．
        
    - メソッド `mul(&self, other: &Complex) -> Complex`: 複素数同士の積．$(a+bi)(c+di) = (ac-bd) + (ad+bc)i$．
        
2. **`Signal` 構造体**:
    
    - フィールド: `data: Vec<Complex>`
        
    - メソッド `new(data: Vec<Complex>) -> Self`
        

### アルゴリズム: `inner_product`

`Signal` 構造体に以下のメソッドを実装せよ．

Rust

```
// 擬似コード (Logic)
fn inner_product(&self, other: &Signal) -> Complex {
    // 1. Assert lengths are equal (次元が合わなければ計算不能)
    // 2. Initialize sum = 0 + 0i
    // 3. Loop through elements:
    //      sum += self[i] * other[i].conjugate()  <-- 重要：ここで共役をとる
    // 4. Return sum
}
```

この実装により，コード上の `signal_a.inner_product(&signal_b)` が，数学的な $\langle \mathbf{a}, \mathbf{b} \rangle$ と**完全に同型**になる．

---

## 3. 演習領域 (Exercise Zone)

実装前に，手計算で「期待値」を算出せよ．これがユニットテストの正解データとなる．

問題:

2次元複素ベクトル $\mathbf{x}, \mathbf{y}$ を以下とする．

$$\mathbf{x} = \begin{pmatrix} 1 + i \\ 2 \end{pmatrix}, \quad \mathbf{y} = \begin{pmatrix} 1 - i \\ 3 \end{pmatrix}$$

1. 内積 $\langle \mathbf{x}, \mathbf{y} \rangle$ を計算せよ．
    
    定義：$x_0 \overline{y_0} + x_1 \overline{y_1}$
    
    - $y_0 = 1 - i$ なので，$\overline{y_0} = \_\_\_\_\_\_$
        
    - 第1項：$(1+i)(\_\_\_\_\_\_) = \_\_\_\_\_\_$
        
    - 第2項：$2 \cdot 3 = 6$ (実数の共役はそのまま)
        
    - 合計：$\_\_\_\_\_\_$
        
2. **ノルムの2乗 $\langle \mathbf{x}, \mathbf{x} \rangle$ を計算せよ．**
    
    - $|x_0|^2 = |1+i|^2 = 1^2 + 1^2 = \_\_\_\_$
        
    - $|x_1|^2 = 2^2 = 4$
        
    - 合計：$\_\_\_\_\_\_$ （※必ず実数になることを確認せよ）
        

---

(Next Action)

この講義内容を元に，Linear-Algebra/Inner_Product.md を更新し，Rustで Complex と Signal の基本実装を行え．

実装ができたらコードを提示せよ．「共役」の処理が正しく実装されているか査読する．