---
tag: note
type: precalculus
---
# Rapporto Incrementale

Il rapporto incrementale di una funzione $f$ equivale il rapporto tra la variazione delle coordinate $\Delta y$ e la variazione delle ascisse $\Delta x$.
Rapporto incrementale = $\frac{\Delta y}{\Delta x}$. Si rinomina ora $\Delta x$ con $h$ e si osserva che $\Delta y = f(x_0 + h) - f(x_0)$. Il rapporto incrementale si può allora scrivere come:
$$\frac{\Delta{y}}{\Delta{x}} = \frac{f(x_0 + h) - f(x_0)}{h}$$

> [!IMPORTANT]
Il rapporto incrementale rappresenta il coefficente angolare $m$ di una retta $r$ secante al grafico della funzione $f : D$ in due punti $a$, $b \in D$

# Derivata prima
Una funzione di equazione $y = f(x)$, definita in un intorno (completo) di $x_0$, si dice derivabile in $x_0$ se: 


$$\lim_{h \to 0}\frac{f(x_0 + h) - f(x_0)}{h} = l$$

esiste finito. 

> [!IMPORTANT]
La derivata prima $f'$ indica il tasso di cambiamento della funzione $f$ al variare del suo argomento $x$. Corrisponde al coefficente angolare $m$ (tangente) delle retta $y = mx + q$ passante per il grafico della funzione $f$ nel punto $x$.

# Teorema di Fermat
Sia $f$ una funzione definita in un intervallo chiuso $[a, b]$ e sia $c \in [a, b]$ in cui $f$ derivabile. Se $f(c)$ equivale un punto di _estremo relativo_, la derivata $f'$ si annulla nel punto $c$ ($f'(c) = 0$).

1. $f : [a, b]$
2. $c \in (a, b)$
3. se $f(c) =$ _estremo relativo_ | $f'(c) = 0$

> [!IMPORTANT]
Se la funzione $f$ nel punto $c$ equivale un punto di estremo relativo, $c$ è un _punto stazionario_

# Teorema di Cauchy 
Siano $f$ e $g$ due funzioni **continue** in un intervallo chiuso $I = [a, b]$ derivabile nell'intervallo aperto $(a, b)$. Esiste un punto $c \in (a, b)$ che soddisfa la condizione sottostante:

1. $f : [a, b]$
2. $c \in (a, b)$
3. $$\frac{f'(c)}{g'(c)} = \frac{f(b) - f(a)}{g(b) - g(a)}$$
# Teorema di Rolle
Sia $f$ una funzione che soddisfa le seguenti ipotesi:

1. $f$ continua nell'intervallo chiuso $[a, b]$
2. $f$ derivabile nell'intervallo aperto $(a, b)$
3. $f(a) = f(b)$

Allora esiste $c \in (a, b) \rightarrow f'(c) = 0$

> [!IMPORTANT]
Se una funzione $f$ continua in un intervallo chiuso $[a, b]$, derivabile nell'intervallo aperto $(a, b)$, assume nel punto $a$ lo stesso valore assunto nel punto $b$, la funzione presenta almeno un punto stazionario $c$ nell'intervallo aperto $(a, b)$

# Teorema di Lagrange 
Sia $f$ una funzione che soddisfa le seguenti condizioni:

1. $f$ continua nell'intervallo chiuso $[a, b]$
2. $f$ derivabile nell'intervallo aperto $(a, b)$

Allora esiste $c \in (a, b) \rightarrow f'(c) = \frac{f(b) - f(a)}{b - a}$  

> [!IMPORTANT]
Se una funzione $f$ è continua in un intervallo chiuso $[a, b]$ e derivabile nell'intervallo aperto $(a, b)$, la funzione presenta almeno un punto $c$ in cui la derivata equivale il rapporto tra la differenza delle coordinate della funzione e le ascissce nei punti $\{b, a\}$

