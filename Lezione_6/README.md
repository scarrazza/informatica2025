# 💻 Laboratorio di Informatica 6

### Prof. Stefano Carrazza - Corso C

Esercizi di base in C++ focalizzati sull'utilizzo degli **array** (stack e dinamici).

Prima di iniziare, si suggerisce di creare una cartella dedicata a questa lezione per salvare tutti i file degli esercizi e un `makefile` per semplificare la compilazione.

```bash
cd ~/           # Spostamento alla home directory
mkdir lezione6  # Creazione della cartella
cd lezione6     # Accesso alla cartella creata
```

Successivamente, creare un `makefile` con le istruzioni di compilazione necessarie per tutti gli esercizi.

-----

### 🚀 Esercizio 1 - Hello World con Stack Arrays

Scrivere un programma in C++ che sfrutti l'uso degli array allocati sullo stack (dimensione fissa).

1.  **Costruzione Vettori:** Costruire i seguenti vettori di tipo `double` usando *stack arrays* (dimensione 5):

$$
\mathbf{v} = \begin{pmatrix}
2 \\
5 \\
10 \\
20 \\
50
\end{pmatrix},\quad
\mathbf{w} = \begin{pmatrix}
10 \\
-5 \\
3 \\
1 \\
100
\end{pmatrix}
$$


3.  **Stampa Iniziale:** Stampare su terminale i valori degli array `v` e `w`, seguendo il formato:

    ```
    v[0] = <valore>
    v[1] = <valore>
    ...
    w[0] = <valore>
    w[1] = <valore>
    ...
    ```

4.  **Copia e Inizializzazione:** Creare un array `double s[5]` e inizializzarlo con i valori contenuti in `v`.

5.  **Somma:** Sommare gli elementi di `w` con i rispettivi elementi di `s` (i.e., $s[i] = s[i] + w[i]$).

6.  **Stampa Finale:** Stampare il nuovo array `s` su schermo, utilizzando lo stesso formato del punto 2.

-----

### 📐 Esercizio 2 - Prodotto Scalare con Array Dinamici

Scrivere un programma in C++ che calcola il prodotto scalare tra array allocati dinamicamente.

1.  **Allocazione Dinamica:** Costruire i vettori `v` e `w` dell'Esercizio 1 (dimensione 5) usando **array dinamici**.

    > **⚠️ Attenzione:** Ricordarsi di allocare con l'operatore `new` e liberare la memoria con l'operatore `delete` alla fine del programma/scope.

2.  **Prodotto Scalare:** Implementare il **prodotto scalare** tra `v` e `w` e stampare il risultato.

3.  **Copia e Modifica:** Creare un vettore dinamico `z` come copia esatta di `v` (stessa dimensione e contenuti). Successivamente, impostare il valore di `z[2]` a 0.

4.  **Normalizzazione:** Calcolare e stampare su schermo la **norma Euclidea** (o modulo) del vettore `z`:
    $$||\mathbf{z}|| = \sqrt{\sum_{i=0}^{N-1} z_i^2}$$

5.  **Vettore Normalizzato:** Normalizzare il vettore `z` (ossia, dividere ogni elemento $z_i$ per la sua norma) e stampare i suoi valori su terminale.

-----

## 🏎️ Esercizio 3 - Analisi del Moto Rettilineo

Scrivere un programma C++ per l'analisi statistica della velocità di una particella, leggendo i dati da file.

1.  **Download Dati:** Scaricare il file dei dati:

    ```bash
    wget https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_6/data_moto.dat
    # oppure con
    curl -o data_moto.dat https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_6/data_moto.dat
    ```

2.  **Lettura e Calcolo:** Leggere dal file le $N=1000$ coppie di punti **(spazio (km), tempo (h))**. Calcolare per ogni misura la **velocità istantanea** ($v_i = x_i / t_i$). Salvare tutte le velocità in un array di tipo `double`.

