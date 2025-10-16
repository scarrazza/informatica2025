# 💻 Laboratorio di Informatica 4

### Prof. Stefano Carrazza - Corso C

Questa dispensa serve a praticare le strutture di controllo fondamentali in C++: **`if`**, **`else`**, **`else if`** e **`switch`**.

Prima di iniziare, si consiglia vivamente di organizzare il lavoro creando una cartella dedicata per questa sessione. Questo aiuterà a mantenere ordinati tutti i file degli esercizi (`.cpp`, `makefile`, ecc.).

```bash
cd ~              # Naviga alla tua home directory
mkdir lezione4    # Crea la directory 'lezione4'
cd lezione4       # Entra nella cartella 'lezione4'
```

Successivamente, si consiglia di creare un **`makefile`** che contenga le istruzioni necessarie per compilare tutti gli esercizi con un comando semplificato.

-----

### 🌡️ **Esercizio 1: Conversione di Temperature**

Scrivere un programma in C++ che permetta all'utente di convertire una temperatura data in **Celsius** ($^\circ\text{C}$) in **Kelvin** ($\text{K}$) o **Fahrenheit** ($^\circ\text{F}$), utilizzando la struttura di selezione a due vie **`if`** / **`else`**.

#### Istruzioni Dettagliate

1.  **Input Celsius:** Richiedere all'utente di inserire la temperatura di input in Celsius tramite `std::cin`.
2.  **Archiviazione:** Salvare il valore in una variabile di tipo **`double`**.
3.  **Scelta Conversione:** Chiedere all'utente di selezionare il tipo di conversione desiderata:
    ```text
    Premere 1 per conversione a Kelvin (K).
    Premere 2 per conversione a Fahrenheit (°F).
    Opzione scelta: *implementare cin*
    ```
4.  **Selezione:** Salvare la scelta in una variabile **`int`** e implementare la logica di selezione con **`if/else`**.
5.  **Formule:** Applicare le seguenti formule di conversione per l'opzione scelta:
    $$T(\text{Kelvin}) = T(\text{Celsius}) + 273.15$$   $$T(\text{Fahrenheit}) = T(\text{Celsius}) \times \frac{9.0}{5.0} + 32.0$$
6.  **Output:** Stampare il risultato formattato in modo chiaro e leggibile:
    ```text
    T(Celsius) = *valore di input* -> T(*unità scelta*) = *valore dopo la conversione*
    ```

#### 🧪 Test di Verifica

Assicurarsi che il programma fornisca i seguenti risultati corretti:

  - $20{\,}^\circ\text{C} \to 68.0{\,}^\circ\text{F}$
  - $20{\,}^\circ\text{C} \to 293.15{\,}\text{K}$

-----

### 📐 **Esercizio 2: Risoluzione di Equazione Quadratica**

Scrivere un programma in C++ che risolva l'equazione quadratica $\mathbf{a x^2 + b x + c = 0}$. Il programma dovrà gestire tutti i possibili scenari del discriminante ($D > 0$, $D = 0$ e $D < 0$) utilizzando la struttura di selezione a più vie **`if/else if/else`**. I coefficienti $a$, $b$ e $c$ devono essere forniti dall'utente tramite `std::cin`.

#### Istruzioni Dettagliate

1.  **Input Coefficienti:** Richiedere all'utente l'introduzione di tre numeri (**`double`**) per i coefficienti $a$, $b$ e $c$.
2.  **Calcolo Discriminante:** Calcolare il discriminante $D$:
    $$D = b^2 - 4ac$$
    Utilizzare la funzione `std::pow(b, 2)` o semplicemente `b * b` per l'elevamento a potenza.
3.  **Condizione:** Creare una condizione **`if/else if/else`** per gestire i tre casi possibili per il discriminante $D$:
      * $D > 0$: Due soluzioni reali e distinte.
      * $D = 0$: Una soluzione reale (due coincidenti).
      * $D < 0$: Due soluzioni complesse coniugate.
4.  **Calcolo Soluzioni:** Calcolare le soluzioni $x_1$ e $x_2$ utilizzando la nota formula quadratica:
    $$x_{1,2} = \frac{-b \pm \sqrt{D}}{2a}$$
    **Nota Importante:** Per il caso $D < 0$, $\sqrt{D}$ produce un numero immaginario. Poiché `std::sqrt()` opera in campo reale, il suo argomento deve essere positivo. Si suggerisce di calcolare separatamente la componente reale e la componente immaginaria delle soluzioni:
    $$x_{1,2} = \frac{-b}{2a} \pm i \frac{\sqrt{|D|}}{2a}$$

