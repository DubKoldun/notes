# Translation Methods

> Лабораторные:
>
> 1. perl
>2. Ручное построение трансляторов
> 3. Использование автоматических генераторов трансляторов
> **e.g.** ANTLR (java), Bison + Yacc (c++), Happy (haskell)
> 4. Написание автоматического генератора транслятора
>    
>    1 - pcms, 2-4 - защита

$\Sigma, \Sigma^*, L \subset \Sigma^*$ - формальный язык

Базовый класс формальных языков - регулярные (= автоматные). Для порождения - регулярные выражния, для распозования - конечные автоматы

Контекстно-свободные языки: КС грамматики / МП автоматы

**токены (лексемы)** - единые неделимые элементы языка ($\in \Sigma$)

## Лексический анализ

Первый этап любого разбора - *лексический анализ*

Последовательность символов -> последовательность токенов ($\in \Sigma^*$)

>  **e.g.** арифмитические выражения
>  
>  $\Sigma = \{n,+,\times,\ (,\ ) \}$
>  
>  $(2 \ + \ 2) \times 2 \rightarrow  (n + n) \times n$
>  
>  $n : (0|1|...|9)(0|1|...|9)^*$

*жадный лексический анализ на базе регулярных выражений*: пропускем пробельные символы, смотрим первый непробельный, находим максимальный префикс какого-то возможного токена

---

1. Проверить, что строка выводится в грамматике $\Gamma$ // алгоритм КЯК $\Omicron(n^3)$

2. Построить дерево разбора

3. Синтаксически управляемая трансляция

    >  $E \rightarrow T \\ E \rightarrow E \ + \ T \\ T \rightarrow F \\ T \rightarrow T \ \times \ F \\ F \rightarrow n \\ F \rightarrow (E)$
    
    **Аттрибуто транслирующие грамматики** - КСГ с добавлением двух элементов: аттрибуты и транслирующие символы

    **транслирующие символы** - фрагменты кода, которые вставляем в грамматику, которые могут взаимодействовать с аттрибутами
    
    >$E \rightarrow E \ + \ T \ \{E_{0}.v = E_{1}.v \ +\ T.v \}$
    >
    >$T \rightarrow T \ \times \ F \ \{T_{0}.v = T_{1}.v \ +\ F.v \}$



Нужно быстрее, чем за куб => накладываем ограничения на грамматики

**Однозначность** - если у любого слова не более одного дерева разбора в этой грамматике  // Модификация алгоритма Эрли - $\Omicron(n^2)$

**LL, LR** - грамматики, на которые наложены дополнительные ограничения, чтобы разбор работал за линейное время



$\Gamma, \ w$ на вход

Можем строить дерево разбора сверзу вниз - **нисходящая трансляция**. Шаг называется *раскрытие нетерминала*

Снизу вверх - **восходящий разбор**. Шаг - *свёртка*

## Метод нисходящих трансляций для LL грамматик

s - стартовый нетерминал, w - слово, префикс которого разобран (x, y left)

**LL(k) - грамматика** - если достаточно посмотреть на первые k символов y, чтобы понять, какое правило применить для нетерминала A

Грамматика $\Gamma$ называется **LL(1) грамматикой**, если $s \Rightarrow^* xA\xi \Rightarrow x \alpha \xi \Rightarrow^* xc\eta \\ s \Rightarrow^* xA\tau \Rightarrow x\beta\sigma \Rightarrow^*xc\zeta \\ \alpha = \beta$

---

**def** *FIRST*: $(N \cup \Sigma)^* \rightarrow 2^{\Sigma \cup \{\epsilon\}}$ 
    $c \in FIRST(\alpha) \Leftrightarrow \alpha \Rightarrow^* cx \\ e \in FIRST(\alpha) \Leftrightarrow \alpha\Rightarrow^* \epsilon $

> **e.g.** $S \rightarrow SS \\ S \rightarrow (S) \\ S \rightarrow \epsilon$ 
>
> $FIRST(S) = \{c, \epsilon\}$
>
> $FIRST('S)') = \{(,)\}$
>
> $FIRST(\epsilon) = \{\epsilon\}$
>
> $FIRST('))((') = \{')'\}$

