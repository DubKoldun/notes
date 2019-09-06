## $\lambda - calculation$

Алонзо Чёрч ~ 40 годы. Развитие идеи, что все - функция
Рассмотрим алфавит. 

$pre- \lambda -term \ T \ := 
\left\{ 
	\begin{array}{ll} 
   		x \ (variable; set \ of \ small \ letter \ with \ indices); \\
		(T,T) \ (application); \\ 
		\lambda x.T \ (abstraction). \\  
	\end{array} 
\right. $

x,y - метапеременные для переменных
большие буквы - метапеременные для T

Назовем два $ pre- \lambda -terms$ (P,Q)  $ \alpha$ - эквивалентными, если  

1. P=x Q=y и x=y
2. P = (S<sub>1</sub>T<sub>1</sub>) Q = (S<sub>2</sub>T<sub>2</sub>) и S<sub>1</sub> = $\alpha$S<sub>2</sub>, T<sub>1</sub> = $\alpha$T<sub>2</sub> 
3. P = $(\lambda x.A) \ Q \ =  \ \lambda y.B \ and \  A[x:=t] B[y:=t] \ t $ - свободная переменна

Равенство <=> текстовое совпадение
$A[x:=B] = 
\left \{
\begin{array}{ll} 
B  , \  A=x \\
A,  \ A=y, \ y!=x \\
P[x:=B] \  Q[x:B] \ A = (PQ) \\
\lambda y.p[x:=B] \ if  \ A = \lambda y.P \  and \ y \ \neq x \\
A \ if \ A= \lambda x.P
\end{array} 
\right. $

$Example\\
(\lambda x.(lambday.(yx))) [x:=p]
lambdat.[(lambday.(y.x))] [x:=p]
lambdat. lambday((y.x)[x:=p]) -> lambdat.lambday.y[x:=p] x[x:=p] -> (lambdat.(lambday.yp)) $
$$
(\lambda a.\lambda b(a b)c)d)e))f)g
$$

$$
(\lambda x.a)[x:=t] => \lambda x.a
$$

$$
FV(T) = \left\{check pic\right.
$$

lambda term - класс эквивалентности lambda-termov по отношению эквивалентности

def. \beta - редекс

def. \alpha -><sub>b</sub> B находятся в отношении B - редукции, если

1. A = PQ B = RS. P -><sub>B</sub>R Q=<sub>alpha</sub> S либо (знаки отрази)  
2. A - B - редекс A = (Lambdax.P) Q, B =p[x:=Q] при условии, что Q  обобщается для подстановки для x в P

Ex. \beta-редекс ($\Latex$) beta$



* ``Def.``  Нормальная форма если нет ни одного $\beta -redex$ 

* ``Ex.``  $\Omega = \omega \ \omega$ 

* `Statement` 

  Теорема Чёрча Росса 

``` cpp
int main() {
    call();
    return 0;
}
```

