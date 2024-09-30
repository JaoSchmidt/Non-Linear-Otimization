### 1.16 Calcule o gradiente e o hessiano das funções $f : \mathbb{R}^n \rightarrow \mathbb{R}$ abaixo:

#### (a) $f(x) = a^t x$;

Tem-se que a seguinte fórmula é equivalente:

$f(x) = \sum^n_{i=1} a_ix_i$

$\nabla f(x) = (\frac{\delta \sum^n_{i=1} a_ix_i}{\delta x_1},
\frac{\delta \sum^n_{i=1} a_ix_i}{\delta x_1},
\frac{\delta \sum^n_{i=1} a_ix_i}{\delta x_3},
...,
\frac{\delta \sum^n_{i=1} a_ix_i}{\delta x_n})$

Fazendo o gradiante:

$\nabla f(x) = (a_1,a_2,a_3,...,a_n) = a$

A matriz Hessaiano será uma matriz $n\times n$ nula: 

$H[f(x)] = \nabla^2 f(x) = [0]_{n\times n}$

 ----

#### (b) $f(x) = \frac{1}{2} x^t A x + b^t x + c$, onde $A \in \mathbb{R}^{n \times n}$, $b \in \mathbb{R}^n$, $c \in \mathbb{R}$;

$\nabla f(x) = \frac{df(x)}{dx}$ (nesse caso, já que há apenas uma variável x)

Fazendo de parcela em parcela:

$\nabla c = 0$ (Vetor nulo de dimensão $n$)

$\nabla^2 c = 0$ (Matriz nula de dimensão $n\times n$)

Segunda parcela, usando a mesma lógica da letra A:

$\nabla b^tx = b$

$H[b^tx] = 0$

Terceira parcela, escrevendo de forma equivalente:

$\newcommand\f{\sum^n_{i=1}\sum^n_{j=1} x_ia_{ij}x_j}
x^tAx = \f \newline
\nabla x^tAx = (\frac{\f}{\delta x_1},
\frac{\f}{\delta x_1},
\frac{\f}{\delta x_3},
...,
\frac{\f}{\delta x_n})$

Como exemplo, ao analisar a primeira dimensão do vetor, tem-se:

$\frac{\delta (\sum^n_{i=1}\sum^n_{j=1} x_ia_{ij}x_j)}{\delta x_1}$

Pode-se separar as parcelas que não serão nulas (i.d dependem de 1):

$\frac{\delta (\sum^n_{i=1}\sum^n_{j=1} x_ia_{ij}x_j)}{\delta x_1}$

$=\frac{\delta a_{11}x_1^2}{\delta x_1} + a_{12}x_2 + a_{13}x_3 + ... + a_{1n}x_n + x_2a_{21} +x_3a_{31} + ... +x_na_{n1}$

Organizando ao isolar o x várias vezes:

$=\frac{\delta a_{11}x_1^2}{\delta x_1} + (a_{12} + a_{21})x_2 +(a_{13} + a_{31})x_3 +...+(a_{1n} + a_{n1})x_n$

Pode-se escrever o primeiro termo da seguinte maneira:

$=(a_{11} + a_{11})x_1 + (a_{12} + a_{21})x_2 +(a_{13} + a_{31})x_3 +...+(a_{1n} + a_{n1})x_n$

Assim, derivando parcialmente em função de $x_2$, tem-se o seguinte:

$=(a_{21} + a_{12})x_1 + (a_{22} + a_{22})x_2 +(a_{23} + a_{32})x_3 +...+(a_{2n} + a_{n2})x_n$

Portanto, pode-se derivar até a dimensão $n$ do gradiente. Para $x_n$:

$=(a_{n1} + a_{1n})x_1 + (a_{2n} + a_{n2})x_2 +(a_{n3} + a_{3n})x_3 +...+(a_{nn} + a_{nn})x_n$

É possível observar que, em cada linha $i$, temos a soma das linhas $i$s das matrizes $A$ e $A^t$.

Portanto a parcela final será:

$\nabla x^tAx = (A + A^t)x$

Por fim

$\nabla f(x) = \frac{1}{2}(A+A^t)x+b$

Para a matriz do hessiano, sabe-se que:

$(A+A^t)x = 
\begin{bmatrix}
(a_{11} + a_{11})x_1 + (a_{12} + a_{21})x_2 + (a_{13} + a_{31})x_3 + \dots + (a_{n1} + a_{1n})x_n \\
(a_{21} + a_{12})x_1 + (a_{22} + a_{22})x_2 + (a_{23} + a_{32})x_3 + \dots + (a_{n2} + a_{2n})x_n \\
\vdots \\
(a_{n1} + a_{1n})x_1 + (a_{n2} + a_{2n})x_2 + (a_{n3} + a_{3n})x_3 + \dots + (a_{nn} + a_{nn})x_n \\
\end{bmatrix}$

