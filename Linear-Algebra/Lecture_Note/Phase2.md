
# Phase 2: The Rotation of Basis (基底の回転)

> Theme: DFT as a Matrix Operator
> 
> Focus: 信号を「時間」の座標系から「周波数」の座標系へ回転させる．

準備運動（Phase 1）は終わった．

我々は今，複素ベクトル空間 $\mathbb{C}^N$ という「舞台」と，距離を測る「定規（内積）」を手に入れた．

次に行うのは，この空間内でベクトルを**回転（基底変換）**させる操作，すなわち **DFT（離散フーリエ変換）** の実装である．

## 1. 写経セクション (Transcription Section)

### 2.1 フーリエ基底 (Fourier Basis)

$\mathbb{C}^N$ 空間において，以下の $N$ 個のベクトルセット $\{\mathbf{e}_0, \mathbf{e}_1, \dots, \mathbf{e}_{N-1}\}$ を考える．

第 $k$ 番目の基底ベクトル $\mathbf{e}_k$ の 第 $n$ 成分 $e_k[n]$ は以下で定義される．

$$e_k[n] = \exp\left( j \frac{2\pi}{N} k n \right) = \cos\left( \frac{2\pi}{N} kn \right) + j \sin\left( \frac{2\pi}{N} kn \right)$$

これは，複素平面上の単位円を周波数 $k$ で回転する「純粋な波」である．

### 2.2 直交性 (Orthogonality)

驚くべきことに，これらの基底は互いに直交している（ただし正規化係数を無視すれば）．

$$\langle \mathbf{e}_k, \mathbf{e}_l \rangle = \begin{cases} N & (k = l) \\ 0 & (k \neq l) \end{cases}$$

この性質ゆえに，任意の信号 $\mathbf{x}$ は，これらの基底の和として一意に分解できる．

### 2.3 DFTの定義 (再)

DFTとは，入力信号 $\mathbf{x}$ と，各基底 $\mathbf{e}_k$ との**内積をとる操作**に他ならない．

$$X[k] = \langle \mathbf{x}, \mathbf{e}_k \rangle = \sum_{n=0}^{N-1} x[n] \overline{e_k[n]} = \sum_{n=0}^{N-1} x[n] \exp\left( -j \frac{2\pi}{N} kn \right)$$

（※ここで $\overline{e_k[n]}$ により指数部の符号がマイナスになることに注意せよ．これがDFTの式にマイナスがついている理由である）

---

## 2. 実装課題 (Implementation Task)

Signal 構造体を拡張し，以下の機能を実装せよ．

ライブラリ（PI, cos, sin）は std::f64::consts::PI 等を使用せよ．

### Task 2.1: 基底生成メソッド

指定された長さ $N$ と周波数 $k$ を持つ基底信号を生成せよ．

Rust

```
impl Signal {
    // 周波数 k の基底ベクトル e_k を生成
    fn basis(n: usize, k: usize) -> Signal {
        let mut data = Vec::with_capacity(n);
        // ループで exp(j * 2π * k * i / n) を計算し push
        // Eulerの公式: exp(jθ) = cos(θ) + j*sin(θ)
        // ...
        Signal::new(data)
    }
}
```

### Task 2.2: DFTメソッド

自身の信号を DFT 変換し，スペクトル（複素数のベクトルのまま）を返せ．

Rust

```
impl Signal {
    // DFT: X[k] = <x, e_k>
    fn dft(&self) -> Signal {
        let n = self.data.len();
        let mut spectrum_data = Vec::with_capacity(n);
        
        for k in 0..n {
            let e_k = Signal::basis(n, k);
            let x_k = self.inner_product(&e_k).unwrap(); // <x, e_k>
            spectrum_data.push(x_k);
        }
        
        Signal::new(spectrum_data)
    }
}
```

(Action)

この2つのメソッドを実装し，main 関数で以下の実験を行え．

1. 長さ $N=8$ 程度の信号 $\mathbf{x}$ を適当に作る（例：全部1, あるいは単純なサイン波）．
    
2. `dft` を実行する．
    
3. 結果を表示し，特定の $k$ に値が集中しているか（あるいは拡散しているか）を確認せよ．
    

実装ができたらコードを提示せよ．次は「窓関数」により，この綺麗な数学的世界が現実世界でどう歪むかを見る．