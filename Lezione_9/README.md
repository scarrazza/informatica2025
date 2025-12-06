# 💻 Laboratorio di Informatica 9

### Prof. Stefano Carrazza - Corso C

**Riassunto:** Esercizi di base in C++: **caricamento dati**, strutture, puntatori e gestione della memoria.

Prima di iniziare suggeriamo di creare una cartella per questa lezione in cui potete salvare tutti i file che saranno creati per gli esercizi.

```bash
cd ~/           # ci porta alla home directory
mkdir lezione9  # crea la directory sulla vostra home
cd lezione9     # entrate dentro la cartella
```

Dopodiché creare un `makefile` con le istruzioni di compilazione per tutti gli esercizi.

-----

### 💾 Esercizio 1 - Data loading, funzioni e struct

Consideriamo un file di dati in cui vengono salvate le coordinate cartesiane $(x,y)$ di particelle cariche sotto un campo magnetico con sorgente centrata in origine.

1.  Definire una `struct point2d` in cui vengono salvati un puntatore `double *coordinate;` e una variabile `distance` di tipo `double` nel file header **`funzioni.h`**.

2.  Scaricare il file che contiene le coordinate $(x,y)$ per ogni particella con:

    ```bash
    wget https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_9/data1.dat
    # oppure (se macos)
    curl https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_9/data1.dat -o data1.dat
    ```

3.  Implementare un **array di struct `point2d`** chiamato `punti` di dimensione **1000** (*hint:* su stack). Implementare un ciclo in cui per ogni elemento `point2d` il puntatore `coordinate` viene inizializzato come un **array dinamico di dimensione 2**, dove il primo valore corrisponde alla $x$ e il secondo alla $y$ letti da file.

4.  Scrivere una funzione `compute_distance` di tipo `void` che prende come argomento 1 `point2d` e calcola la distanza rispetto alla sorgente usando il **teorema di Pitagora**. Definire questa funzione sul header `funzioni.h` e l'implementazione su un file sorgente **`funzioni.cc`**.

5.  Calcolare la **distanza media** per tutti gli elementi dell'array `punti` tramite una funzione `mean` di tipo `double` che prende come argomento l'array `punti` e la sua dimensione.

6.  Ricordarsi di **pulire la memoria** con attenzione.

-----

### ✍️ Esercizio 2 - Generazione dati su file

Scrivere un programma in C++ in cui:

1.  Definite una funzione di tipo `double` che restituisce la formula:
    $$f(x) = -\frac{\sin(x^2)}{x} + 0.01 x^2$$
    dove $x$ è l'argomento della funzione.

2.  Sul `main` costruire un array $x$ di **100 elementi** distanziati linearmente tra **$[-3, 3]$**.

3.  Stampare su file **`output.dat`** riga per riga le coppie $x$ e $f(x)$.

-----

### 🔍 Esercizio 3 - Data filtering

Scrivere un **programma in C++** in cui dei punti letti da file vengono classificati in 2 categorie: **dentro** e **fuori** da un cerchio centrato nel piano $(x,y) = (0.5, 0.5)$ e raggio $r = 0.5$. Programmare applicando la distinzione tra header e sorgenti.

1.  Definire una struttura dati per punti sul piano $(x,y)$. Scaricare il file di dati con le coordinate $(x,y)$ di 1000 punti con:

    ```bash
    wget https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_9/data3.dat
    # oppure
    curl https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_9/data3.dat -o data3.dat
    ```

2.  Caricare i dati da file in un **array dinamico** della struttura definita al punto 1.

3.  Per ogni elemento dell'array di punti determinare se si trova dentro o fuori del cerchio e stampare le coordinate $(x,y)$ in 2 file distinti, rispettivamente **`dentro.dat`** e **`fuori.dat`**. (*Suggerimento*: costruire una funzione che calcola la distanza tra il punto e il centro del cerchio in modo che il codice di filtraggio sia breve.)

-----

### ⚛️ Esercizio 4 - Data generator