Simplificando:

$\nabla f(x) = \frac{1}{2}(A+A^t)x = \frac{1}{2}
\begin{bmatrix}
\sum^n_{i=1} (a_{i1}+a_{1i})x_i\\
\sum^n_{i=1} (a_{i2}+a_{2i})x_i\\
\vdots \\
\sum^n_{i=1} (a_{in}+a_{ni})x_i\\
\end{bmatrix}$

Aplicando Hessaiano:

$\nabla' f(x) = \frac{1}{2}
\begin{bmatrix}
\frac{\delta\sum^n_{i=1} (a_{i1}+a_{1i})x_i}{\delta x_1} & 
\frac{\delta\sum^n_{i=1} (a_{i1}+a_{1i})x_i}{\delta x_2} & \dots &
\frac{\delta\sum^n_{i=1} (a_{i1}+a_{1i})x_i}{\delta x_n} \\
%
\frac{\delta\sum^n_{i=1} (a_{i2}+a_{2i})x_i}{\delta x_1} &
\frac{\delta\sum^n_{i=1} (a_{i2}+a_{2i})x_i}{\delta x_2} & \dots &
\frac{\delta\sum^n_{i=1} (a_{i2}+a_{2i})x_i}{\delta x_n} \\
%
\vdots & \vdots & \ddots & \vdots\\
%
\frac{\delta\sum^n_{i=1} (a_{in}+a_{ni})x_i}{\delta x_1} &
\frac{\delta\sum^n_{i=1} (a_{in}+a_{ni})x_i}{\delta x_2} & \dots &
\frac{\delta\sum^n_{i=1} (a_{in}+a_{ni})x_i}{\delta x_n} \\
\end{bmatrix}$

Resolvendo:

$\nabla' f(x) = \frac{1}{2}
\begin{bmatrix}
a_{11} + a_{11} & 
a_{21} + a_{12} & \dots &
a_{n1} + a_{1n} \\
%
a_{12} + a_{21} & 
a_{22} + a_{22} & \dots &
a_{n2} + a_{2n} \\
%
\vdots & \vdots & \ddots & \vdots\\
%
a_{1n} + a_{n1} & 
a_{2n} + a_{n2} & \dots &
a_{nn} + a_{nn} \\
\end{bmatrix} = \frac{1}{2}(A + A^t)$


#### \(c\) $f(x) = g^t(x) g(x) = \| g(x) \|_2^2$, onde $g : \mathbb{R}^n \rightarrow \mathbb{R}^m$.

### 1.17 Sejam $A ∈ \mathbb{R}^{m×n}$, $b ∈ \mathbb{R}^m$. Para $x ∈ \mathbb{R}^n$, definimos $q(x) = f (Ax + b)$ com $f : \mathbb{R}^m → \mathbb{R}$. Calcule o gradiente e o hessiano da função q:

Usando regra da cadeia no Gradiente:

$\nabla q(x) = \nabla f(Ax+b)(\nabla (Ax))$

Organizando a funçção original

$Ax = 
\begin{bmatrix}
a_{11}x_1 + a_{12}x_2 + a_{13}x_3 + \dots + a_{1n}x_n \\
a_{21}x_1 + a_{22}x_2 + a_{23}x_3 + \dots + a_{2n}x_n \\
\vdots \\
a_{n1}x_1 + a_{n2}x_2 + a_{n3}x_3 + \dots + a_{nn}x_n \\
\end{bmatrix}$

Aplicando derivada parcial em cada uma das dimensões:

$\nabla (Ax) = 
\begin{bmatrix}
a_{11}\\
a_{22}\\
\vdots \\
a_{nn}\\
\end{bmatrix}
=D(A)
$

Assim:

$% Lembrar de perguntar como aplica o gradiente$

$\nabla q(x) = (\nabla f)(Ax+b)*D(A)$

### 2.3 Considere os números reais $a_1 ≤ a_2 ≤ \dots ≤ a_n$. Encontre a solução dos seguintes problemas:

#### (a) Minimizar: $∑^n_{i=1} |x − a_i|$

$f(x) = |x-a_1| + |x-a_2| + |x-a_3| + \dots+ |x-a_n|$

Sabendo que $a_{k+1} \ge a_k$, pode-se fazer $x = k$ e $a_{k+1} > k > a_k$:

Tem-se que:

