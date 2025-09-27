# 💻 Laboratorio di informatica 1

### Prof. Stefano Carrazza - Corso C

Questa dispensa introduce i concetti fondamentali dell'uso del **sistema operativo Linux**. L'obiettivo è fornire una panoramica dell'ambiente desktop, del terminale, e dei comandi di base per la gestione dei file. Gli esercizi proposti vi guideranno attraverso i primi passi per preparare il vostro ambiente di lavoro.

-----

### 🔑 Esercizio 1: Registrazione e accesso al laboratorio

Per poter utilizzare le macchine del laboratorio di calcolo del Dipartimento di Fisica, è necessario registrarsi. Segui questi passaggi:

  * Visita il sito per la registrazione: [https://studenti.fisica.unimi.it/registrazione](https://studenti.fisica.unimi.it/registrazione).
  * Una volta completata la registrazione, potrai accedere alle macchine del laboratorio con le credenziali che hai impostato.

-----

### ⌨️ Esercizio 2: Il terminale e i comandi Bash

Per interagire con il sistema operativo in modo efficiente, impareremo a usare il **terminale**. Questo programma ci permette di eseguire comandi usando un linguaggio chiamato **Bash** (Bourne-Again SHell), uno dei più popolari e potenti.

  * Cerca e apri l'applicazione Terminal.
  * Il primo comando che impareremo è `echo`, che stampa a schermo il testo che gli viene passato. Prova a scrivere:
    ```bash
    echo "Hello World!"
    ```

  * premi Invio per eseguire il comando. **Ricorda**: ogni comando deve essere seguito dalla pressione del tasto Invio/Enter.
  * Per scoprire i comandi più comuni in Bash, usa il comando `help`.
  * Per ottenere informazioni dettagliate su un comando specifico, puoi usare `man` (manual page). Ad esempio, per sapere di più sul comando `echo`, scrivi:
    ```bash
    man echo
    ```

  * Per uscire dalla pagina del manuale, premi il tasto `q`.
  * Usa le frecce su e giù sulla tastiera per scorrere i comandi che hai già digitato, in modo da non doverli riscrivere ogni volta.
  * Per approfondire, puoi consultare la pagina di Wikipedia su Bash: [https://it.wikipedia.org/wiki/Bash](https://it.wikipedia.org/wiki/Bash).

**Esercizio Aggiuntivo**:
Crea un **alias** per il comando `ls -l` in modo da non doverlo digitare ogni volta. Cerca come si fa a creare un alias con Bash e provalo. (Suggerimento: usa il comando `alias`).

-----

### 📂 Esercizio 3: Navigazione e gestione del file system

Il **file system** è la struttura che organizza i file e le cartelle (chiamate anche directories) sul disco fisso. La directory principale, chiamata **root**, è indicata con il simbolo `/`. Al suo interno si trovano le sottocartelle del sistema come `/home/`, `/usr/`, `/bin/`, ecc.

Ogni utente ha una propria directory home (ad esempio, `/home/john`), dove ha i permessi di lettura e scrittura completi. Useremo questa directory per tutti i nostri esercizi.

Ecco i comandi principali per interagire con il file system. Puoi sempre usare `man <comando>` per maggiori dettagli.

| Comando | Nome esteso | Funzione | Esempio |
| :--- | :--- | :--- | :--- |
| `pwd` | Print Working Directory | Mostra il percorso della cartella in cui ti trovi. | `pwd` |
| `ls` | List | Elenca i file e le cartelle nella directory attuale. | `ls -l` (mostra dettagli come permessi e dimensioni) |
| `mkdir` | Make Directory | Crea una nuova cartella. | `mkdir NuovaCartella` |
| `touch` | - | Crea un file vuoto. | `touch file.txt` |
| `rm` | Remove | Cancella un file o una cartella. **Attenzione**: questo comando è irreversibile\! | `rm file.txt` |
| `rm -r` | Remove (recursive) | Cancella una cartella e tutto il suo contenuto. | `rm -r CartellaDaCancellare` |
| `cd` | Change Directory | Naviga tra le cartelle. | `cd Documents`, `cd ..` (torna alla cartella precedente), `cd -` (torna alla cartella visitata prima) |
| `cat` | Concatenate | Mostra il contenuto di un file direttamente nel terminale. | `cat file.txt` |

**Esercizio Pratico**:

  * Naviga nella tua home directory (basta digitare `cd`).
  * Verifica la directory in cui ti trovi con il comando `pwd`.
  * Crea una cartella chiamata `corso_di_informatica` con il comando `mkdir`.
  * Entra nella cartella `corso_di_informatica` e crea al suo interno un'altra cartella chiamata `Lezione1`.
  * Entra nella cartella `Lezione1` e crea un file vuoto chiamato `data.txt` (digitando `touch data.txt`).
  * Verifica che la struttura sia corretta usando il comando `ls -l`.

Il risultato dovrebbe essere:
```
/home/<tuo_username>/corso_di_informatica
  └─ Lezione1
       └─ data.txt
```

-----

### 📝 Esercizio 4: Copiare e spostare file

Ora che sai come creare file e cartelle, vediamo come gestirli.

  * **Copiare file (`cp`)**:
    ```bash
    cp <sorgente> <destinazione>
    ```
    Per copiare una cartella e tutto il suo contenuto, devi usare l'opzione `-r` (recursive): `cp -r <cartella_sorgente> <cartella_destinazione>`.

  * **Spostare o rinominare file (`mv`)**:
    ```bash
    mv <sorgente> <destinazione_o_nuovo_nome>
    ```
    Questo comando serve sia per spostare un file in un'altra cartella che per rinominarlo.

**Esercizio Pratico**:

  * Posizionati nella cartella `corso_di_informatica/Lezione1` che hai creato prima.
  * Crea un file di testo chiamato `temp.txt`.
  * Copia il file `temp.txt` nella cartella `corso_di_informatica`.
  * Posizionati nella cartella `corso_di_informatica`.
  * Rinomina `temp.txt` in `README.md` usando il comando `mv`.
  * Sposta il file `README.md` nella cartella `Lezione1`.
  * Elimina il file `temp.txt` (che si trova ancora nella cartella `Lezione1`) e verifica che tutto sia a posto.

Dopodiché:

  * Usa `echo` per aggiungere la frase "Questa è una lezione di Bash." all'interno del file `README.md`. Puoi farlo con il seguente comando:
    ```bash
    echo "Questa è una lezione di Bash." > README.md
    ```
  * Visualizza il contenuto del file `README.md` usando `cat`.

Ora che hai terminato, è il momento di pulire e riordinare lo spazio di lavoro.

  * Torna alla tua home directory.
  * Usa il comando `rm -r` per cancellare l'intera cartella `corso_di_informatica`.
  * Verifica che la cartella sia stata rimossa correttamente usando `ls`.

-----

### ✍️ Esercizio 5: Utilizzare un editor di testo

Gli editor di testo sono essenziali per scrivere e modificare codice. Su Linux, esistono molti editor, e ognuno ha le sue specificità.

  * `gedit`: semplice e intuitivo, ottimo per chi inizia.
  * `vim` e `emacs`: editor molto potenti e configurabili, ma richiedono tempo per essere imparati.
  * `code`: un editor moderno, con molte funzionalità integrate e un'interfaccia grafica.

**Esercizio con Visual Studio Code (code)**:

  * Apri il terminale e naviga in una cartella a tua scelta dentro la tua home.
  * Apri Visual Studio Code creando un nuovo file chiamato `file1.txt`:
    ```bash
    code file1.txt
    ```
  * Scrivi qualcosa all'interno, salvalo e chiudi `code`.
  * Torna al terminale e verifica il contenuto del file con il comando `cat file1.txt`.
  * Cancella il file `file1.txt` usando `rm`.
  * Ripeti l'operazione, ma questa volta creando un file `file.cc`:
    ```bash
    code file.cc
    ```

  * Crea la riga `#include <iostream>`. Noterai che code riconosce la sintassi del C++ e colora le parole di conseguenza.

**Nota sui caratteri speciali per la tastiera italiana**:

  * `{` = Alt Gr + Shift + è
  * `}` = Alt Gr + Shift + +
  * `~` = Alt Gr + ì

-----

### 🌐 Esercizio 6 (Opzional da casa): Accesso remoto (ssh) e copia di file (scp)

Lavorare da remoto è una pratica comune. Impareremo a usare i comandi `ssh` e `scp` per connetterci alle macchine del laboratorio dal tuo computer e viceversa.

**Accesso remoto con ssh**

`ssh` (Secure SHell) ti permette di connetterti a un computer remoto e usare il suo terminale.

```bash
ssh <username>@<indirizzo_computer>
```

  * `ssh <username>@tolab.fisica.unimi.it`: per accedere alle macchine del laboratorio.
  * `ssh -X <username>@<indirizzo_computer>`: se vuoi che le applicazioni grafiche del computer remoto vengano visualizzate sul tuo schermo.
  * Per disconnetterti, usa il comando `exit`.

**Copia di file con scp**

`scp` (Secure CoPy) ti permette di copiare file tra computer in rete.

```bash
# Per copiare un file dal tuo PC al server remoto
scp <file_locale> <username>@<indirizzo_computer>:<percorso_remoto>

# Per copiare un file dal server remoto al tuo PC
scp <username>@<indirizzo_computer>:<file_remoto> <percorso_locale>
```

Per copiare intere cartelle, usa l'opzione `-r` (recursive).

**Esercizio Pratico**:

  * Connettiti a una macchina del laboratorio con `ssh`.
  * Verifica il contenuto della tua home directory remota.
  * Da un nuovo terminale sul tuo computer locale, copia un file che hai creato in precedenza dalla tua macchina locale a quella remota usando `scp`.
  * Copia un file dalla macchina remota alla tua usando `scp`.

-----

### 🧠 Esercizi Opzionali per l'approfondimento

Se hai completato gli esercizi precedenti e vuoi mettere alla prova le tue nuove competenze, prova a risolvere questi problemi.

1.  **Creazione e gestione avanzata di file**:

      * Crea una cartella chiamata `Esercizi_Extra`.
      * Al suo interno, crea 10 file vuoti chiamati `file1.txt`, `file2.txt`, ..., `file10.txt` usando un solo comando Bash. (Suggerimento: cerca come usare le parentesi graffe `{}` con il comando `touch`).
      * Cancella tutti i file appena creati con un solo comando. (Suggerimento: usa `rm` con il carattere jolly `*`).

2.  **Redirezione dell'output**:

      * Il comando `ls` stampa i nomi dei file a schermo. Prova a reindirizzare l'output del comando `ls -l` in un nuovo file chiamato `elenco_file.txt`. (Suggerimento: usa il carattere `>`).
      * Visualizza il contenuto di `elenco_file.txt` usando `cat`.

3.  **Comandi concatenati**:

      * Crea una singola riga di comando che, partendo dalla tua home directory, crei una cartella chiamata `progetto`, si sposti al suo interno, crei un file `main.cc` e apra `code` su quel file. (Suggerimento: usa il punto e virgola `;` per concatenare i comandi).

4.  **Ricerca di file**:

      * Cerca il comando `find`. Usalo per trovare tutti i file con estensione `.txt` all'interno della tua home directory.

5.  **Permessi dei file**:

      * Usa il comando `ls -l` su un file. Osserva i permessi (es. `-rw-r--r--`). Cerca il comando `chmod` e prova a cambiare i permessi di un file, ad esempio rendendolo eseguibile per tutti.
