# 💻 Laboratorio di Informatica 8

### Prof. Stefano Carrazza - Corso C

**Riassunto:** Esercizi di base in C++: strutture dati, funzioni, headers e sorgenti.

Prima di iniziare suggeriamo di creare una cartella per questa lezione in cui potete salvare tutti i file che saranno creati per gli esercizi.

```bash
cd ~/           # ci porta alla home directory
mkdir lezione8  # crea la directory sulla vostra home
cd lezione8     # entrate dentro la cartella
```

Dopodiché creare un `makefile` con le istruzioni di compilazione per tutti gli esercizi.

-----

### 🍎 Esercizio 1 - Hello World struct 1

Scrivere un programma in C++ in cui:

1.  Definiamo la struttura seguente:
    ```c++
    struct prodotto {
      int peso;
      double prezzo;
      string nome;
    };
    ```
2.  Dentro il `main` inizializziamo un `prodotto` con `nome` **"banana"**, `peso` di **200g** e `prezzo` di **2.5 euro**.
3.  Scriviamo una funzione `void stampa_prodotto` che prende per argomento `prodotto` e stampa:
    ```
    Prodotto:
      - nome: *stampare nome*
      - peso: *stampare peso*
      - prezzo: *stampare prezzo*
    ```
    Sostituire i valori tra asterischi con i valori numerici salvati nell'oggetto prodotto inizializzato al punto precedente.

-----

### 🛒 Esercizio 2 - Hello World struct 2

Scrivere un programma in C++ in cui:

1.  Definiamo la struttura `prodotto` presentata sopra.
2.  Inizializziamo un **array dinamico** di `prodotto` con dimensione massima di **4 elementi**.
3.  Chiediamo all'utente di introdurre dei prodotti fino a un massimo di **4 elementi**. L'utente dovrà specificare il nome del prodotto, il suo peso e prezzo.
4.  Implementare una funzione `void fattura(prodotto *p, int size);` che prende come argomento l'array dinamico inizializzato dall'utente e stampa la tabella seguente:
    ```
    Fattura
    --------------------------------
    Nome           Peso     Prezzo
    --------------------------------
    *prodotto 1* *peso1* *prezzo1*
    *prodotto 2* *peso2* *prezzo2*
    *prodotto 3* *peso3* *prezzo3*
    *prodotto 4* *peso4* *prezzo4*
    --------------------------------
    Totale (euro): *prezzo totale*
    --------------------------------
    ```
5.  Verificare che il programma funzioni correttamente.

-----

### ➕ Esercizio 3 - Vettori

Scrivere un programma in C++ in cui dei vettori 3D vengono salvati in una struttura dati:

```c++
struct vettore {
  double x;
  double y;
  double z;
};
```

1.  Scrivere la funzione `main` e dichiarare **2 variabili** di tipo `vettore` chiamate `a` e `b` rispettivamente.
2.  Assegnare ad `a` il vettore **(-1, 2, -3)**.
3.  Assegnare a `b` il valore di `a`.
4.  Implementare una funzione `scalar` di tipo `double` che calcola il **prodotto scalare** tra 2 oggetti di tipo `vettore`. Testare tale funzione direttamente sul `main` passando `a` e `b` come argomenti e stampando il risultato su terminale.
5.  Implementare una funzione `somma` di tipo `vettore` che prende come argomenti 2 oggetti `vettore` e ritorna un nuovo oggetto `vettore` in cui le coordinate corrispondono alla **somma delle coordinate** degli argomenti. Stampare le coordinate del nuovo vettore su terminale.

-----

### ⚙️ Esercizio 4 - Headers e sorgente

Scrivere un programma in C++ in cui viene utilizzato un file header.

1.  Creare un file header intitolato `funzioni.h` e dichiarare una funzione `scambia1` di tipo `void` che prende come argomenti i **riferimenti** a 2 numeri di tipo `double`.
2.  Sempre sullo stesso header, dichiarare un'ulteriore funzione chiamata `scambia2` di tipo `void` che prende i **puntatori** di 2 numeri di tipo `double`.
3.  Creare un file `funzioni.cc` in cui viene implementato un algoritmo di scambio tra le variabili di tipo `double` per le funzioni `scambia1` e `scambia2`.
4.  Creare un file `main.cc`, includere il header `funzioni.h` e testare le funzioni `scambia1` e `scambia2`.
5.  Aggiustare sul `makefile` il comando di compilazione tenendo conto di tutti i files `*.cc`.

-----

### 🧠 Esercizi Opzionali per l'approfondimento

Questi esercizi sono consigliati per approfondire i concetti della lezione.

1. **Prodotto Maggiore**

    A partire dalla struttura `prodotto` dell'Esercizio 1 e 2:

    - Implementare una funzione `prodotto* trova_maggiore(prodotto *p, int size);` che riceve un array dinamico di prodotti e restituisce un **puntatore** al prodotto con il prezzo maggiore.
    - Nel `main`, inizializzare un array di almeno 3 prodotti e utilizzare la funzione per trovare e stampare il nome e il prezzo del prodotto più costoso.

2. **Strutture Annidate: Data**

    Scrivere un programma in C++ che utilizza strutture dati annidate.

    1.  Definire la struttura `data` per rappresentare una data:
        ```c++
        struct data {
          int giorno;
          int mese;
          int anno;
        };
        ```
    2.  Definire la struttura `evento` che contiene un `string nome` e un oggetto `data`:
        ```c++
        struct evento {
          string nome;
          data data_evento;
        };
        ```
    3.  Nel `main`, creare un oggetto `evento` (es. "Compleanno", data 10/12/2025) e una funzione `void stampa_evento(evento e)` che stampa i dettagli dell'evento, incluso il formato della data (Giorno/Mese/Anno).

3. **Headers e Vettori (Prodotto Vettoriale)**

    A partire dalle strutture e funzioni dell'Esercizio 3 (Vettori):

    1.  Aggiungere al file header `funzioni.h` una dichiarazione per una nuova funzione `vettore prodotto_vettoriale(vettore a, vettore b);`.
    2.  Nel file `funzioni.cc`, implementare la funzione `prodotto_vettoriale` che calcola il **prodotto vettoriale** tra i due vettori 3D e restituisce il `vettore` risultante.
        > Il prodotto vettoriale $c = a \times b$ ha coordinate $c_x = a_y b_z - a_z b_y$, $c_y = a_z b_x - a_x b_z$, $c_z = a_x b_y - a_y b_x$.
    3.  Nel `main.cc`, testare la nuova funzione e stampare le coordinate del vettore risultato del prodotto vettoriale tra `a = (1, 0, 0)` e `b = (0, 1, 0)`.
