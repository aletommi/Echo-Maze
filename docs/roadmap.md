# Roadmap di Sviluppo — Echo Maze (Versione Phaser.js + Lobby Multiplayer)

---

# 🧱 FASE 1 — Setup del Progetto
## 1.1 Struttura del repository
- Cartella **client/**
- Cartella **server/**
- Cartella **shared/**
- Cartella **docs/** → file .md

## 1.2 Configurazione Phaser.js
- Setup scena principale
- Configurazione Canvas
- Setup fisica Arcade
- Gestione camera multipla

## 1.3 Setup server
- Avvio server Node.js
- Integrazione WebSocket (ws o socket.io)
- Gestione connessioni giocatori

---

# 🧩 FASE 2 — Sistema Lobby & Matchmaking
## 2.1 Schermata iniziale
- Pulsante **Crea partita**
- Pulsante **Entra nella partita**

## 2.2 Creazione della partita
- Generazione codice partita alfanumerico (es. 8 caratteri)
- Registrazione stanza nel backend
- Attesa secondo giocatore

## 2.3 Unione alla partita
- Inserimento codice
- Validazione stanza
- Sync stato partita

## 2.4 Avvio del gioco
- Transizione alla scena Phaser principale quando entrambi sono pronti

---

# 🎮 FASE 3 — Movimento e Telecamere
## 3.1 Movimento pipistrelli
- Input WASD / Frecce
- Velocità costante
- Collisioni automatiche tramite Arcade Physics

## 3.2 Telecamere indipendenti
Ogni giocatore:
- vede solo la propria telecamera
- segue il proprio pipistrello
- mantiene un piccolo cerchio di luce attorno a sé

## 3.3 Sincronizzazione multiplayer
- invio posizione giocatore → server → altro client
- gestione lag e smoothing

---

# 🔊 FASE 4 — Sistema di Ping Sonoro (Phaser)

- **Vedere file ping.md per i dettagli.**

---

# 🗺️ FASE 5 - Tipologie di Stanze

- **Vedere mapGeneration.md (FASE 4) per i dettagli.**

# 🗺️ FASE 6 — Generazione Procedurale (Server-side)
## 6.1 Generazione labirinto
- algoritmo (DFS, Prim, Eller)
- generazione server → invio mappa ai client

## 6.2 Materiali acustici
- associazione materiale a ogni cella

## 6.3 Zones mute & camere
- aggiunta aree di assorbimento
- camere grandi per eco multiplo

---

# 👾 FASE 7 — Mostri e Trappole

- **Vedere file monster.md e traps.md per i dettagli.**
- Implementazione IA e sincronizzazione stato lato server.
- Rendering visivo (visibili solo se colpiti dal ping).

---

# 🧩 FASE 8 — Puzzle Sonori

- **Vedere gameplay.md (Sezione 11) e levels.md (Livello 5) per i dettagli.**
- Implementazione delle meccaniche di attivazione (Porte Acustiche, ecc.).

# 🏞️ FASE 9 — Creazione dei 5 Livelli

- **Vedere file levels.md per la progressione e i dettagli.**
- Configurazione dei parametri variabili per ogni livello (dimensioni, materiali, mostri, trappole).
---

# 🖥️ FASE 10 — Backend Avanzato
## 10.1 Sistema utenti
- registrazione
- login
- salvataggio statistiche

## 10.2 Leaderboard
- tempo completamento
- morti
- tentativi

## 10.3 Gestione partite
- cleanup stanze
- gestione disconnessioni

---

# 🎨 FASE 11 — Effetti Grafici & Audio
## 11.1 Effetti grafici Phaser
- shader per eco
- dissolvenza muri
- risonanza potenziata

## 11.2 Effetti audio
- ping
- rimbalzi
- ambiente caverna

---

# 🚀 FASE 12 — Polishing & Ottimizzazioni
## 12.1 Bilanciamento
- difficoltà mostri
- durata ping
- densità trappole

## 12.2 Performance
- batching grafico
- ottimizzazione onde
- riduzione traffico WebSocket

## 12.3 QA & bugfix

---

# 🎯 Conclusione
Questa roadmap aggiornata definisce un percorso chiaro per sviluppare Echo Maze usando **Phaser.js**, con multiplayer cooperativo, lobby con codice partita e telecamere indipendenti per ciascun giocatore. Ogni fase è modulare e può essere implementata in ordine, mantenendo l'MVP chiaro e scalabile.