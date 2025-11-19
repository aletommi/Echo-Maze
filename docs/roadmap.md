# 🗺️ Roadmap di Sviluppo — Echo Maze (8 Fasi)

Questa roadmap guida lo sviluppo del gioco step-by-step, strutturando la sequenza di implementazione in 8 fasi modulari.

**Stack Tecnologico:**
* **Frontend:** React (UI/Menu) + Phaser.js (Game Canvas).
* **Backend:** Next.js (API/Auth) + Node.js Custom Server (WebSocket/Game Loop).
* **Comunicazione:** Socket.io (per la gestione stanze e sync in tempo reale).

---

# 🧱 FASE 1 — Infrastruttura & Lobby System
**Obiettivo:** Creare la connessione tra due giocatori e l'interfaccia pre-partita.

### 1.1 Setup Ambiente
* Configurare l'architettura per ospitare React/Phaser (Client) e Node.js/Socket.io (Server).
* Installare e configurare Phaser.js all'interno del client React.

### 1.2 Logica di Lobby
* Implementare logica `createRoom` / `joinRoom` con generazione di codice alfanumerico a 8 caratteri.
* Gestire la connessione e disconnessione di massimo 2 giocatori.

### 1.3 Interfaccia Lobby (React)
* Creare interfaccia in stile **scuro e minimale**.
* Implementare il sistema di **Stato "Pronto" / "Non Pronto"**.
* Implementare il pulsante **"Avvia Partita"** (visibile solo all'Host quando entrambi sono pronti).

---

# 🗺️ FASE 2 — Generazione Mappa Procedurale
**Obiettivo:** Il server genera il labirinto e il client lo disegna.

### 2.1 Algoritmo Server-Side
* Implementare algoritmo di generazione (DFS o Prim).
* **Materiali Acustici:** Assegnare materiali (Metallo, Sabbia, Cristallo) ai tile in base ai parametri del livello.

### 2.2 Rendering Client (Phaser)
* Ricevere il JSON della mappa dal server.
* Implementare il rendering del `Tilemap` in Phaser per disegnare muri e pavimenti.
* Assegnare proprietà di collisione ai muri (Arcade Physics).

---

# 🦇 FASE 3 — Personaggi & Sincronizzazione
**Obiettivo:** I giocatori si muovono nel labirinto e si vedono a vicenda.

### 3.1 Movimento Locale
* Implementare input WASD / Frecce.
* Implementare la collisione del pipistrello con i muri del `Tilemap`.
* Implementare l'**aura di luce** attorno al pipistrello (visione base).

### 3.2 Sincronizzazione Multiplayer
* **Server Authority:** Il server riceve e trasmette gli aggiornamenti di posizione (x, y).
* **Client Prediction/Interpolation:** Implementare tecniche per rendere fluido il movimento del compagno.

---

# 🔊 FASE 4 — Il Sistema di Ping (Core Mechanic)
**Obiettivo:** Implementare l'ecolocalizzazione e la meccanica cooperativa principale.
*(Riferimento: `ping.md`)*

### 4.1 Ping Base (Raycasting)
* Implementare la logica del **cono di 40 gradi** direzionale.
* Eseguire Raycasting per rilevare l'impatto sui muri.
* **Effetto Visivo:** Illuminare il tile colpito + **5 tile adiacenti** ("splash").
* Implementare logica di **rimbalzo** (angolo di riflessione) con degrado dell'intensità.

### 4.2 Ping Potenziato (Co-op)
* **Attivazione:** Rilevare la **collisione fisica** tra i due coni di 40 gradi dei giocatori.
* **Effetto:** Generare una **"Super-Eco"** circolare con raggio e intensità maggiori.

---

# 👾 FASE 5 — Mostri & Intelligenza Artificiale
**Obiettivo:** Introdurre i pericoli che reagiscono al suono.
*(Riferimento: `monster.md`)*

### 5.1 Implementazione AI (Server)
* Definire lo stato dei mostri sul server (posizione, stato Alert/Idle).
* Implementare le regole di visibilità: i mostri sono visibili solo se colpiti dal ping.

### 5.2 Comportamento Mostri
* **Listener (Cieco):** Implementare logica di Pathfinding verso l'origine del ping.
* **Stalker:** Implementare la logica "non osservato" (segue i giocatori se non visti dalla loro aura di luce).
* **Screamer (Veggente):** Implementare l'urlo come funzione che illumina la mappa (globale) e allerta gli altri mostri.

---

# 💣 FASE 6 — Trappole & Elementi Interattivi
**Obiettivo:** Implementare gli ostacoli statici e i puzzle.
*(Riferimento: `traps.md`)*

### 6.1 Sistema Trigger
* **Mine Sonore:** Implementare il trigger di esplosione al contatto con l'onda del ping.
* **Campanelli:** Trigger sonoro che attira i mostri circostanti.

### 6.2 Elementi Puzzle
* **Barriere Acustiche:** Implementare il cambio di stato (aperto/chiuso) in base al tipo di ping (singolo vs. potenziato).
* **Zone Anti-Eco:** Definire queste aree in modo che il ping venga annullato istantaneamente al contatto.

---

# 🏆 FASE 7 — Loop di Gioco e Livelli
**Obiettivo:** Creare un flusso di gioco completo e tracciare le performance.
*(Riferimento: `levels.md`)*

### 7.1 Gestione Partita
* Implementare un **Timer Ufficiale** (lato server).
* Implementare la logica per la transizione tra i **5 Livelli**.
* Definire le condizioni di vittoria (raggiungimento dell'uscita) e sconfitta (Game Over).

### 7.2 Backend & Leaderboard
* Implementare il salvataggio delle statistiche post-partita (tempo totale, ping usati, trappole attivate).
* Configurare il database PostgreSQL per la **Leaderboard** (Next.js API).

---

# 🎨 FASE 8 — Polish Audio & Visivo
**Obiettivo:** Ottimizzare l'esperienza utente e l'atmosfera.

### 8.1 Effetti Grafici
* Implementare shader in Phaser per l'effetto di **dissolvenza**.
* Creare l'effetto visivo del **bagliore neon** (verde) per lo stato di "Pronto".
* Ottimizzare il rendering del Tilemap per migliorare le performance.

### 8.2 Design Sonoro
* Implementare suoni per il ping, i rimbalzi e le trappole.
* Aggiungere audio d'ambiente per aumentare la tensione e l'immersività.