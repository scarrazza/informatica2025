# 💻 Laboratorio di Informatica 7

### Prof. Stefano Carrazza - Corso C

**Obiettivo:** Pratica intensiva su concetti fondamentali del C++: puntatori, gestione dinamica della memoria, definizione di funzioni e implementazione di algoritmi di base (ordinamento, analisi di array, integrazione numerica e algebra lineare).

Prima di iniziare, si consiglia vivamente di organizzare il lavoro creando una cartella dedicata e un `Makefile` per una compilazione efficiente di tutti gli esercizi.

```bash
cd ~              # Vai alla home directory
mkdir lezione7    # Crea la directory per la lezione
cd lezione7       # Entra nella cartella
```

Successivamente, crea un `makefile` con le istruzioni di compilazione adatte per tutti gli esercizi.

-----

### 🎯 Esercizio 1 - Fondamenti sui Puntatori

Scrivere un programma in C++ per esplorare l'uso dei puntatori e la gestione della memoria.

1.  Creare una variabile `x` di tipo `double` inizializzata a `5.5` e un puntatore `p` di tipo `double*` inizializzato a `NULL`.

2.  Stampare su terminale:

      * Il **valore** della variabile `x`.
      * L'**indirizzo di memoria** della variabile `x` (usando l'operatore `&`).
      * L'**indirizzo puntato** da `p` (il suo contenuto).
      * L'**indirizzo di memoria** del puntatore `p` stesso.

3.  Assegnare al puntatore `p` l'indirizzo della variabile `x` (`p = &x`). Successivamente, stampare:

      * L'indirizzo ora puntato da `p`.
      * Il **valore** salvato all'indirizzo puntato da `p` (usando l'operatore di dereferenziazione `*`).

4.  Chiedere all'utente di inserire un numero di tipo `double` da terminale e assegnare questo valore a ciò che è puntato da `p` (`*p = ...`). Verificare e stampare che il valore di `x` sia stato modificato.

5.  **Gestione Dinamica:**

      * Creare un array dinamico di tipo `double` di dimensione 10 (usando `new[]`).
      * Stampare l'indirizzo di memoria di tutte le componenti dell'array (usando aritmetica dei puntatori o l'operatore `&`).
      * **Verifica:** Controllare che la distanza (in byte) tra gli indirizzi delle componenti adiacenti sia pari alla dimensione in byte del tipo `double` (ottenibile con `sizeof(double)`).
      * **Importante:** Ricordarsi di eliminare l'array dinamico prima della fine del `main` (usando `delete[]`).

-----

### ⚙️ Esercizio 2 - Funzioni e Analisi di Array

Scrivere un programma in C++ che utilizza diverse funzioni per l'analisi e la manipolazione di un array.

1.  Creare un array su stack: `int v[10] = {9, 2, 1, 3, 4, 7, 0, 11, 20, 5};`.

2.  Scrivere una funzione `print_array` di tipo `void` che accetta un array di interi e la sua dimensione. La funzione deve stampare il contenuto dell'array. Testarla con l'array `v` nel `main`.

3.  Scrivere una funzione `max_array` di tipo `int` che restituisce il valore massimo presente nell'array in input. Testarla e stampare il risultato nel `main`.

4.  Scrivere una funzione `min_array` di tipo `int` che restituisce il valore minimo presente nell'array in input. Testarla e stampare il risultato nel `main`.

5.  **Passaggio per Riferimento:** Scrivere una funzione `min_max_array` di tipo `void` che calcola e restituisce il valore massimo e minimo dell'array tramite due argomenti (`min` e `max`) passati alla funzione **per riferimento**.

6.  **Ordinamento:** Scrivere una funzione `sort_array` di tipo `void` che ordina l'array di interi in modo crescente utilizzando l'algoritmo **Selection Sort**. Testare la funzione sull'array `v` e stampare il contenuto ordinato utilizzando `print_array`.

-----

### 📐 Esercizio 3 - Integrazione Numerica

Scrivere un programma in C++ per calcolare l'integrale definito di una funzione analitica (la funzione Gaussiana) utilizzando la **Regola dei Trapezi**.

La formula della Regola dei Trapezi è:

```math
\int_a^b f(x) \, dx \approx d \cdot \sum_{i=0}^{n-1} \frac{f(a + i \cdot d) + f(a + (i + 1) \cdot d)}{2}
```
dove l'ampiezza di ogni intervallo è data da $d = \frac{b-a}{n}$ e $n$ è il numero di *steps*.

1.  **Funzione Gaussiana:** Implementare una funzione `gauss` di tipo `double` che accetta $x$ come argomento e restituisce il valore di una Funzione Gaussiana normalizzata, centrata in $\mu=0$ e con deviazione standard $\sigma=1$:

```math
\text{gauss}(x) = \frac{1}{\sqrt{2\pi}} \cdot e^{-x^2/2}
```
**Suggerimento:** includere l'header `<cmath>` per `sqrt`, `exp` e per la costante $\pi$ (spesso disponibile come `M_PI` se sono attivate estensioni POSIX o si definisce l'header `_USE_MATH_DEFINES` prima di includere `<cmath>`).

