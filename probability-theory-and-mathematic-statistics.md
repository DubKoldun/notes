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

9. $(\sum_{i = 1}^{\infty} A_i) = \prod_{i = 1}^{\infty} A_i$
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

