# Теория Вероятности и Математическая Статистика

> Суслина Ирина Александровна
>
> ---
>
> Литература:
>
> Боровков АА ТВ М 1986
>
> Прохоров ЮВ ТВ М 1975

Базовый объект ТВ ($\Omega, \ \Sigma, \ P$), где $\Omega$ - пространство элементарных исходов, $\Sigma$ - $\sigma$-алгебра множеств (событий), P : $\Sigma \rightarrow [0,\ 1], \forall A \in \Sigma: p = p(A)$ - вероятностная мера

$\Omega = \{\omega\}$, $\omega$ - элементарный исход

эксперимент => один и только один элементарный исход

эксперимент можно повторить многократно в идентичных условиях

**def** $(\Omega, \ \Sigma)$ - измеримое пространство, $(\Omega, \ \Sigma, \ P)$ - вероятностное пространство

**def** измеримое пространство $(\Omega, \ \Sigma)$, где $\Omega$ - не более, чем счётно; здесь $\Sigma$ - множество всех подмножеств

Если $\Omega$ более чем счётно

$\sigma$-алгебра должна быть указана конкретная

Любой элемент из $\Sigma$ определяется событием A, B, C

### Действия

1. $A + B = C \ (A \cup B)$
2. $A \times B = C \ (A \cap B)$
3. $A \setminus B = C$
4. $\overline{A} = \Omega \setminus A$

### Свойства

1. $A + B = B + A$

    $(A + B) + C = A + (B + C) = A + B + C$

2. $A \times B = B \times A$

    $(A \times B) \times C = A \times (B \times C) = A \times B \times C$

3. $A \times \Omega = A$

    $A + \Omega = \Omega$

    $A \times \empty = \empty$

    $A + \empty = A$

4. $A \times \overline{A} = \empty$
5. $A + \overline{A} = \Omega$
6. $A \times B \subset A \ (A \times B \subset B)$
7. $\overline{\overline{A}} = A$
8. $A \setminus B = A \times \overline{B}$
9. $\overline{A + B} = \overline{A} \times \overline{B}$
10. $\overline{A \times B} = \overline{A} + \overline{B}$
11. $(A + B) \times C = A \times C + B \times C$
12. $(A \setminus B) \times C = A \times C \setminus B \times C$

обощение свойств 9-11 на _счётное число_ множеств:

9. $(\overline{\sum_{i = 1}^{\infty} A_i}) = \prod_{i = 1}^{\infty} \overline{A_i}$
10. $\overline{(\prod_{i = 1}^{\infty} A_i)} = \sum_{i = 1}^{\infty} A_i$
11. $(\sum_{i = 1}^{\infty} A_i) \times B = \sum_{i = 1}^{\infty} A_i \times B$

**def** $\mathbb{A}$ называется алгеброй множеств, если:

1. $\Omega \in \mathbb{A}$
2. $] A \in \mathbb{A} \Rightarrow \overline{A} \in \mathbb{A}$
3. $] A \in \mathbb{A}, B \in \mathbb{A} \Rightarrow A \times B \in \mathbb{A}$

**stat** алгебра замкнута относительно действий в конечном числе

**доказательство** $A \times B = \overline{A + B}$, свойство 10

​	                         $A \setminus B = A \times \overline{B}$, свойство 8

**stat** $\Sigma$ - $\sigma$-алгебра множеств, если $\Sigma$ - алгебра и $\forall A_i \in \Sigma, i = 1, 2, ... \ \sum_{i = 1}^{\infty} A_i \in \Sigma$

#### дополнительные определения событий

1. $\forall A \in \Sigma$ определяется событием
2. $\Omega = D$ - достоверное событие
3. $A = \empty$ - невозможное событие
4. $\overline{A} = \Omega \setminus A$ - противоположное событие
5. A и B называются несовместимыми =, если $A \times B = \empty$

$] \ \Omega$ не более чем счётно

1. $p: \ \Omega \rightarrow [0, 1], \ p(\omega) \geqslant 0$
2. $\sum_{\omega \in \Omega} p(\omega) = 1$

$\forall A \in \Sigma: p(A) = \sum_{\omega \in A} p(\omega)$      ($\Sigma$ - множество всех подмножеств)

### примеры основных дискретных схем

1. Классическая (+ обобщение: геометрическая поверхность)
2. Геометрическая
3. Пуассона
4. Бернулли
5. Полиномиальная
6. Гипергеометрическая

## I. Классическая схема