2.  **Integrazione:** Implementare una funzione `integrate_gaussian` di tipo `double` che prende come argomenti i limiti di integrazione `a` e `b`, e il numero di *steps* `n`. La funzione deve calcolare e restituire l'integrale numerico della funzione `gauss` tra $a$ e $b$ utilizzando la formula dei trapezi.

3.  **Test:** Testare la funzione `integrate_gaussian` sulle seguenti configurazioni, facendo variare il numero di steps `n`:

    | Limiti $(a, b)$ | Steps $n$ |
    | :---: | :---: |
    | $(-10, 10)$ | $10, 100$ |
    | $(-1, 1)$ | $10, 100$ |

    Stampare i risultati per mostrare come la precisione cambi al variare di $n$.

-----

### ⏺️ Esercizio 4 - Discriminatore di Punti nel Cerchio

Scrivere un programma in C++ che determina se un punto con coordinate cartesiane $(x,y)$ si trova all'interno di un cerchio dato.

**Cerchio di Riferimento:** Centro $C=(1, 1)$, Raggio $R=1$.

1.  Creare variabili di tipo `const double` per salvare le proprietà del cerchio: `x_c`, `y_c`, `r`.

2.  **Distanza Euclidea:** Costruire una funzione `distanza` di tipo `double` che calcola la distanza tra un punto generico $(x, y)$ e il centro del cerchio $(x_c, y_c)$.

      * Passare come argomenti le quattro coordinate.
      * **Suggerimento:** Utilizzare il Teorema di Pitagora, dove i cateti sono le differenze in ascissa e ordinata. La formula è:
```math
\text{distanza} = \sqrt{(x - x_c)^2 + (y - y_c)^2}
```

3.  **Verifica del Cerchio:** Implementare una funzione `check_circle` di tipo `void` che prende come argomenti le coordinate $(x, y)$, il centro $(x_c, y_c)$, il raggio $r$, e una variabile `status` di tipo `bool` **passata per riferimento**.

      * All'interno della funzione, chiamare `distanza`.
      * Se la distanza è minore o uguale al raggio, assegnare `true` a `status`; altrimenti, assegnare `false`.

4.  **Ciclo Interattivo:** Implementare un ciclo infinito in cui:

      * Vengono chieste e introdotte da terminale coppie di coordinate $(x,y)$.
      * Viene applicato il discriminatore chiamando `check_circle`.
      * Viene stampato il risultato (`true` o `false`).

5.  **Test:** Verificare manualmente l'output del programma per le seguenti coppie di punti:

    | $(x, y)$ | Risultato Atteso |
    | :---: | :---: |
    | $(1.1, 0.7)$ | `true` |
    | $(2.1, 0.7)$ | `false` |
    | $(0.5, 0.3)$ | `true` |
    | $(1.0, 1.0)$ | `true` |
    | $(0.1, 0.1)$ | `false` |

