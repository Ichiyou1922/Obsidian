$\mathbb{R}^3$ の部分集合 $W$ を以下のように定義する．

$$W = \{ \boldsymbol{x} = \begin{pmatrix} x \\ y \\ z \end{pmatrix} \in \mathbb{R}^3 \mid x + y + z = 0 \}$$

この $W$ は $\mathbb{R}^3$ の部分空間か？

**検証プロセス：**

(1) 零ベクトルの確認

まず，零ベクトル $\mathbf{0} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$ が $W$ に含まれるか確認する．

条件式 $x + y + z = 0$ に代入すると: 
$0 + 0 + 0 = 0$
よって，零ベクトルは $W$ に含まれる．

(2) 加法についての閉性

任意の2つのベクトル $\boldsymbol{u} = \begin{pmatrix} u_1 \\ u_2 \\ u_3 \end{pmatrix} \in W$，$\boldsymbol{v} = \begin{pmatrix} v_1 \\ v_2 \\ v_3 \end{pmatrix} \in W$ を取る．

これらが $W$ の元であるという前提条件は，以下の式で表される：

（$\boldsymbol{u}$ について）:

$u_1 + u_2 + u_3 = 0$ 

（$\boldsymbol{v}$ について）:

$v_1 + v_2 + v_3 = 0$
  

今，和 $\boldsymbol{u} + \boldsymbol{v} = \begin{pmatrix} u_1+v_1 \\ u_2+v_2 \\ u_3+v_3 \end{pmatrix}$ を考える．

この和の成分が条件 $X + Y + Z = 0$ を満たすかどうかを計算する．

$(u_1+v_1) + (u_2+v_2) + (u_3+v_3) = (u_1 + u_2 + u_3) + (v_1 + v_2 + v_3) = 0$
この結果は $0$ になるか？ 理由と共に記述せよ：
$\mathbb{u}, \mathbb{v}$ の前提条件より=0が成り立つ．
よって，加法について閉じている．

(3) スカラー乗法についての閉性

任意のスカラー $k \in \mathbb{R}$ と $\boldsymbol{u} \in W$ に対し，$k\boldsymbol{u} = \begin{pmatrix} ku_1 \\ ku_2 \\ ku_3 \end{pmatrix}$ を考える．

成分の和を計算する：

$(ku_1) + (ku_2) + (ku_3) = k(u_1 + u_2 + u_3) = k\cdot 0 = 0$

よって，スカラー乗法について閉じている．

結論：

以上の (1), (2), (3) より，$W$ は $\mathbb{R}^3$ の部分空間である．