## Алгортим удаления бесполезных символов

1. Удалить непорождающие символы
2. Удалить недостижимые

### Удаление непорождающих символов

1. Множество непорождающих символов $Gen = \empty$

    do {

    ​    for A $\rightarrow \alpha$

    ​        if $\alpha \in (\Sigma \cup Gen)^*$:

    ​            Gen $\cup=$ A

    } while Gen change

    NonGen = N $\setminus$ Gen

    
    
    A - порождающий, но Алгоритм 1 выбрал как порождающий
    
    $A \Rightarrow \alpha \Rightarrow^{k - 1} x$

#### Лемма о рекурсивном вычислении FIRST

$\alpha = c\beta$

$FIRST(\alpha) = \{c\}$

$\alpha = A\beta$

$FIRST(\alpha) = (FIRST(A)) \setminus \epsilon) \cup (FIRST(\beta)\ if\ \epsilon \in FIRST(A))$

$FIRST(\epsilon) = \{\epsilon\}$

### Алгоритм 

FIRST: map<N, set<$\Sigma \cup \epsilon$>>

function getFIRST($\alpha$)

​    if $\alpha = \epsilon$ return $\{\epsilon\}$

​    if $\alpha[i] \in \Sigma$ return $\{\alpha[i]\}$

​    // $\alpha[0] \in N$

​    return $(FIRST[ \alpha[0]] \setminus \epsilon) \cup (getFIRST(\alpha[1:]), if \ \epsilon \in FIRST[\alpha[0]])$

#### Алгоритм построения FIRST

do {

​    for A $\rightarrow \alpha$:

​        FIRST[A] $\cup = getFIRST(\alpha)$

} while FIRST changes

**def** *FOLLOW*: $N \rightarrow 2^{\Sigma \cup \{\$\}}$

​    $c \in FOLLOW(A) \Leftrightarrow S \Rightarrow^* \alpha A c \beta$

​    $\$ \in FOLLOW(A) \Leftrightarrow S \Rightarrow^* \alpha A$

### Алгоритм FOLLOW

FOLLOW: map<N, set<$\Sigma \cup \$$>>

FOLLOW(S) = {$}

do {

​    for A $\rightarrow \alpha$

​        for B in $\alpha$

​            let $\alpha = \xi B \eta$

​            FOLLOW(B) = FIRST($\eta) \setminus \epsilon$

​            if $\epsilon \in FIRST(\eta)$

​                FOLLOW(B) $\cup =$ FOLLOW(A)

} while FOLLOW changes

## Теорема

$\Gamma$ является LL(1) $\Leftrightarrow$ $\forall A \rightarrow \alpha, A \rightarrow \beta$:

1. $FIRST(\alpha) \cap FIRST(\beta) = \empty$
2. $\epsilon \in FIRST(\alpha) \Rightarrow FIRST(\beta) \cap FOLLOW(A) = \empty$

>  Доказательство:
>
>  $\Rightarrow$) от противного:
>
>  ​    ] не (1) 
>
>    1. $\exists A \rightarrow \alpha, A \rightarrow \beta, c \in FIRST(\alpha) \cap FIRST(\beta)$
>
>  ​      $S \Rightarrow^* xA\sigma \Rightarrow x \alpha \sigma \Rightarrow^* xc\xi\sigma$
>
>  ​      $S \Rightarrow^* xA\sigma \Rightarrow x \beta \sigma \Rightarrow^* xc\eta\sigma$
>
>  ​    2. $\epsilon \in FIRST(\alpha) \cap FIRST(\beta)$
>
>  ​       $S \Rightarrow^* xA\sigma \Rightarrow x \alpha \sigma \Rightarrow^* x\sigma \Rightarrow xc\tau$
>
>  ​        $S \Rightarrow^* xA\sigma \Rightarrow x \beta \sigma \Rightarrow^* x\sigma \Rightarrow xc\tau$
>
>  ​    ] не (2)
>
>  ​    ...

