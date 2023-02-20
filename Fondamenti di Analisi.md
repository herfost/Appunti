---
tag: note
type: analisi
---
# Primitiva
Una funzione $F(x)$ si dice primitiva (o antiderivata) della funzione $f(x)$ se:
$$F'(x) = f(x)$$
# Integrale indefinito
Insieme di tutte le primitive di una data funzione $f(x)$ in un dato intervallo chiuso $[a, b]$:
$$\int f(x)dx = F(x) + c$$ $\int$: simbolo di integrazione.
$f(x)$: funzione integranda.
$dx$: differenzia, $x$ variabile di integrazione.
$F(x) + c$: integrale indefinito

Ponendo $c = 0$ si ottiene la __primitiva fondamentale__:
$$\int f(x)dx = F(x)$$
# Proprietà 
## Addizione
$$\int [f(x) \pm g(x)]dx =\int f(x)dx \pm \int g(x)dx$$
## Moltiplicazione
$$\int kf(x) = k\int f(x)$$
con $k$ costante
## Composta
$$\int f \circ g  g'dx = F \circ g + c$$

# Somma integrale
Data una funzione $f(x$) l'area $A$ compresa tra il grafico della funzione $f(x)$ e l'asse delle $x$ si approssima mediante la somma di $n$ aree di rettangoli $(A_0, A_1, ..., A_{n-1})$ dove l'area $A_i = f(x_i)\Delta{x_i}$ 
$$
\sum_{i = 0}^{n}f(x_i)\Delta{x_i}
$$
> [!IMPORTANT] L'IDEA
La somma integrale di una funzione $f(x)$ consiste nella somma di $n$ sotto aree rettangolari $A$ 

# Area integrale
Ponendo la dimensione delle sotto aree $\Delta{x}$ a valori infinitesimi si aumenta la precisione della somma: 
$$ \lim_{h \to 0}\sum_{i = 0}^{n}f(x_i)h$$
![[Riemann_Sum.gif]]

> [!IMPORTANT] L'IDEA
L'area integrale di una funzione $f(x)$ consiste nella [[#Somma integrale]] di $f(x)$ in cui le sotto aree $\Delta{x}$ sono valori infinitesimali

# Integrale definito 
Sia $I$ un intervallo chiuso $[a,b]$, sia $f(x)$ una funzione continua in $I$, l'integrale definito della funzione $f(x)$ nell'intervallo $I$ rappresenta l'area $A$ compresa tra il grafico della funzione $f(x)$, l'asse delle $x$ e le rette verticali $x = a$, $x = b$.

$$\lim_{h \to 0}\sum_{a}^{b}f(x_i)h = \int_{a}^{b}{f(x)dx} = F(b) - F(a)$$
---
[Template :: [[AnalisiT]]]  
[Date :: ]