3.  **Statistiche (Media e Deviazione Standard):** Calcolare la **velocità media** ($\bar{v}$) e la rispettiva **deviazione standard** ($\sigma_v$). Stampare i risultati su schermo.

4.  **Statistiche (Minimo e Massimo):** Calcolare e stampare i valori di **velocità minima** e **velocità massima**.

5.  **Verifica:** Verificare visivamente i risultati ottenuti con il plot seguente:

<img src="images/moto.png" width="400">

-----

### 🔬 Esercizio 4 - Ricerca della Massa del Bosone di Higgs

Scrivere un programma C++ che legge la distribuzione di massa invariante per il bosone di Higgs e ne determina il valore più probabile (il *picco*).

La distribuzione in questione si presenta graficamente nel modo seguente:

<img src="images/higgs.png" width="400">

1.  **Download Dati:** Scaricare il file dei dati:

    ```bash
    wget https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_6/data_higgs.dat
    # oppure con
    curl -o data_higgs.dat https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_6/data_higgs.dat
    ```

2.  **Lettura Dati:** Leggere tutti gli $N = 10000$ valori di massa invariante e salvarli in un array dinamico `mass` di tipo `double`.

3.  **Ordinamento:** Ordinare il vettore `mass` in modo crescente usando l'algoritmo **Selection Sort**. *(Per verifica, si consiglia di stampare su schermo i primi e gli ultimi valori.)*

4.  **Minimo e Massimo Vettoriale:** Estrarre il valore **minimo** e **massimo** direttamente dall'array `mass` (sfruttando l'ordinamento, *senza implementare cicli o algoritmi aggiuntivi*). Stampare i valori su terminale.

5.  **Definizione Bins:** Costruire un array dinamico `bins` che contenga i **bordi superiori** (upper edge) di un istogramma, partendo dal valore minimo della massa fino al valore massimo, con *steps da 5 GeV*.

6.  **Array Frequenze:** Creare un array dinamico `freq` per le frequenze (conteggi) dell'istogramma, inizializzato a zero.

7.  **Istogrammazione:** Implementare l'algoritmo di istogrammazione. Stampare su schermo i valori dei bins (lower-edge e upper-edge) e le rispettive frequenze.

8.  **Determinazione Massa:** Determinare e stampare il **bin di massa del Higgs** (specificando il *lower-edge* del bin) con la frequenza più elevata.

-----

### 🧠 Esercizi Opzionali per l'approfondimento

Questi esercizi sono proposti per approfondire e consolidare le competenze sugli array e sull'analisi dei dati.

1. **Implementazione di Altri Algoritmi di Ordinamento**

    Rifare il punto 3 dell'Esercizio 4 utilizzando i seguenti algoritmi di ordinamento alternativi:

    * **Bubble Sort**
    * **Insertion Sort**
    * **Merge Sort** (più avanzato)

    Misurare e confrontare il tempo di esecuzione di ciascun algoritmo per ordinare l'array `mass` di $10000$ elementi.

2. **Intervalli di Confidenza per la Media**

    Nell'Esercizio 3, dopo aver calcolato la velocità media ($\bar{v}$) e la deviazione standard ($\sigma_v$), calcolare l'**errore sulla media** ($\sigma_{\bar{v}}$) e determinare l'**intervallo di confidenza al 95%** per la velocità media.
    $$\sigma_{\bar{v}} = \frac{\sigma_v}{\sqrt{N}}$$

    Stampare su schermo la media con il rispettivo errore.

3. **Array Bidimensionali (Matrici)**

    Scrivere un programma C++ che:

    1.  Definisce e inizializza una matrice $3 \times 3$ sullo stack.
    2.  Definisce e inizializza una matrice $3 \times 3$ dinamicamente (`new double*[3]`).
    3.  Implementa la funzione per il **prodotto tra matrici** e la applica alle due matrici $3 \times 3$.
    4.  Stampa su schermo la matrice risultante.
