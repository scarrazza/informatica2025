# 💻 Laboratorio di Informatica 5

### Prof. Stefano Carrazza - Corso C

Esercizi fondamentali in C++ sull'uso dei **cicli** (`for`, `while`, `do/while`).

Prima di iniziare, per mantenere organizzato il lavoro, create una cartella dedicata a questa lezione e salvatevi tutti i file degli esercizi.

```bash
cd ~/           # Vai alla home directory
mkdir lezione5  # Crea la directory
cd lezione5     # Entra nella cartella
```

Successivamente, create un **`makefile`** con le istruzioni di compilazione per tutti gli esercizi.

-----

### 💬 **Esercizio 1: Hello World con i tre cicli**

Implementare un programma in C++ che sfrutti le tre strutture iterative fondamentali per stampare un messaggio sul terminale.

1.  Creare un ciclo **`for`** che stampi **5 volte** il messaggio, indicando l'indice di iterazione:

    ```
    Hello World for index = *i*
    ```

    dove `*i*` è l'indice intero del loop.

2.  Analogamente, implementare un ciclo **`while`** che stampi lo stesso messaggio per 5 volte:

    ```
    Hello World while index = *i*
    ```

3.  Infine, implementare un ciclo **`do/while`** per la stessa operazione:

    ```
    Hello World do/while index = *i*
    ```

-----

### 📊 **Esercizio 2: Calcolo della Media (Input da Terminale)**

Scrivere un programma in C++ che calcoli la media aritmetica di una serie di numeri forniti in input dall'utente, utilizzando un ciclo **`for`**.

1.  Chiedere all'utente **quanti numeri** (`n`, di tipo `int`) desidera introdurre.
2.  Utilizzare un ciclo `for` per chiedere all'utente di inserire sequenzialmente `n` numeri, di tipo **`double`**.
3.  Mantenere un totale progressivo (`double sum = 0.0;`) e incrementarlo con ciascun numero introdotto.
4.  Al termine del ciclo, calcolare la media.
5.  Stampare il risultato finale su schermo.

-----

### 🧮 **Esercizio 3: Contatore di Numeri Pari e Dispari**

Creare un programma in C++ che conti il numero totale di numeri **pari** e **dispari** introdotti dall'utente.

1.  Implementare un ciclo (`for` o `while`) che chieda all'utente di introdurre numeri **interi**. La condizione per **terminare** l'input deve essere l'invio del segnale **CTRL+D** (o **CTRL+Z** su alcuni sistemi), rilevato tramite la condizione `cin.eof()`.
2.  Per ogni numero introdotto, utilizzare una struttura `if/else` e l'operatore **modulo** (`%`) per determinarne la parità o disparità.
3.  Utilizzare due contatori interi (`int`) distinti per tenere traccia dei totali.
4.  Al termine dell'input, stampare su schermo il totale dei numeri pari e dei numeri dispari.

-----

### 📂 **Esercizio 4: Calcolo della Media (Input da File)**

Calcolare la media aritmetica dei dati contenuti in un file esterno.

1.  **Scaricare il file di dati** contenente $1000$ misurazioni della costante di accelerazione di gravità `g`. Eseguire il comando appropriato sul terminale:

    ```bash
    wget https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_5/data.dat
    # oppure (per macOS o alternative a wget)
    curl https://raw.githubusercontent.com/scarrazza/informatica2025/master/Lezione_5/data.dat -o data.dat
    ```

2.  Aprire il file e **leggere tutti i numeri** utilizzando un ciclo, la cui condizione di terminazione è raggiunta quando si verifica la **fine del file** (`eof`).

3.  Mantenere una variabile `double sum = 0.0;` per la somma incrementale dei valori.

4.  Contare il numero totale di elementi letti.

5.  Calcolare la media e stamparla su schermo. Verificare che il valore ottenuto sia prossimo a $g \approx 9.7803184$.

-----

### 📈 **Esercizio 5: Successione di Fibonacci**

Scrivere un programma in C++ che calcoli e stampi i primi $n$ elementi della celebre successione di Fibonacci.

**La regola:** I primi due elementi sono $0$ e $1$. Ogni elemento successivo è la somma dei due precedenti (es. $0, 1, 1, 2, 3, 5, 8, \dots$).

1.  Chiedere all'utente **quanti elementi** (`n`, di tipo `int`) della successione desidera calcolare.
2.  Implementare un ciclo **`for`** che calcoli e stampi tutti gli $n$ elementi. Assicurarsi di gestire correttamente i primi due elementi $(0, 1)$ al di fuori o all'inizio del ciclo.

-----

### 🧠 Esercizi Opzionali per l'approfondimento

Questi esercizi sono pensati per chi vuole mettere alla prova le proprie conoscenze e approfondire l'uso dei cicli e delle strutture dati.

1. **Stampa al Contrario (Palindromi)**

    Scrivere un programma che:

    1.  Chieda all'utente di inserire un numero intero positivo.
    2.  Utilizzi un ciclo (`while` o `do/while`) per **stampare le cifre del numero al contrario**. Ad esempio, se l'input è $12345$, l'output deve essere $54321$.
    3.  **SFIDA:** Modificare il programma per determinare se il numero inserito è un **palindromo** (ossia, si legge allo stesso modo sia da destra che da sinistra, es. $121$).

2. **Ricerca del Massimo**

    Scrivere un programma che:

    1.  Chieda all'utente di inserire una serie di numeri **`double`** (simulando, ad esempio, delle temperature).
    2.  Utilizzi un ciclo (`while`) per continuare a leggere i numeri finché l'utente non inserisce un valore "sentinella" (ad esempio, il numero $0.0$).
    3.  Durante il ciclo, **identifichi e salvi il numero più grande** (`massimo`) introdotto fino a quel momento.
    4.  Al termine, stampi il valore massimo trovato.

3. **Controllo di un Intervallo**

    Scrivere un programma che chieda all'utente di inserire un numero intero positivo. **Vincolare l'input** a un intervallo specifico (ad esempio, $[1, 100]$) utilizzando un ciclo **`do/while`**. Il programma deve:

    1.  Chiedere ripetutamente l'input all'utente.
    2.  Continuare a chiedere l'input **finché** il numero non rientra nell'intervallo richiesto.
    3.  Stampare un messaggio di conferma solo quando l'input è valido.