#### 🧪 Test di Verifica

Verificare l'implementazione con i seguenti coefficienti:

  - **$D > 0$:** $a = 2, b = 5, c = 2 \to x_1 = -0.5, x_2 = -2.0$.
  - **$D = 0$:** $a = 4, b = -4, c = 1 \to x_{1,2} = 0.5$.
  - **$D < 0$:** $a = 1, b = 4, c = 5 \to x_1 = -2 + i, x_2 = -2 - i$.

-----

### 🆔 **Esercizio 3: Identificazione Studente con `switch`**

Utilizzare la struttura di controllo **`switch`** per stampare il nome di uno studente a partire dal suo numero di matricola.

1.  **Input Matricola:** Creare una variabile **`int`** per memorizzare il numero di matricola (solo parte numerica) e richiederne l'input da terminale.
2.  **`switch`:** Implementare una condizione **`switch`** sulla variabile di matricola.
      * **`case`:** Definire un `case` corrispondente al **vostro** numero di matricola che stampi il **vostro nome e cognome**.
      * **`default`:** Definire il caso **`default`** che stampi il messaggio di errore: `"Matricola non trovata. Riprovare."`.

-----

### 🚲 **Esercizio 4: Scelta Telaio Bicicletta**

Scrivere un programma in C++ che proponga la taglia ideale di telaio per una bicicletta (**XS, S, M, L, XL**) in base a una serie di criteri complessi che tengono conto di **età**, **altezza** (in metri) e **peso** (in kg) dell'atleta. Tutti e tre i dati devono essere introdotti dall'utente.

Implementare le condizioni utilizzando esclusivamente le strutture di selezione annidate e concatenate **`if`**, **`else if`**, **`else`**.

#### Criteri di Selezione

1.  **👶 Minore o uguale a 10 anni:** $\to \text{XS}$
2.  **🧑‍🦱 Tra 10 e 18 anni (compresi):**
      * Altezza $\le 1.10\text{m}: \to \text{XS}$
      * Altezza $\in (1.10\text{m}, 1.30\text{m}]$ **e** Peso $\le 40\text{kg}: \to \text{S}$
      * Altezza $\in (1.10\text{m}, 1.30\text{m}]$ **e** Peso $> 40\text{kg}: \to \text{M}$
      * Altezza $\in (1.30\text{m}, 1.60\text{m}]: \to \text{M}$
      * Altezza $> 1.60\text{m}: \to \text{L}$
3.  **👤 Più di 18 anni:**
      * Altezza $\le 1.40\text{m}$ **oppure** Peso $\le 40\text{kg}: \to \text{XS}$
      * Altezza $\in (1.40\text{m}, 1.60\text{m}]: \to \text{S}$
      * Altezza $\in (1.60\text{m}, 1.70\text{m}]: \to \text{M}$
      * Altezza $\in (1.70\text{m}, 1.90\text{m}]: \to \text{L}$
      * Altezza $> 1.90\text{m}: \to \text{XL}$

-----

### 🧠 Esercizi Opzionali per l'approfondimento

Per consolidare ulteriormente la comprensione delle strutture di controllo, si propongono i seguenti esercizi opzionali:

1. **Calcolatrice Semplice con `switch`**

    Ampliare la logica dell'**Esercizio 3** creando una semplice calcolatrice che esegua una delle quattro operazioni aritmetiche fondamentali (**+, -, \*, /**) su due numeri inseriti dall'utente, utilizzando la struttura **`switch`** per selezionare l'operazione.

    1.  Richiedere due operandi (**`double`**).
    2.  Richiedere all'utente di selezionare l'operazione (es. `+`, `-`, `*`, `/`) come carattere (**`char`**).
    3.  Utilizzare uno **`switch`** sul carattere dell'operazione.
    4.  Gestire il caso di **divisione per zero** (`/`) all'interno del `case` corrispondente, stampando un messaggio di errore.
    5.  Il `default` dovrà gestire operazioni non valide.

2. **Anno Bisestile**

    Scrivere un programma che, dato un anno (variabile **`int`**) inserito dall'utente, determini se tale anno sia **bisestile** o meno, utilizzando la struttura **`if/else`**.

    Un anno è bisestile se:

    1.  È **divisibile per 400**.
    2.  Oppure, è **divisibile per 4** ma **NON è divisibile per 100**.

    Utilizzare l'operatore **modulo** (`%`) per verificare la divisibilità.
