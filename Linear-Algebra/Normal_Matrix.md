さて，実対称行列が「直交行列で対角化できる」ことは分かった．

では，複素数の世界を含めて，どのような行列ならこれほど美しく（直交基底で）対角化できるのだろうか？

「対称行列」や「直交行列」を包括する，より普遍的な条件が存在する．

それが**「正規行列 (Normal Matrix)」**である．第11章の核心部へ進もう．

---

**Mode A: 講義生成 (Lecture & Transcription Mode)**

# Lecture: Chapter 11.2 Normal Matrices

> Theme: The Grand Unification of Diagonalizability (対角化可能性の大統一)
> 
> Focus: 実対称，エルミット，直交，ユニタリ……これら「性質の良い行列」はすべて**「正規行列」**という一つのクラスに統合される．

## 1. 写経セクション (Transcription Section)

_(Note: 「正規性」こそが，行列が美しく分解できるための必要十分条件である．この定義は線形代数における「良家」の家訓のようなものである)_

### 11.2 正規行列 (Normal Matrix)

定義:

正方行列 $A$ が，その随伴行列 $A^*$（実行列なら転置 $A^T$）と可換（Commutative）であるとき，$A$ を正規行列と呼ぶ．

$$A A^* = A^* A$$

（実行列の場合： $A A^T = A^T A$）

包含関係 (The Hierarchy):

以下の行列はすべて「正規行列」の特殊ケースである．定義式を代入して確認せよ．

1. エルミット行列 ($A^* = A$):
    
    $A A^* = A A = A^2$，逆も $A^2$．ゆえに可換．
    
2. ユニタリ行列 ($A^* = A^{-1}$):
    
    $A A^* = I$，$A^* A = I$．ゆえに可換．
    
3. 歪エルミット行列 ($A^* = -A$):
    
    $A (-A) = -A^2$，逆も $-A^2$．ゆえに可換．
    

定理 (正規行列の基本定理):

複素正方行列 $A$ がユニタリ行列によって対角化可能（つまり，正規直交基底で対角化可能）であるための必要十分条件は，$A$ が正規行列であることである．

$$P^{-1} A P = D \quad (P \text{ is Unitary}) \iff A A^* = A^* A$$

構造的意義 (The Structure):

なぜ「可換性 ($AA^*=A^*A$)」が重要なのか？

それは，行列 $A$ が空間を変換する際，「長さ（ノルム）の変え方」において矛盾がないことを保証するからである．

正規行列であれば，任意のベクトル $x$ に対して $\|Ax\| = \|A^*x\|$ が成り立つ．この「長さの対称性」が，固有ベクトルの直交性を生み出す源泉である．

---

## 2. 再構築領域 (Reconstruction Zone)

_(Note: 実際に手を動かして「正規性」を確認し，その幾何学的意味（回転と拡大の独立性）を感じ取れ)_

### 正規性の判定アルゴリズム

行列 $A = \begin{pmatrix} 1 & -1 \\ 1 & 1 \end{pmatrix}$ （回転拡大行列）を考える．

これが正規行列であることを確認する．

1. 転置 $A^T$ を書く:
    
    $A^T = \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix}$
    
2. 積 $A A^T$ を計算する（行×列）:
    
    $A A^T = \begin{pmatrix} 1 & -1 \\ 1 & 1 \end{pmatrix} \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix} = \begin{pmatrix} 2 & 0 \\ 0 & 2 \end{pmatrix} = 2I$
    
3. 積 $A^T A$ を計算する（列×行）:
    
    $A^T A = \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix} \begin{pmatrix} 1 & -1 \\ 1 & 1 \end{pmatrix} = \begin{pmatrix} 2 & 0 \\ 0 & 2 \end{pmatrix} = 2I$
    
4. 判定:
    
    $A A^T = A^T A$ が成立したため，$A$ は正規行列である．
    
    （注：$A$ は対称行列ではないが，正規行列であるため，複素数の範囲で直交対角化が可能である）
    

---

## 3. 演習領域 (Exercise Zone)

_(Note: 「対称ではないが正規である行列」を扱い，複素対角化の威力を体感せよ)_

**問題 1: 歪対称行列の正規性**

行列 $A = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}$ （90度回転行列）を考える．

これは $A^T = -A$ を満たす（歪対称行列）．

1. 正規性の確認:
    
    $A A^T$ と $A^T A$ を計算し，一致することを示せ．
    
    $A A^T = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix} \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix} = \_\_\_\_\_\_$
    
    $A^T A = \_\_\_\_\_\_$
    
2. 固有値と固有ベクトル（複素数）:
    
    特性方程式 $|A - tI| = t^2 + 1 = 0$ より，固有値は $\lambda = \pm i$ である．
    
    $\lambda = i$ に対応する固有ベクトル $v_1$ を求めよ．
    
    $\begin{pmatrix} -i & -1 \\ 1 & -i \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \mathbf{0} \implies x - iy = 0 \implies v_1 = \begin{pmatrix} i \\ 1 \end{pmatrix}$ (例)
    
    $\lambda = -i$ に対応する固有ベクトル $v_2$ を求めよ．
    
    $v_2 = \_\_\_\_\_\_$
    
3. 直交性の確認:
    
    複素ベクトル空間における内積（エルミット内積）は $(x, y) = x^T \bar{y}$ （または $x^* y$）で定義される．
    
    $v_1$ と $v_2$ の内積を計算し，直交しているか確認せよ．
    
    $(v_1, v_2) = v_1^T \overline{v_2} = \begin{pmatrix} i & 1 \end{pmatrix} \overline{\begin{pmatrix} \dots \\ \dots \end{pmatrix}} = \_\_\_\_\_\_$
    

結論：

行列 $A$ は実数の範囲では対角化できない（回転なので軸がない）．

しかし，複素数まで拡張すれば，______ 行列であるため，直交する固有ベクトルを持って対角化できる．

---

(事後チェック)

問題1-3のヒント: 複素共役 $\overline{i} = -i$ を忘れると内積が0にならない．注意せよ．