Il file `/home/comune/20190718/data.dat`, presente sulla macchina `tolab.fisica.unimi.it`, contiene riga per riga la descrizione di un numero imprecisato di misure temporali di un oggetto in movimento sullo spazio tridimensionale effettuate in laboratorio. La prima colonna del file determina l'istante $t$, del vettore velocità $(\text{v}_x, \text{v}_y, \text{v}_z)$ sullo spazio tridimensionale, mentre l'ultima colonna contiene l'energia cinetica totale $K$ dell'oggetto all'istante $t$. Dunque, ogni riga del file `data.dat` contiene 1 dato di tipo `int` e 4 dati di tipo `double`.

Definita la struttura:

```c++
struct misure {
    int t;          // istante della misura
    double vx;      // coordinata vx dell'oggetto
    double vy;      // coordinata vx dell'oggetto
    double vz;      // coordinata vz dell'oggetto
    double K;       // energia cinetica totale dell'oggetto
    double massa;   // massa dell'oggetto in moto
};
```

Svolgere i seguenti punti con un programma in C++, usando la distinzione **header/sorgente** e **makefile** assieme ad un script di plotting:

1.  Caricare tutte le misure descritte nel file `data.dat` in un **array di misure allocato dinamicamente**. Il campo `massa` verrà riempito in seguito, inizializzarlo a zero durante il caricamento da file. Stampare a video: (i) il **numero di misure lette** e (ii) la **descrizione completa di ogni misura**. (*Hint*: scrivere funzioni per caricare l'array da file e per stampare la descrizione completa di ogni misura.)

2.  (i) Scrivere una funzione che calcola la massa $m$ per ogni istante $t$ sapendo che l'energia cinetica $K$ è data da:
    $$K = \frac{1}{2} \cdot m \cdot (v_x^2 + v_y^2 + v_z^2)$$
    (ii) Assegnare a ciascuna misura la propria massa, cioè: assegnare al campo `massa` di `misure`.
    (iii) Stampare a video la descrizione aggiornata delle misure. (*Hint*: usare la funzione del punto 1.)

-----

### 🧠 Esercizi Opzionali per l'approfondimento

Questi esercizi sono consigliati per approfondire i concetti della lezione, in particolare la gestione avanzata dei dati e della memoria.

1. **Deallocazione Controllata**

    A partire dall'**Esercizio 1**, concentrarsi sulla gestione della memoria.

    1.  Scrivere una funzione `void dealloca_punti(point2d *punti, int size)` che si occupa di deallocare correttamente sia gli array dinamici `coordinate` interni a ciascuna `struct point2d`, sia l'array principale `punti` (se fosse stato allocato dinamicamente, ma in questo caso pulisce gli array interni).
    2.  Nel `main`, assicurarsi che la funzione venga chiamata una sola volta alla fine del programma per prevenire **memory leak**.
    3.  Utilizzare uno strumento come **Valgrind** (se disponibile sul sistema) per verificare che la deallocazione sia avvenuta senza errori.

2. **Distanza Massima e Minima**

    A partire dall'**Esercizio 1**, dopo aver calcolato tutte le distanze.

    1.  Implementare due funzioni:
        * `double trova_min_distanza(point2d *punti, int size);`
        * `double trova_max_distanza(point2d *punti, int size);`
    2.  Queste funzioni devono scorrere l'array `punti` e restituire rispettivamente la **distanza minima** e la **distanza massima** calcolate (campo `distance`).
    3.  Nel `main`, stampare i valori minimo, massimo e medio (usando la funzione `mean` dell'Esercizio 1).

3. **Strutture e Puntatori a Strutture**

    A partire dall'**Esercizio 4**, modificando la funzione di calcolo massa.

    1.  Modificare la funzione che calcola la massa (punto 2.i dell'Esercizio 4) affinché prenda come argomento un **puntatore a `struct misure`** (`misure* m`) e aggiorni direttamente il campo `massa` della misura puntata. La funzione non dovrà restituire nulla (`void`).
    2.  Rinominare la funzione in `void calcola_e_assegna_massa(misure *m);`.
    3.  Nel `main`, implementare un ciclo in cui si scorre l'array dinamico di misure e si chiama la nuova funzione per ogni elemento, passando l'indirizzo dell'elemento come argomento.
        *Esempio (all'interno del ciclo):* `calcola_e_assegna_massa(&punti[i]);`