$card(\Omega) = n$

$p(\omega ) = ^{\omega \in \Omega} \frac{1}{n}$, p - вероятностная мера

$p(A) = \frac{card(A)}{card(\Omega)}$

1. $p(\omega) \geqslant 0$
2. $\sum_{\omega \in \Omega} p(\omega) = \frac{1}{n} \sum_{\omega \in \Omega} 1_\omega$

$\Omega$ - измерима по Лебегу

$\forall A \subset \Omega: \ p(A) = \frac{\mu(A)}{\mu(\Omega)}$

## II. Геометрическая схема

$\Omega = \{A, \overline{A} A, \overline{A} \overline{A} A, ... \}$

имеется эксперимет с двумя исходами

$\forall p \in (0, 1) p(A) = p, p(\overline{A}) = 1 - p = q$

$p(\overline{A} ... \overline{A} A) = q^k p$

#### свойства вероятностной меры (дискр.)

 1. $p(B) = ^{B \in \Sigma} q^k p, k = 0, 1, 2, ...$

    $p(B) > 0$

2. $\sum_{B \in \Omega} p(B) = \sum_{k = 0}^{\infty} q^k p = p \frac{1}{1 - q} = 1$

---

## III. Схема Бернулли

Серия из "n" испытаний с двумя исходами "А" - успех, "$\overline{A}$" - неудача

$p \in (0, 1), p(A) = p, p(\overline{A}) = 1 - p = q$
$$
] C_i =
	\left \{
		\begin{array}{ll}
			A, success \  in \  i-th \\
			\overline{A}, fail -//-
		\end{array}
	\right.
$$

$\omega$ - исход всей серии: $\Omega = \{\omega \}$ 

$\omega = C_1 C_2 C_3 ... C_n$

] k($\omega$) - количество успехов в элементарных исходах $\omega$

$p(\omega) = (def) \ p^{k(\omega)} q^{n - k}(\omega)$

$B_{n,m,p} = \{ \omega \in \Omega (result \ n -), k(\omega) = m \}$

$p(B_{n,m,p}) = \sum_{\omega \in B_{n,m,p}} p(\omega) = p^m q^{n - m} |B_{n,m,p}| = C^m_np^,q^{n-m}$

$\{ B_{n,m,p}, P(B_{n,m,p}) \}$ def схема Бернулли

Проверка корректности определения

1. $p(\omega)=p^{k(\omega)}q^{n-k(\omega)} > 0$
2. $\sum_{\omega \in \Omega} = \sum^n_{m = 0} \sum_{\omega \in B_{n,m,p}} p(\omega) = \sum_{m = 0}^n C^m_n p^mq^{n-m}=(p+q)^n =1$

## IV. Схема Пуассона

$\Omega = \{\omega_0 = 0, \omega_1 = 1, ..., \omega_n = n, ... \}$, фикс $\lambda > 0$

$p(\omega_n) = ^{def} \frac{\lambda^n}{n!}e^{-\lambda}$

Проверка корректности определения

1. $p(\omega_n) = \frac{\lambda^n}{n!} e^{-\lambda} > 0$
2. $\sum^{\infty}_{n = 0} p(\omega_n) =e^(-\lambda) \sum^\infty_{n = 0} \frac{\lambda^n}{n!} = e^\lambda e^{-\lambda} = 1$

## V. Полиномиальная схема 

Пусть имеется последовательность независимых однотипных опытов в результате любого опыта может произойти одно из событий $A_1 .. A_k$

с вероятностями $p_i \geqslant 0, i = 1..k$

$\sum_{i = 1}^m p_i = 1$

Общее число объектов "n" и рассматриваем событие 

$B_{n,m_1,...,m_k,p_1,...,p_k}$

$m_i \geqslant 0 \sum^k_{i = 1} m_i = n$

$p(B_{n,m,...,m_k}) =p_1^{m_1}p_2^{m_2}...p_k^{m_k} |B_{n,m,...,m_k}| = p^{m_1}_1 p_2^{m_2}...p_k^{m_k} \frac{n!}{m!...m_k!}$

## VI. Гипергеометрическая схема

Пусть в урне имеется n однотипных предметов, при чём