1. $|k-a_1| >  |k-a_2| > |x-a_3| > \dots > |x-a_k|$

2. $|k-a_n| >  |k-a_{n-1}| > |k-a_{n-2}| > \dots > |k-a_{k+1}|$

Portanto:

$f(k) = k - a_1 + k - a_2 + \dots + k - a_k + a_{k+1} - k + \dots a_n - k$

$= k*k - (n-k)*k - \sum^k_{i=1} a_i + \sum^n_{i=k+1} a_i$

$= k(k - n + k)- \sum^k_{i=1} a_i + \sum^n_{i=k+1} a_i$

$= 2k^2 - nk- \sum^k_{i=1} a_i + \sum^n_{i=k+1} a_i$

A primeira parcela $(2k^2 - nk)$ possui raizes $0$ e $n/2$, com $k^*=n/4$ e mínimo igual a $n^2/8$

A segunda parcela $(-\sum^k_{i=1} a_i + \sum^n_{i=k+1} a_i)$ possui $k^*=n$ com mínimo igual a $-\sum^n_{i=1} a_i$

#### (b) Minimizar: $\max\{|x − a_i|, i=1,\dots ,n\}$

$f(x) = \max(|x-a_1|, |x-a_2|,|x-a_3|, \dots,|x-a_n|)$

Sabendo que $a_{k+1} \ge a_k$, pode-se fazer $x = k$ e $a_{k+1} > k > a_k$:

Tem-se que:

1. $|k-a_1| >  |k-a_2| > |x-a_3| > \dots > |x-a_k|$

2. $|k-a_n| >  |k-a_{n-1}| > |k-a_{n-2}| > \dots > |k-a_{k+1}|$

Assim:

$f(x) = \max(|x-a_1|, |x-a_2|,|x-a_3|, \dots,|x-a_n|)$

$= \max(|x-a_1|, |x-a_n|)$

Portanto, o $x^* = \frac{a_1 + a_n}{2}$

$f(x^*) = \frac{a_n-a_1}{2}$

#### \(c\) Minimizar: $∑^n_{i=1} |x − a_i|^2$

Pela definição de módulo, tem-se $|x-a_i| = \sqrt{(x-a_i)^2}$

Assim, o problema é equivalente a minimizar $f(x) = ∑^n_{i=1} (x − a_i)^2$

Abrindo:

 $∑^n_{i=1} (x − a_i)^2 = ∑^n_{i=1} (x^2 − 2xa_i + a_i^2) = nx^2 - 2x ∑^n_{i=1}a_i +∑^n_{i=1}a_i^2$

Podemos achar $x^*$ ignorando as parcelas constantes:

Minimizar: $nx^2 - 2x ∑^n_{i=1}a_i$

Portanto $x^* =  \frac{∑^n_{i=1}a_i}{n}$ 

#### (d) Minimizar: $\prod^n_{i=1} |x − a_i|$

Novamente, sabendo que $a_{k+1} \ge a_k$, pode-se fazer $x = k$ e $a_{k+1} > k > a_k$:

Assim, o problema original é equivalente a:

 $(k − a_1)(k-a_2)(k-a_3)\dots(k-a_k)(a_{k+1}-k)\dots(a_{n-1}-k)(a_n-k) \ge0$

No entanto, podemos multplicar por $\frac{-1}{-1}$ várias vezes e chegar numa fórmula mais limpa

(pular)

### 2.4 Obtenha expressões para as derivadas primeiras e segundas da função de Rosenbrock $f (x) = 100(x_2 − x^2_1)^2 + (1 − x_1)^2$. Verifique que $ẍ = (1, 1)^t$ é um minimizador local. Prove que $∇^2f (ẍ)$ é singular se e somente se $x_2 −x^2_1 = 0.005$

Achando o gradiente

$\nabla f(x) = (200(x_2-x_1^2)(-2x_1) + 2(1-x_1)*(-1),\ 200(x_2-x^2_1))$

$= (-400x_2x_1 + 400x^3_1 - 2 + 2x_1,\ 200x_2 - 200x^2_1)$

Igualando ao vetor nulo:

$\begin{cases}
400x_2x_1 + 400x^3_1 - 2 + 2x_1 = 0 \\
200x_2 - 200x^2_1 = 0
\end{cases}$

Primeira equação:

$200x_2 - 200x^2_1 = 0 \implies x_2= x_1^2$

Substituindo:

$400x^3_1 + 400x^3_1 -2 + 2x_1 = 0 \implies x_1 = 1$

$\therefore x_1 = 1$ & $x_2 = x_1^2 \implies x_2 = 1$ $QED$

