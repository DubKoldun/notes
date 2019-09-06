## $\lambda - calculation$

_Алонзо Чёрч_ ~ 40 годы. Развитие идеи, что все - функция

Рассмотрим алфавит

$pre- \lambda -term \ T \ :=
\left\{
	\begin{array}{ll}
   		x \ (variable; set \ of \ small \ letter \ with \ indices); \\
		(T,T) \ (application); \\
		\lambda x.T \ (abstraction). \\
	\end{array}
\right. $

x, y - метапеременные для переменных
большие буквы - метапеременные для T

Назовем два $ pre- \lambda -terms$ (P, Q)  $ \alpha$ - **эквивалентными**, если

1. P = x Q = y и x = y
2. P = (S<sub>1</sub>T<sub>1</sub>) Q = (S<sub>2</sub>T<sub>2</sub>) и S<sub>1</sub> = $\alpha$S<sub>2</sub>, T<sub>1</sub> = $\alpha$T<sub>2</sub>
3. P = $(\lambda x.A) \ Q \ =  \ \lambda y.B \ and \  A[x:=t] B[y:=t] \ t $ - свободная переменна

**Равенство** <=> текстовое совпадение
$$
A[x:=B] =
	\left \{
		\begin{array}{ll}
			B  , \  A=x \\
			A,  \ A=y, \ y!=x \\
			P[x:=B] \  Q[x:B] \ A = (PQ) \\
			\lambda y.p[x:=B] \ if  \ A = \lambda y.P \  and \ y \ \neq x \\
			A \ if \ A= \lambda x.P
		\end{array}
	\right.
$$
**Example**
$ (\lambda x.(\lambda y.(y x))) [x := p] \rightarrow
\lambda t.[(\lambda y.(y.x))] [x := p] \rightarrow \\
\lambda t. \lambda y((y.x)[x := p]) \rightarrow \lambda t.\lambda y.y[x := p] x[x := p] \rightarrow (\lambda t.(\lambda y.yp)) $

1. аппликация левоассоциативна: $x.y.r.t = (((x y)r)t)$
2. $\lambda$ берёт всё, что дают: $((\lambda a.(\lambda b (((((ab)c)d)e))f)g)$

$$
FV(T) =
	\left \{
		\begin{array}{ll}
			\{x\}, T = x \\
			FV(P) \cup FV(Q), T = PQ \\
			FV(P) \setminus \{x\}, T = \lambda x.P
		\end{array}
	\right.
$$

**lambda term** - класс эквивалентности lambda-term'ов по отношению эквивалентности

**def** **$\beta$-редекс**

**def** $\alpha$ -><sub>b</sub> B находятся в отношении B - редукции, если

1. A = PQ B = RS. P -><sub>B</sub>R Q =<sub>$\alpha$</sub> S либо (знаки отрази)
2. A - B - редекс A = ($\lambda$ x.P) Q, B = p[x := Q] при условии, что Q  обобщается для подстановки для x в P

**example**
$$
\lambda a. \lambda b. a \ - И = T \\
\lambda a. \lambda b. b \ - Л = F \\
And = \lambda x. \lambda y. x \ y \ F \\
And \ T \ F = ((\lambda x. \lambda y x \ y \ F) T) F \rightarrow _\beta ((\lambda y. x \ y \ F) [x := T]) F = \\
= (\lambda y. T \ y \ F) F \rightarrow _\beta T \ F \ F = ((\lambda a. \lambda b. a) F) F) \rightarrow _\beta (\lambda b. F) F \rightarrow _\beta F
$$


### Чёрчевские нумералы

$\lambda f. \lambda x. f^n x$

$f^k (x) =
	\left \{
		\begin{array}{ll}
			x, n = 0 \\
			f(f^{n - 1}, n > 0)
		\end{array}
	\right.$

$\overline{2} = \lambda n.\lambda f. \lambda x. n \ f \ (f \ x)$

_Карринг_: a (+) b: `let plus a = fun x -> x + a`

`plus 1 3 = (plus 1) 3 = 4`

**def**  **Нормальная форма** - нет ни одного $\beta$-редексов (невозможно редуцировать)

**example:** $\omega = \lambda f . \lambda x. x. x$

$\Omega = \omega \omega$

**statement** $\Omega$ не имеет норм.

$(\lambda x. x. x) \omega = \omega. \omega$

У выражения существует нормальная форма, если существует последовательность $\rightarrow _\beta$, приводящая к нормальной форме

### Теорема Чёрча Росса

Существует не более одной нормальной формы у любого выражения



