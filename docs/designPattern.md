# DESIGN_PATTERNS.md — Pattern Obbligatori per Echo Maze

Questo documento elenca e descrive i **design pattern obbligatori** per garantire una struttura pulita, scalabile e gestibile per lo sviluppo di **Echo Maze**, specialmente considerando:
- multiplayer realtime
- effetti acustici complessi
- IA dei mostri
- gestione stanze/trappole
- Phaser.js come game engine

Solo i pattern essenziali sono inclusi.

---

# 🎯 1. State Pattern (Obbligatorio)
Gestisce gli stati complessi e variabili di molte entità del gioco.

## Dove si usa
- IA dei mostri:
  - Screamer → Idle / SeePlayer / Screaming / Chasing
  - Listener → Idle / Triggered / Charging / Returning
  - Stalker → Hidden / Following / Frozen / Retreating
- Giocatori: Idle / Moving / Pinging / Stunned
- Trappole: Inactive / Triggered / Cooldown
- Porte acustiche: Open / Closing / Closed

## Perché è obbligatorio
Senza una macchina a stati, i comportamenti diventano incontrollabili e poco leggibili. Serve per evitare spaghetti code e per rendere la IA modificabile.

---

# 🔔 2. Observer / Pub-Sub Pattern (Obbligatorio)
Gestisce tutti gli eventi asincroni del gioco.

## Dove si usa
- il ping che notifica:
  - mostri
  - trappole
  - materiali acustici
  - effetti grafici
- aggiornamento HUD
- timer
- sincronizzazione multiplayer lato client

## Perché è obbligatorio
Il gioco è fortemente basato sugli **eventi sonori**, quindi serve un sistema reattivo e flessibile che permetta a molti elementi di rispondere allo stesso evento senza dipendere gli uni dagli altri.

---

# 🏭 3. Factory Pattern (Obbligatorio)
Gestisce la creazione di oggetti complessi in modo centralizzato e coerente.

## Dove si usa
- Mostri (Screamer, Listener, Stalker)
- Trappole
- Stanze speciali
- Materiali acustici
- Oggetti della mappa generati proceduralmente

## Perché è obbligatorio
Il generatore procedurale deve creare entità molto diverse in base al livello e al template. Con una Factory puoi mantenere la logica centralizzata e semplificare il testing.

---

# 🌐 4. Authoritative Server Pattern (Obbligatorio)
Il server ha il controllo totale sullo stato del gioco.

## Funzioni del server
- calcolo movimenti reali
- IA dei mostri
- attivazione trappole
- gestione collisioni
- validazione ping
- sincronizzazione tra i due giocatori

## Perché è obbligatorio
Evita hack, desync e comportamenti inconsistenti. I client diventano solo un renderer grafico.

---

# 🧳 5. DTO (Data Transfer Object) Pattern (Obbligatorio)
Serve per definire i formati dei messaggi scambiati tra client e server.

## Dove si usa
- lobby (create, join, ready, start)
- sincronizzazione player
- invio eventi di ping
- aggiornamento mostri
- invio della mappa generata

## Perché è obbligatorio
Garantisce coerenza nei messaggi, evita payload inutili e permette un networking pulito e scalabile.

---

# 🧱 6. Object Pooling (Obbligatorio)
Gestisce oggetti istanziati molto frequentemente.

## Dove si usa
- onde/ping (molti cerchi generati al secondo)
- particelle di eco
- effetti grafici temporanei
- esplosioni delle mine

## Perché è obbligatorio
Phaser.js non gestisce bene la creazione/distruzione continua di centinaia di oggetti. Il pooling aumenta enormemente le performance.

---

# 🎬 7. Scene Manager (Obbligatorio)
Phaser usa le Scene, ma è necessario strutturarle con un pattern chiaro.

## Scene fondamentali
- LobbyScene
- LoadingScene
- LevelScene
- UIScene
- ScoreScene

## Perché è obbligatorio
Organizzare correttamente il flusso delle schermate previene bug, mantiene ordine e rende espandibile il progetto.

---

# ✔ Conclusione
Questi design pattern costituiscono l’ossatura architetturale minima per sviluppare Echo Maze in modo solido e professionale. Sono indispensabili per:
- mantenere il codice pulito
- gestire IA e complessità acustiche
- evitare problemi di performance
- garantire un multiplayer stabile

Senza di essi, il progetto diventerebbe fragile, difficile da debuggare e impossibile da scalare.