**(b) Provando singular quando $x_2 - x_1^2 = 0.005$**

> OBS: A matriz Hessiana $\nabla ^2 f(x)$  é dita singular se não é invertível i.e. determinante é zero.

$\nabla f(x)= (-400x_2x_1 + 400x^3_1 - 2 + 2x_1,\ 200x_2 - 200x^2_1)$

$det(H_f) = 
\begin{vmatrix}
-400x_2 + 1200x_1^2 + 2 & -400x_1\\
-400x_1 & 200
\end{vmatrix}
= -8*10^4x_2+24*10^4x_1^2 + 400 - 16*10^4x_1^2$

$=8*10^4x_2 - 8*10^4x_1^2+400=0$

Dividindo por 400:

$=200x_2 - 200x_1^2+1=0$

Dividindo por 200:

$x_2 - x_1^2 + 0.005 = 0 \implies x_2 - x_1^2 = 0.005$ QED

### Questão 2.5

**Encontre os pontos estacionários de**

$f(x) = 2x^3 - 3x^2 - 6x y (x - y - 1)$

**Quais desses pontos são minimizadores ou maximizadores, locais ou globais?**

$f(x) = 2x^3 - 3x^2 - 6x y (x - y - 1) = 2x^3 - 3x^2 - 6x^2 y + 6xy^2 + 6xy$


$\nabla f(x) = (6x^2 - 6x - 12xy + 12y^2 + 6y,\ -6x^2 + 12xy + 6x)$

Simplificando:

$\nabla f(x) = (6x^2 - 6x - 12xy + 12y^2 + 6y,\ -6x^2 + 12xy + 6x)$

$\begin{cases}
6x^2 - 6x - 12xy + 12y^2 + 6y = 0 \\
-6x^2 + 12xy + 6x = 0
\end{cases}$

Dividindo por $6$:

$\begin{cases}
x^2 - x - 2xy + 2y^2 + y = 0 \\
-x^2 + 2xy + x = 0
\end{cases}$

Isolando o $y$ na segunda linha e dividindo por x:

> Obs: Com isso, também tem-se $x= 0$ como solução, que resolve a primeira equação quando $y=0$ também.

$\begin{cases}
x^2 - x - 2xy + 2y^2 + y = 0 \\
y = \frac{x - 1}{2} 
\end{cases}$

Substituindo $y$ por $\frac{x-1}{2}$ na primeira equação:

$x^2 - x - 2x\frac{x-1}{2} + \frac{x^2-2x+1}{2} + \frac{x-1}{2} = 0$

Separando as somas das frações:

$x^2 - x - x^2 + x + \frac{x^2}{2} -x +\frac{1}{2} + \frac{x}{2} - \frac{1}{2} = 0$

Removendo os termos nulos:

$\frac{x^2}{2} -x + \frac{x}{2} = 0 \implies x^2 - x = 0$

Já sabe-se do ponto $(0,0)$, mas agora obtem-se o ponto $x=1$ e $y=0$

Pela hessiana:

$\nabla^2 f(x)=\begin{bmatrix}
12x - 6 -12y & -12x +24y + 6 \\
-12x + 24y + 6 & 12x
\end{bmatrix}$

Tem-se o caso 1: hessiana no $x^* = (0,0)$:

No ponto $x^* = (0,0)$ com um vetor $d = (d_1,d_2)$ qualquer, tem-se:

$\nabla^2 d^T*f(x^*)*d = d^T*
\begin{bmatrix}
-6 & 6\\
6 & 0 
\end{bmatrix}*d= -6d_1^2 + 6d_2^2 + 6d_1d_2$

Portano hessiana $\nabla f(0,0)$ é indefinida. Com o ponto $(0,0)$ como sela

Caso 2: hessiana no $x^* = (1,0)$:

$\nabla^2 d^T*f(x^*)*d = d^T*
\begin{bmatrix}
6 & -6\\
-6 & 12 
\end{bmatrix}*d= 6d_1^2 -6d_1d_2 - 6d_1d_2 + 12d_2^2 = 6(d_1-d_2)^2 + 6d_2^2 > 0$

Portano hessiana $\nabla f(1,0)$ é definida positiva. Com o ponto $(1,0)$ mínimizador.

### Questão 2.6

**Seja $f(x) = (x_1 - x_2^2)(x_1 - \frac{1}{2}x_2^2)$. Verifique que $\bar{x} = (0, 0)^t$ é um minimizador local de  $\varphi(\lambda) \equiv f(\bar{x} + \lambda d)$ para todo $d \in \mathbb{R}^2$, mas $\bar{x}$ não é minimizador local de $f$.**