---
# Teorema di de l'Hôpital
[Pagina Wikipedia](https://it.wikipedia.org/wiki/Regola_di_de_l%27H%C3%B4pital)
Siano $f$ e $g$ due funzioni derivabili in un interno $I$ di $x_0 \in \mathbb{R} - \{ x_0\}$ e siano verificate le seguenti ipotesi:

1. $\lim\limits_{x\to x_0}f(x) = \lim\limits_{x\to x_0}g(x) = \{0, \pm\infty\}$
2. $g'(x) \not= 0$ $\forall x \in I$, $x \not= x_0$
3. esiste $\lim\limits_{x\to x_0}\frac{f'(x)}{g'(x)}$

Allora  $\lim\limits_{x\to x_0}\frac{f(x)}{g(x)} = \lim\limits_{x\to x_0}\frac{f'(x)}{g'(x)}$

> [!IMPORTANT]
Le forme indeterminate dei limiti ($\frac{0}{0}$, $\frac{\infty}{\infty}$) possono essere risolte mediante l'impiego delle derivate, ovvero:
$$\frac{f(x)}{g(x)} = \frac{0}{0} \lor \frac{\infty}{\infty}$$ 
$$\frac{f(x)}{g(x)} = \frac{f'(x)}{g'(x)} = l$$

# Formula di Taylor
Siano $I \subset \mathbb{R}$ un intorno di $x_0 \in \mathbb{R}$ e $f : D \rightarrow \mathbb{R}$ una funzione derivabile $n-1$ volte in $I$ tale che esiste la derivata $n$-esima $f^{(n)}(x_0)$ allora:
$$T_n(f, x) = \sum_{k = 0}^{n}\frac{f^{(k)}(x_0)}{k!}(x - x_0)^k$$
$f(x) = T_n(f, x) + R_n(x)$ con $R_n(x)$ infinitesimo di ordine $(x - x_0)^n$ ovvero
$$\lim_{x\to x_0}\frac{R_n(x)}{(x - x_0)^n} = 0$$
### Resto di Peano
indica la dimensione dell'errore dell'apporsimazione:
$$R_n(x) = o((x-x_0)^n)$$

$$T_n(f, x) = \sum_{k = 0}^{n}\frac{f^{(k)}(x_0)}{k!}(x - x_0)^k + o((x-x_0)^k)$$
> [!IMPORTANT]
La formula di Taylor consente di approssimare una funzione $f$ con un polinomio $k$ arbitrario centrato in $x_0$

# Formula di McLaurin
Siano $I \subset \mathbb{R}$ un intorno di $x_0 \in \mathbb{R}$ e $f : D \rightarrow \mathbb{R}$ una funzione derivabile $n-1$ volte in $I$ tale che esiste la derivata $n$-esima $f^{(n)}(x_0)$ allora:
$$P_n(f, x) =  f(0) + \frac{f'(0)}{2!} + ... \frac{f^n(0)}{n!} = \sum_{k = 0}^{n}\frac{f^{(k)}(0)}{k!}x^k + o(x^k)$$
> [!IMPORTANT]
La formula di Taylor consente di approssimare una funzione $f$ con un polinomio $k$ arbitrario centrato in $0$

# Classificare punti stazionari
Si pone la derivata $f'$ della funzione $f$ pari a $0$ ossia:
$$f'(x) = 0$$
__Esempio__
$f(x) = x^4 - 2x^2 + 1$

1. Si ricava la derivata della funzione $f$:
$f'(x) = 4x^3 - 4x = 4x(x^2 - 1)$

2. Si trovano i punti stazionari della funzione ponendo $f'(x) = 0$:
$4x^3 - 4x = 4x(x^2 - 1) = 0$
$$
\begin{equation}
\begin{cases}
	x = 0\\
	x= \pm 1
\end{cases}
\end{equation}
$$
3. Si classificano i punti stazionari tramite lo studio del segno della derivata ponendo $f'(x) > 0$:
$4x^3 - 4x = 4x(x^2 - 1) > 0$
$$
\begin{equation}
\begin{cases}
	x > 0\\
	-1 < x < 1
\end{cases}
\end{equation}
$$

4. Si classificano i punti:

| Minimo Relativo | Massimo Relativo | Flesso a tangente orizzontale crescente | Flesso a tangente orizzontale decrescente |
| --------------- | ---------------- | --------------------------------------- | ----------------------------------------- |
| $---x_0+++$     | $+++x_0---$      | $+++x_0+++$                             | $---x_0---$                               |


$x = -1$ $\min$
$x = 0$ $\max$
$x = 1$ $\min$

# Classificazione punti di non derivabilità
$f(x)$ continua non derivabile in $x_0$: $f'(x) : D$, $x_0 \not\in D$.

__Esempio__
$f(x) = \sqrt[3]{x^2}$
1. Si ricava la derivata: $f'(x) = \frac{2}{3}x^{-\frac{1}{3}}$

2. Si trovano i punti di non derivabilità: $x \not\in D$
$x \not= 0$
3. Si calcolano i limiti dei punti di non derivabilità:
$\lim_\limits{x\to 0^+}f'(x) = +\infty$ 
$\lim_\limits{x\to 0^+}f'(x) = -\infty$

4. Si classifica il punto:

| Punto angoloso        | Cuspide                    | Flesso a tangente verticale |
| --------------------- | -------------------------- | --------------------------- |
| Limiti finiti diversi | Limiti non finiti discordi | Limiti non finiti concordi  |

$x = 0$ $cuspide$

# Retta tangente nel punto $x_0$
L'equazione della retta $y = mx + q$ riscritta come $y - y_0 = m(x - x_0)$ viene riscritta nuovamente mediante l'uso della dsterivata: $y' = m$ quindi $y - y_0 = y'(x - x_0)$.

__Esempio__
$y = f(x) = x^2 -3x + 2$ 
$x_0 = 3$

1. Si ricava il $y_0$ sostituendo la $x$ della funzione $f(x)$ con $x_0$:
$y_0 = f(x_0) = 3^2 - 3(3) + 2 = 2$

2. Si ricava il coefficiente angolare $m$ ovvero la derivate $y'$ e sostituendo la $x$ con $x_0$ :  
$y' = f'(x) = 2x - 3 = 2(x_0) - 3 = 2(3) - 3 = 3$

3. Si riscrive l'equazione della retta sostituendo i valori noti:
$y' = 2$
$x_0 = 3$ 

$y - y_0 = y'(x - x_0)$
$y - 2 = 3(x - 3)$

La retta tangente nel punto $x_0$ = $y = 3x + 7$

---

[Template :: [[../templates/PrecalculusT]]]  
[Date :: ]