# 💻 Laboratorio di Informatica 3

### Prof. Stefano Carrazza - Corso C

Questa sessione si concentra sulle basi della programmazione in C++, esplorando concetti fondamentali come la gestione di testo (`string`), l'interazione con l'utente (`cin`, `cout`), l'uso di operatori aritmetici e logici e la gestione di file (`fstream`).

Prima di iniziare, ti suggeriamo di organizzare i tuoi file in una cartella dedicata per mantenere l'ambiente di lavoro pulito e ordinato.

```bash
cd ~              # Naviga alla tua home directory
mkdir lezione3    # Crea una nuova cartella
cd lezione3       # Entra nella cartella appena creata
```

## 🛠️ Setup del Progetto con `Makefile`

Per compilare ed eseguire i tuoi programmi in modo efficiente, crea un `Makefile` nella cartella `lezione3`. Questo file ti permetterà di automatizzare le operazioni di compilazione (`make all`) e pulizia dei file generati (`make clean`).

```makefile
# Makefile
all: esercizio1 esercizio2 esercizio3 esercizio4 esercizio5

esercizio1: esercizio1.cc
	g++ -o esercizio1 esercizio1.cc

esercizio2: esercizio2.cc
	g++ -o esercizio2 esercizio2.cc

esercizio3: esercizio3.cc
	g++ -o esercizio3 esercizio3.cc

esercizio4: esercizio4.cc
	g++ -o esercizio4 esercizio4.cc

esercizio5: esercizio5.cc
	g++ -o esercizio5 esercizio5.cc

clean:
	rm -f esercizio1 esercizio2 esercizio3 esercizio4 esercizio5
```

Per compilare tutti i programmi, esegui:

```bash
$ make all
```

Per rimuovere tutti i file eseguibili creati, esegui:

```bash
$ make clean
```

-----

### **🔢 Esercizio 1: Operazioni Aritmetiche Base**

Questo esercizio ti introduce agli operatori di incremento, decremento, divisione e modulo in C++.

1.  Chiedi all'utente di inserire un numero intero `n`.
2.  Calcola l'incremento (`++`) e il decremento (`--`) di `n`.
3.  Calcola la divisione e il resto (`%`) di `n` per un numero intero `r = 2`.
4.  Stampa tutti i risultati a schermo in un formato chiaro e leggibile.

-----

### **✅ Esercizio 2: Controllo di Numeri Pari e Dispari**

Utilizza l'operatore modulo (`%`) e la logica condizionale (`if` e `else`) per determinare se un numero è pari o dispari.

1.  Chiedi all'utente di inserire un numero intero.
2.  Verifica se il numero è pari o dispari.
3.  Stampa il risultato a schermo.

-----

### **👤 Esercizio 3: Gestione di Nomi e Dati Personali**

Lavora con diversi tipi di variabili (`char`, `string`, `int`) per acquisire e stampare informazioni personali.

1.  Chiedi all'utente di inserire il proprio nome, cognome e numero di matricola.
      * Usa `char nome[20];` per il nome.
      * Usa `std::string` per il cognome.
      * Usa `int` per il numero di matricola.
2.  Stampa un riepilogo delle informazioni nel formato:
    ```
    <cognome>, <nome> è registrato con numero matricola: <matricola>.
    ```

-----

### **✍️ Esercizio 4: Scrittura su File**

Estendi l'esercizio precedente per salvare l'output su un file, introducendo il concetto di I/O (Input/Output) su file.

1.  Crea una copia del programma dell'Esercizio 3.
2.  Usa `fstream` per creare e aprire un nuovo file chiamato `risultato.dat`.
3.  Dopo aver verificato che il file sia stato aperto correttamente (con `good()`), scrivi l'output su questo file, oltre che su schermo.
4.  Chiudi il file alla fine del programma con `close()`.

-----

### **📂 Esercizio 5: Lettura da File**

Modifica il programma dell'Esercizio 4 per leggere l'input da un file, simulando una gestione dati più automatizzata.

1.  Crea una copia del programma dell'Esercizio 4.
2.  Usa `fstream` per aprire un file di input chiamato `myinput.dat` (assicurati che esista e contenga le informazioni necessarie).
3.  Leggi i dati (nome, cognome, matricola) direttamente da questo file.
4.  Chiudi il file.
5.  Stampa il risultato sia a schermo che sul file `risultato.dat`, come nell'esercizio precedente.

-----

### 🧠 Esercizi Opzionali per l'approfondimento

Se hai completato gli esercizi precedenti e vuoi mettere alla prova le tue nuove competenze, prova a risolvere questi problemi.

1.  **Calcolatore di Voti**:

    Scrivi un programma che chieda all'utente un punteggio da 0 a 100 e stampi la valutazione corrispondente (`A`, `B`, `C`, `D`, `F`) usando una serie di istruzioni `if`, `else if` ed `else`.

      - `A`: 90-100
      - `B`: 80-89
      - `C`: 70-79
      - `D`: 60-69
      - `F`: 0-59

2.  **Conta Vocali e Consonanti**

    Scrivi un programma che chieda all'utente una singola riga di testo e conti il numero di vocali e consonanti al suo interno. Ignora gli spazi e i caratteri speciali. Usa un ciclo (`for` o `while`) e un'istruzione condizionale.

3.  **Gestione Errori in File I/O**

    Migliora l'Esercizio 4 o 5 per includere una gestione degli errori più robusta. Se il file non si apre correttamente, il programma deve stampare un messaggio di errore a schermo e terminare.
