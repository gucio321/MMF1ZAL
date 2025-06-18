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

Dla $\left|z\right| < \left|a\right|$ jest to $\frac{1}{a} \sum_{n=0}^{\infty} \left(\frac{- z}{a}\right)^n$,
natomiast dla $\left|z\right| > \left|a\right|$ jest to $-\frac{1}{z} \sum_{n=0}^{\infty} \left(\frac{-a}{z}\right)^n$.

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
