# Exercício 1.8.2

Sendo $e = u - u_h$ a função definida como o erro da aproximação de elementos
finitos. Temos que a norma de energia para o problema modelo estudado é dada por:
$$
||e||_{E}^2 = \int_{0}^{1} [e'(u' - u_h') + e (u-u_h)]dx
$$
(1)

Podemos manipular a Eq. (1) como:
$$
||e||_{E}^2 = \int_{0}^{1} [e'(u' - u_h') + e (u-u_h) + e'v_h' - e v_h
+ e v_h -e v_h]dx
$$
Os termos da Eq. acima podem ser reorganizados como:
$$
||e||_{E}^2 = \int_{0}^{1} [e'(u' - v_h') + e (u-v_h)]dx + \\
\int_{0}^{1} [e'(v_h' - u_h') + e (v_h-u_h)]dx
$$
(2)

Para quaisquer funções $v$, $w$ $\in$ $H_{0}^1$, temos:
$$
\int_{0}^{1} (v'w' + vw) dx \leq c ||v||_E ||w||_E
$$
(3)

Pela ortogonalidade temos que o segundo termo da Eq. (2) se anula, e além disso
aplicando (3) em (2) temos:
$$
||e||_E^2 \leq c ||e||_E||u - v_h||_E
$$
(4)

--------------------------------------------------------------------------

Seja $w_h \in H_{0}^{1}$ aquela função teste particular de elementos finitos
que interpola $u$, ou seja, $w_h$ coincide exatamente com $u$ nos nós
da malha. Para essa função temos:
$$
||u - w_h||_E^2 = \int_{0}^{1} [(u'-w_h')^2 + (u-w_h)^2] dx
$$

Que pode ser reescrita como:
$$
||u - w_h||_E^2 = \int_{0}^{1} (u'-w_h')^2 dx + \int_{0}^{1} (u-w_h) dx
$$
(5)

Do cálculo temos a seguinte propriedade que nos ajuda a estimar o valor de uma
integral:
$$
\int_{a}^{b} f(x) dx \leq M(b-a)
$$
(6)

Onde $b > a$ e $M$ é o máximo valor absoluto de $f(x)$ no intervalo $a < x < b$.
Podemos, então, utilizar a propriedade da Eq. (6) para estimar o valor de (5):
$$
||u - w_h||_E^2 \leq c_1 [\max_{0<x<1}|u'-w_h'|^2 + \max_{0<x<1}|u-w_h|^2]
$$
(7)

Agora, então, tentaremos  estimar os valores de máximo absolutos que 
aparecem na Eq. (7):

Sendo $x_A$ e $x_B$ os nós de um elemento, e fazendo a expansão em série de
Taylor para $u(x)$ e $w_h(x)$ em torno de $x_A$ e definindo $\xi = x - x_A$:
$$
u(\xi) = u(x_A) + u'(x_A)\xi + \frac{1}{2} u''(x_A)\xi^2 + O(\xi^3)
$$
(8)

Sendo $w_h$ uma função interpoladora linear de $u$:
$$
w_h(\xi) = w_h(x_A) + \frac{w_B - w_A}{h} \xi
$$
(9)

Subtraindo (9) de (8) e levando em consideração que $w_h = u$ nos nós:
$$
u(\xi)-w_h(\xi) = u'(x_A) - \frac{w_B - w_A}{h}\xi + \frac{1}{2}u''(x_A) 
+ O(\xi^3)
$$

Para um ponto específico $\gamma$ dentro do elemento temos que:
$$
|u(\xi)-w_h(\xi)| = |u'(x_A)\xi - \frac{w_B-w_A}{h}\xi + \frac{1}{2}
u''(\gamma)\xi^2|
$$

E uma vez que $0 < \xi < h$ temos que:
$$
|u(\xi) -w_h(\xi)| \leq c_1 h
$$
(10)

Analisando o máximo do absoluto da diferença das derivadas: isso acontecerá
para um ponto $\alpha$ no qual $u'(\alpha) = w_h'(\alpha)$. Fazendo a expansão
de Taylor em torno deste ponto $\alpha$:
$$
u'(x) = u'(\alpha) + (x-\alpha)u''(x) + O(x-\alpha)
$$
(11)

$$
w_h'(x) = w_h'(\alpha) + 0
$$
(12)

Subtraindo (12) de (11) temos:
$$
u'(x) - w_h'(x) = (x-\alpha)u''(x) + O(x-\alpha)
$$

Que pode ser reescrita em termos de um ponto $\xi$ dentro do intervalo como:
$$
u'(x) - w_h'(x) = (x-\alpha)u''(\xi)
$$
(13)

Para um ponto $\xi$ em $0 < \xi < h$, sabemos que:
$$
|x-\alpha| \leq h
$$
(14)

e também que:
$$
u''(\xi) \leq \max(u''(x)) = c_2
$$
(15)

Com (15) e (14) podemos estimar a Eq. (13):
$$
|u'(x)-w_h'(x)| \leq c_3 h
$$
(16)

Substituindo (10) e (16) em (7), temos:
$$
||u-w_h||_E^2 \leq c h^2
$$