$n_1 \geqslant 0, n_1$ - с признаком 1, $n_2 \geqslant 0, n_2$ - с признаком 2, $n_1 + n_2 = n$ $\Rightarrow$ случайных известных "k" предметов

] $B_{n,n_1,k,k_1} = B_{n,n_1}(k,k_1)$
$k_1$ - 1-ого типа
$k_2 = k - k_1$ - 2-ого типа
] $\omega - \forall$ извлечь $\Omega = \{\omega \}$
$\Rightarrow |\Omega| = C^k_n$
$P(B_{n,n_1} (k, k_1)) = \frac{|B_{n,n_1} (k, k_1)|}{C^k_n} = \frac{C^{k_1}_{n_1} C^{k_2}_{n_2}}{C^k_n}$
$\{B_{n,n_1} (k, k_1), P(B_{n,n_1} (k, k_1)) \}$
1. $p(B_{n,n_1} (k, k_1)) \geqslant 0$
2. $\sum_{\omega \in \Omega} p(\omega) = \sum^k_{k_1 = 0} \frac{C^{k_1}_{n_1} C^{k_2}_{n_2}}{C^k_n}$

## Общая вероятностная схема
] $(\Omega, \Sigma)$ - измеримое пространство
$\Sigma$ - выделенная $\sigma$-алгебра
$p = p(A): \Sigma \rightarrow ^p [0,1] def$ называется **вероятностной мерой**, если для неё выполнено три аксиомы Колмагорова

### Аксиомы Колмогорова

1. $P(\Omega) = 1$
2. $P(A) \geqslant 0, \forall A \in \Sigma$
3. $P(\sum^\infty_{i = 1} A_i) = \sum^\infty_{i = 1} (A_i)$, если $A_i \in \Sigma, i = 1,2,..., A_i, A_j = ^{i \ne j} \empty$

**stat** дискретная схема есть частный случай общей схемы $(\Omega, \Sigma, p)$

> Доказательство:
>
> 1. $p(\Omega) = \sum_{\omega \in \Omega} p(\omega) = 1$
>
> 2. $p(A) = \sum_{\omega \in A} p(\omega) \geqslant 0$
>
> 3. ] $\{A_i \}^\infty_{i = 1}, A_i \in \Sigma$
>
>     $A_i A_j = \empty$
>
>     $\sum^\infty_{i = 1} A_i \subseteq \Omega$
>
>     $ 1 \geqslant p(\sum^\infty_{i = 1} A_i) = \sum_{\omega \in \sum^\infty_{i = 1} A_i \subseteq \Omega}\ p(\omega) = \sum_i \sum_{\omega \in A_i p(\omega)}$
> $\square$

### Аксиомы непрерывности и счётной аддитивности

#### две аксиомы непрерывноси

1. **аксиома** / *аксиома непрерывности* /

    ] $(\Omega, \Sigma, P)$ - вероятностное пространство

    и $B_1 \supseteq B_2 \supseteq B_3 \supseteq ...$

    $B_n, n = 1,2,3, ...; B_n \in \Sigma$

    $B = \cap^\infty_{n = 1} B_n = ^{def} \lim_{n \to \infty} B_n, B \in \sum$

    $P(B) = p(\lim_{n \to \infty} B_n) = \lim_{n \to \infty} p(B_n)$

2. **аксиома** / *аксиома непрерывности* /

    ] $\{A_i \}^\infty_{i = 1} A_i \in \Sigma$
    $A_1 \subseteq A_2 \subseteq A_3 \subseteq ...$

    $A = \cup^\infty_{i = 1} A_i = ^{def} \lim_{i \to \infty} A_i, A \in \Sigma$

    $p(A) = p(\lim_{i \to \infty} A_i) = \lim_{i \to \infty} P(A_i)$

**stat** аксиома непрерывности *эквивалентны*

> Доказательство:
>
> ] $B_1 \supseteq B_2 \supseteq B_3 \supseteq ...$ - убывающая последовательность множеств
>
> тогда $\{A_i \}^\infty_{i = 1} = \{A_i: A_i = \Omega - B_i \}_i$
>
> и ] справедлива 1 аксиома непрерывности
>
> $B = \cap^\infty_{n = 1} B_n = \cap^\infty_{n = 1} (\Omega \setminus A_n) = \Omega - \cup^\infty_{n - 1} A_n = \Omega \setminus A$
>
> $p(B) = p(\cap^\infty_{n = 1} B_n) = ^{ 1 \ ax} \lim_{i \to \infty} p(B_n) = lim_{n \to \infty} p(\Omega \setminus A_n) = p(\Omega \setminus A) = 1 - P(A) = p(\cup_n A-n)$
>
> т.е. $p(\lim_{n \to \infty} A_n) = p(A)$
>
> $\square$