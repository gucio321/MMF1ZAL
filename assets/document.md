# Zadanie 1

Mamy dwuwymiarowy piekarnik - płaszczyznę.

Niech $T(x,y)$ opisuje temperaurę.
Znamy warunki początkowe:
- $T(x, 0) = 0$
- $T(x, d) = $T_0$

Przez $T_y$ oznaczmy temperaturę w punkcie $y_0$ ($T(x, y_0)$).

```{note}
Stałe:
- $T_0 = 453.15K$
- $d = 60cm$
- $y_0 = 40cm$
- $T_{min} = 347.15K$
```

## Rozwiązanie równaniem Laplace'a

```{admonition} Równanie Laplace'a
Powyższy problem można rozwiązać przy pomocy równania Laplace'a:

$$
\Delta T = 0
$$ (laplace)
```

Ponieważ problem jest de facto 1-wymiarowy (zakładamy że grzałki są szerokości piekarnika, więc temperatura zależy jedynie od y)
Laplace'ian sprowadza się do drugiej pochodnej względem $y$:

$$
\Delta T = 0 \\
\frac{d^2 T}{dy^2} = 0 \Rightarrow T(y) &= \iint dy = \\
&= A y + B
$$

Teraz można zaaplikować warunki początkowe:
- $T(y=0) = 0 \Rightarrow B = 0$
- $T(y=d) = T_0 \Rightarrow A d = T_0 \Rightarrow A = \frac{T_0}{d}$

Więc ostatecznie otrzymujemy $T(y) = \frac{T_0}{d} y$.

## Rozwiązanie przy pomocy transformacji konforemnej

Zakładamy $f(z) = e^{\frac{\pi z}{d}}$.

```{tip}
Można zweryfikować działanie tej funkcji dla następujących przypadków:
- dolna płaszczyzna piekarnika ($y = 0$)
niech $u = x + i*0$ wtedy $f(u) = e^{\frac{\pi x}{d}}$ co będzie odpowiadało wartością na dodatniej póosi rzeczywistej.
- górna płaszczyzna piekarnika ($y = d$)
niech $u = x + i*d$ wtedy $f(u) = e^{\frac{\pi x}{d}} e^{\pi i} = -e^{\frac{\pi x}{d}}$ co będzie odpowiadało wartością na ujemnej póosi rzeczywistej.
- Gdy $y \in [0, d]$, $f(u) pozostaje w górnej półpłaszczyźnie zespolonej, ponieważ $f(u) = e^{\frac{\pi x}{d}} e^{\gamma \pi i}$, dla $\gamma \in [0, 1]$
możemy wyliczyć $\Im f(u) = sin(\gamma \pi) e^{\frac{\pi x}{d}}$. Ta liczba jest zawsze większa bądź równa 0.
```

Widać, że $f(z)$ jest odwzorowaniem konforemnym $T(z)$ na płaszczyźnie zespolonej.

Należy dokonać transformacji odwrotnej $f(z)$, aby otrzymać funkcję $T(x,y)$.

$$
T(x, y) = A * Arg(f(z)) = \frac{T_0}{\pi} * \frac{\pi}{d} x = \frac{T_0}{d} x
$$

## Podsumowanie

Ostatecznie w obu metodach otrzymujemy to samo rozwiązanie:

$$
T(x,y) = \frac{T_0}{d} y
$$

Po podstawieniu wartości stałych mamy:

$$
T(x,y) = \frac{453.15}{60} y \frac{K}{cm} = 7.5525 y \frac{K}{cm}
$$

Wyliczając $T(x, y_0)$ otrzymujemy $T(x, 40) = 7.5525 * 40 = 302.1 K$ co niestety jest mniejsze niż $T_{min}$.

```{raw} latex
\newpage
```

```{admonition} Wniosek
Ciasto się nie upiekło.

![oh no](sad.png)
```

# Zadanie 2

## Wprowadzenie

Rozważamy pole elektrostatyczne pochodzące od 2 ładunków punktowych.
(dodatniego $q$ w $x=a$ i ujemnego $-q$ w $x=-a$). Pole to jest opisane następującą funkcją:

$$
f(z) = \frac{q}{2\pi \epsilon_0} \left( \frac{1}{z-a} - \frac{1}{z+a} \right)
$$ (opis-pola)

Szukamy jego rozwinięcia w szereg Laurenta w okolicy punktu $z_0=0$
dla 2 przypadków:

1. $\left|z\right| < a$
2. $\left|z\right| > a$

## Wstęp teoretyczny

Zdefiniujmy $\hat{L}$ jako operator rozwinięcia w szereg Laurenta.

$$
\hat{L}(f(z), z_0) = \sum_{n=-\infty}^{\infty} a_n (z-z_0)^n
$$

gdzie:

$$
a_n = \frac{1}{2\pi i} \oint_C \frac{f(z)}{(z-z_0)^{n+1}} dz
$$ (laurent-calka)

Jak widać, całka {eq}`laurent-calka` jest operacją liniową.
Z tego wynika, ze $\hat{L}$ również jest operatorem liniowym.

Dlatego możemy rozpatrywać {eq}`opsi-pola` jako sumę 2 niezależnych szeregów.

$$
\hat{L}(f(z), z_0) = \frac{q}{2\pi \epsilon_0} \left( \hat{L}\left(\frac{1}{z-a}, z_0\right) - \hat{L}\left(\frac{1}{z+a}, z_0\right) \right)
$$

## Pierwszy składnik

Rozważamy rozwinięcie funkcji $f(x) = \frac{1}{z-a}$ w okolicy $z_0 = 0$.

To rozwinięcie można przyróœnać do rozwinięcia szeregu geometrycznego. Jest ono równe
$-\frac{1}{a} \sum_{n=0}^{\infty} \left(\frac{z}{a}\right)^n$ dla $\left|z\right| < \left|a\right|$
oraz $\frac{1}{z} \sum_{n=0}^{\infty} \left(\frac{a}{z}\right)^n$ dla $\left|z\right| > \left|a\right|$ ([literatura 1.](#literatura)).

## Drugi składnik

Analogicznie, można dokonać rozwinięcia funkcji $\hat{L}\left(\frac{1}{z+a}, 0\right)$.

Dla $\left|z\right| < \left|a\right|$ jest to:

$$
\frac{1}{z+a} &= \frac{1}{a} \frac{1}{1 - \frac{-z}{a}} \\
&= \frac{1}{a} \sum_{n=0}^{\infty} \left(\frac{- z}{a}\right)^n
$$

natomiast dla $\left|z\right| > \left|a\right|$ analogicznie jest to $-\frac{1}{z} \sum_{n=0}^{\infty} \left(\frac{-a}{z}\right)^n$.

## Podsumowanie

Po zsumowaniu obu składników otrzymujemy:

$$
f(z) \cong \frac{q}{2\pi\epsilon_0}\left\lbrace\begin{matrix}
-\frac{1}{a} \sum_{n=0}^{\infty} \left(\frac{z}{a}\right)^n - \frac{1}{a} \sum_{n=0}^{\infty} \left(\frac{- z}{a}\right)^n, & \left|z\right| < a \\
\frac{1}{z} \sum_{n=0}^{\infty} \left(\frac{a}{z}\right)^n + \frac{1}{z} \sum_{n=0}^{\infty} \left(\frac{-a}{z}\right)^n, & \left|z\right| > a
\end{matrix}\right.
$$

# Literatura

1. _Laurent Series_ - [https://en.wikipedia.org/wiki/Laurent_series](https://en.wikipedia.org/wiki/Laurent_series) dostęp 18.06.2025 20:51
