# 🗺️ Tipologie di Stanze

Questo documento definisce i *template* di stanza che il generatore di labirinti (`mapGeneration.md`) utilizza per comporre i livelli. Ogni template ha uno scopo, dimensioni e un set di regole specifiche.

---

## 1. Stanze Base

Questi sono gli elementi costruttivi fondamentali del labirinto.

### 1.1 Stanza Normale
* **Descrizione:** Le stanze più comuni che compongono la maggior parte del labirinto e fungono da "tessuto connettivo".
* **Dimensioni:** Variabili (piccole, medie, grandi).
* **Contenuto (Trappole):** Contengono solo trappole. La densità e il tipo dipendono dai parametri del livello.
* **Materiali Acustici:** Misti, in base alla configurazione del livello.

### 1.2 Corridoio
* **Descrizione:** Passaggi stretti che collegano stanze più grandi.
* **Dimensioni:** **Altezza fissa di 3 tile**, lunghezza variabile.
* **Contenuto (Trappole):** Hanno una probabilità specifica (es. 30%) di contenere trappole (specialmente Mine Sonore).
* **Materiali Acustici:** Spesso usano materiali con eco forte (Metallo, Cristalli) per creare un "effetto tunnel" sonoro, rendendo difficile capire cosa c'è alla fine.
* **Note di Design:** Creano tensione. Il ping direzionale (40°) rimbalza molto ma illumina poco.

---

## 2. Stanze Tematiche (Mostri)

Queste sono stanze speciali, generate con uno scopo preciso e popolate con incontri pre-configurati. Le loro versioni (Light, Normale, Hard/Extreme) vengono utilizzate in base al livello, come definito in `mapGeneration.md`.

### 🟣 Stanza del Listener — 3 versioni
* **Light (L2):** area larga, 1 Listener, materiali morbidi (Calcare).
* **Normale (L3):** passaggi più stretti, 2–3 Listener, ostacoli sonori.
* **Hard/Extreme (L4–L5):** molti Listener, zone mute strategiche, passaggi strettissimi.
* **Note di Design:** Progettata per punire l'uso sconsiderato del ping.

### 🔵 Stanza dello Stalker — 3 versioni
* **Light (L3):** 1 Stalker, pochi campanelli, stanza media.
* **Hard (L4):** 2–3 Stalker, design complesso, molte zone cieche.
* **Extreme (L5):** stanze enormi, 3–4 Stalker, percorsi intricati.
* **Note di Design:** Progettata per creare paranoia e testare la consapevolezza spaziale e cooperativa (guardarsi le spalle).

### 🟠 Stanza del Screamer — 3 versioni
* **Light (L3):** 1 Screamer, stanza aperta.
* **Hard (L4):** 1–2 Screamer, corridoi lunghi e linee di vista estese.
* **Extreme (L5):** stanze gigantesche con urli continui e illuminazioni frequenti.
* **Note di Design:** Progettata per testare la gestione delle linee di vista e creare panico (l'urlo rivela la mappa ma attira altri pericoli).

---

## 3. Aree Speciali (Puzzle e Ostacoli)

Queste aree sono definite da proprietà acustiche uniche e spesso contengono puzzle.

### 3.1 Zona Muta (Anti-Eco)
* **Descrizione:** Aree coperte di **Materiale Morto**.
* **Effetto:** Il ping si spegne istantaneamente al contatto. I giocatori e i mostri all'interno sono completamente invisibili all'ecolocalizzazione.
* **Posizionamento:** Spesso in cluster (4x4 o 5x5 tile) o usate strategicamente nelle stanze dei mostri (es. Stanza Listener Hard).

### 3.2 Stanza Puzzle (Porta Acustica)
* **Descrizione:** Una stanza, spesso piccola, che contiene una **Barriera Acustica** o una porta bloccata.
* **Meccanica:** Richiede un'azione sonora specifica per essere aperta.
* **Attivazione:**
    * **Ping Singolo:** Apre la barriera per pochi secondi.
    * **Ping Potenziato:** Apre la barriera più a lungo.
* **Note di Design:** Funziona come un "gate" che testa la padronanza delle meccaniche di ping e la cooperazione.

### 3.3 Camera di Risonanza
* **Descrizione:** Una stanza, tipicamente grande, costruita quasi interamente con **Cristalli** e **Metallo**.
* **Effetto:** Genera echi multipli, rimbalzi caotici e un'eco molto lunga.
* **Note di Design:** L'enigma non è un meccanismo, ma l'orientamento stesso. È difficile capire da dove provenga un suono o dove sia un muro, creando confusione.