-----

### 📈 Esercizio 5 - Algebra Lineare e Matrici

Scrivere un programma in C++ per eseguire operazioni di algebra lineare su vettori e matrici.

1.  Creare due vettori (array 1D) di tipo `double` e dimensione 5:

      * $V = \{1, 2, 3, 4, 5\}$
      * $W = \{10, 2, 4, 3, 2\}$

      Creare una matrice (array 2D) $M$ di tipo `double` e dimensione $3 \times 3$:
```math
M = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{pmatrix}
```

3.  **Prodotto Scalare:** Implementare una funzione `scalar` di tipo `double` che accetta due array 1D e la loro dimensione, e restituisce il prodotto scalare tra di essi ($\sum V_i \cdot W_i$). Testare la funzione con $V$ e $W$ e stampare il risultato.

4.  **Norma di un Vettore:** Implementare una funzione `norm` di tipo `double` che accetta un array 1D e la sua dimensione. La funzione deve calcolare la norma euclidea del vettore ($||V|| = \sqrt{V \cdot V}$) **riutilizzando** la funzione `scalar` per calcolare il prodotto scalare $V \cdot V$. Testare l'implementazione con $V$ e stampare il risultato.

5.  **Scambio per Riferimento:** Implementare una funzione `scambia` di tipo `void` che prende i valori di due oggetti e li scambia utilizzando il **passaggio per riferimento** (o un puntatore).

      * **Matrice Trasposta:** Applicare questa funzione alla matrice $M$ per calcolare la sua **matrice trasposta** ($M^T$), scambiando gli elementi $M_{i,j}$ con $M_{j,i}$.
      * Stampare il risultato della matrice trasposta su terminale.

-----

### 🧠 Esercizi Opzionali per l'approfondimento

Questi esercizi sono consigliati per coloro che hanno completato i precedenti e desiderano esplorare concetti più avanzati.

1. **Puntatori a Funzione**

   Modificare l'**Esercizio 3** per renderlo generico.

   -  Ridefinire la funzione `integrate_function` in modo che prenda come primo argomento un **puntatore a funzione** di tipo `double (*)(double)`, oltre ai limiti `a`, `b` e gli *steps* `n`.
   -  Testare la nuova funzione `integrate_function` passandole come argomento la funzione `gauss`.
   -  Testare la stessa funzione `integrate_function` con una semplice funzione polinomiale, ad esempio $f(x) = x^2$.

2. **Algoritmo di Ricerca Binaria**

   - Scrivere una funzione `binary_search` di tipo `bool` che implementa l'algoritmo di **Ricerca Binaria** (o *Binary Search*).
   - La funzione deve accettare un array **ordinato**, la sua dimensione e il valore da cercare.
   - La ricerca binaria funziona solo su array ordinati. Utilizzare l'array `v` già ordinato nell'**Esercizio 2.6** e testare la funzione cercando un valore presente (es. `11`) e uno non presente (es. `100`).

3. **Matrice di Correlazione**

   -  Scrivere una funzione `mean` di tipo `double` che calcola la media aritmetica di un array 1D.
   -  Scrivere una funzione `covariance` di tipo `double` che calcola la covarianza tra due vettori $V$ e $W$ (assumendo che abbiano media nulla per semplicità, oppure calcolandola internamente).
```math
\text{Cov}(V, W) = \frac{1}{N-1} \sum_{i=1}^N (V_i - \bar{V})(W_i - \bar{W})
```
   dove $\bar{V}$ è la media di $V$.

   -  Implementare una funzione `correlation_matrix` che, data una matrice di dati $D$ di dimensione $N \times P$ (dove $N$ sono le osservazioni e $P$ le variabili), calcoli e stampi la sua matrice di correlazione $P \times P$.
