## $\lambda - calculation$

_Алонзо Чёрч_ ~ 40 годы. Развитие идеи, что все - функция

Рассмотрим алфавит


$$
pre- \lambda -term \ T \ :=
\left\{
	\begin{array}{ll}
   		x \ (variable; set \ of \ small \ letter \ with \ indices); \\
		(T,T) \ (application); \\
		\lambda x.T \ (abstraction). \\
	\end{array}
\right.
$$



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

**def** $\alpha$ -><sub>$\beta$</sub> B находятся в отношении $\beta $ - редукции, если

1. A = PQ B = RS. P -><sub>$\beta$</sub>R Q =<sub>$\alpha$</sub> S либо (знаки отрази)
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

---

**def** *Транзитивное, рефлексивное и симметричное замыкание* $(\rightarrow _\beta)$ - отношение $\beta$-редуцируемости ( $\beta$-редукции)

Если для A и B существует конечная поледовательность X~n~ ... X~n~ X~1~ = A, X~n~ = B, $X_i \rightarrow_\beta X_{i + 1}$ 

То $A \rightarrow_\beta B$

**def** *Транзитивное, рефлексивное и симметричное замыкание* $(\rightarrow_\beta)$ - есть $(=_\beta)$

R-отношение $\subseteq U^2$

R обладает ромбовидным свойством, если для любых A, B, C $\in U$

1. $B \ne C$
2. $(A, B) \in R \ \ (A, C) \in R$

Существует $D \in U$:

​    $(B, D) \in R\ \ (C, D) \in R$

```mermaid
graph TD;
    A --> B
    A --> C
    B --> D
    C --> D
```

> $\beta$-редукция не обладает ромбовидным свойством

**def** *комбинатор* - $\lambda$-выражение без свободных переменных

$Identit \ddot{a} t = \lambda x.x$

$verSchmelrung = \lambda x. \lambda y. \lambda z. x\ z\ (y \ z)$

$Konstant = \lambda x. \lambda y. x$

$I =_\beta S\ K \ K$

```mermaid
graph TD;
    A[\x -> x x x (II)] --> B[\x -> x x x (I)]
```

## Теорема Чёрча Росса

$(\twoheadrightarrow_\beta)$ обладает ромбовидным свойством

**def** $(\stackrel{\rightarrow}{\rightarrow_\beta})$ отношение параллельной $\beta$-редукции

$A \rightrightarrows_\beta$, если 

1. $A \equiv \lambda x. P, B = \lambda x. Q, P \rightrightarrows_\beta Q$

2. $A = (\lambda x. P) Q, B = P [x = Q] $ (если есть в каждой подстановке)

3. $A = P_1 Q_1, B = P_2 Q_2$

    $P_1 = P_2 \ or\ P_1 \rightrightarrows_\beta P_2$

    $Q_1 = Q_2 \ or Q_1 \rightrightarrows_\beta Q_2$

4. $A = x, B = x, x \rightrightarrows_\beta x$

**stat** схема доказательства Чёрча Росса

1. $(\rightrightarrows_\beta)$ обладает ромбовидным свойством
2. Если R обладает ромбовидным свойстовм, то R^*^ - транзитивное замыкание обладает ромбовидным свойством
3. Из (1) и (2) следует, что $(\rightrightarrows_\beta)^*$ обладает ромбовидным свойством
4. $(\rightarrow_\beta) \subseteq (\rightrightarrows_\beta)$
5. $(\rightrightarrows_\beta)^* \subseteq (\twoheadrightarrow_\beta)$
6. $(\rightrightarrows_\beta)^* = (\twoheadrightarrow_\beta)$
7. $(\twoheadrightarrow_\beta)$ обладает ромбовидным свойством

### Следствие из теоремы Чёрча Росса

У $\lambda$-терма не может быть двух не равных нормальных форм

Пусть $A \twoheadrightarrow_\beta X, A \twoheadrightarrow_\beta Y$, причём $X \ne Y$

Тогда по ромбовидному свойству существует $T: X \twoheadrightarrow_\beta T, \ Y \twoheadrightarrow_\beta T$

Если $X = T, Y = T$, то  $ X = Y$ невозможно

Значит одно из равенств не выполняется, пусть $X \ne T$

Значит X - ненормальная форма А

**def** $(=_\beta)$ - транзитивное, рефлексивное и симметричное замыкание $(\rightarrow_\beta)$

Y - комбинатор 

Оператор неподвижной терма

$\Omega = (\lambda x. x\ x) (\lambda x. x\ x)$

$Y = \lambda f. (\lambda x. f \ (x\ x)) (\lambda x. f (x \ x))$

$x =_\beta A\ x, \ \ \ \ x = ?$

Давайте рассмотрим $x = Y A$

$YA = _\beta A (Y A)$

$YA = (\lambda f. (\lambda x. f(x \ x)) (\lambda x. f(x\ x))) A \rightarrow_\beta \\ (\lambda x. A (x \ x)) (\lambda x. A (x \ x)) \rightarrow_\beta A [(\lambda x. A(x \ x)) (\lambda x. A (x \ x))]$

$$
Fact = \lambda f. \lambda a . ((>) \ a\ 0)\\
((*)\ a\ [f\ ((-1)\ a)])\ 1\\
---\\
(Y\ Fact)\ 3 \rightarrow Fact\ (Y \ Fact) \ 3 \rightarrow_\beta \\
(*)\ 3\ ((Y \ Fact) \ 2) \rightarrow (*) \ 3\ [(*) \ 2\ [(*) \ 1 \ [Y \ Fact \ 0]]]
$$

## Нормальный порядок редукции

**def** самый левый редекс - это редекс с минимальной редукцией его первого символа

*Нормальный порядок редукции* - редуцируете самый левый редекс

### Теорема

Если нормальная форма существует, то она может быть получена п. л. (??)

