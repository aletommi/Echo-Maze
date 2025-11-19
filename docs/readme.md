# Echo Maze

Echo Maze è un gioco 2D cooperativo basato sull'ecolocalizzazione. Due pipistrelli meccanici si muovono in un labirinto completamente buio, rivelando l'ambiente tramite onde sonore ("ping") che illuminano le pareti solo per un breve istante. Il gioco unisce orientamento, cooperazione, tensione e strategia attraverso un sistema di eco realistico e materiali acustici diversi.

## 🎮 Caratteristiche principali
- **Cooperazione obbligatoria**: due giocatori esplorano insieme il labirinto e condividono le informazioni ottenute con il ping.
- **Generazione procedurale**: ogni livello è creato casualmente, rendendo ogni partita unica.
- **Ecolocalizzazione avanzata**: il ping illumina l'ambiente in base a materiali, rimbalzi e degradazione dell'onda.
- **Mostri sensibili al suono**: varie creature reagiscono al rumore, rendendo necessaria una gestione strategica del ping.
- **5 livelli scalabili**: dalla mappa piccola a labirinti enormi con trappole, zone di assorbimento e puzzle sonori.

## 🧩 Meccaniche di gioco
- **Ping semplice**: onda bianca che si propaga, rimbalza e svanisce.
- **Ping potenziato**: se i due pipistrelli pingano insieme, l'eco è più intensa e duratura (attivato dalla collisione fisica delle onde).
- **Visione limitata**: i giocatori vedono solo una piccola area attorno a loro.
- **Materiali acustici diversi**: ogni parete reagisce al suono in modo unico (basalto, cristalli, metallo, sabbia, ecc.).
- **Mostri Sonori**: varie creature (come il Listener, Stalker e Screamer) reagiscono al rumore, rendendo necessaria una gestione strategica del ping.
- **Trappole Acustiche**: ostacoli (mine, campanelli, barriere) che si attivano o reagiscono al suono del ping, aggiungendo rischio e complessità ai puzzle.

## 📦 Struttura del progetto
Il progetto è suddiviso in vari file di documentazione per mantenere la logica e il design ben separati:

* **readme.md** – Introduzione generale, panoramica del progetto e stack tecnologico.
* **roadmap.md** – Definisce le 8 fasi di implementazione e la strategia di sviluppo.
* **gameplay.md** – Descrizione dettagliata delle meccaniche di gioco, comandi e progressione della difficoltà.
* **ping.md** – Dettaglio tecnico del funzionamento del ping direzionale (40°) e della logica di collisione cooperativa.
* **mosnters.md** – Definisce il comportamento e le IA dei mostri (Listener, Stalker, Screamer).
* **traps.md** – Dettaglia l'attivazione e gli effetti delle trappole acustiche (Mine, Campanelli, Barriere).
* **rooms.md** – Definisce i *template* delle stanze (Normali, Corridoi, Tematiche) e le loro versioni (Light, Hard, Extreme).
* **mapGeneration.md** – Descrive l'algoritmo di generazione procedurale lato server, la segmentazione e l'assegnazione dei materiali.
* **levels.md** – Definisce la progressione dei 5 livelli, i parametri configurabili e gli obiettivi specifici.
* **lobby.md** – Dettaglia il design dell'interfaccia, la creazione della partita, la gestione del codice e il sistema di "Pronto".
* **designPatter.md** – Definisce i pattern architetturali obbligatori (State, Observer, Factory) per lo sviluppo professionale del gioco.


## 🖥️ Tecnologia utilizzata
Frontend (UI/Interfaccia): React (per la gestione della UI, delle lobby, dei menu e dell'HUD).

- **Game Engine**: Phaser.js (per il canvas di gioco, la fisica e il rendering del labirinto).

- **Backend**: NestJS (framework Node.js per la logica di business, le API e la gestione degli utenti).

- **Cooperativa online**: WebSockets (per la gestione delle stanze e la sincronizzazione in tempo reale).

- **Database**: PostgreSQL.

## 🚀 Futuri sviluppi
- Implementazione IA dei mostri e trappole.
- Sistemi di progressione più avanzati.
- Effetti grafici migliorati.
- Leaderboard globale.

## 📄 Licenza
Progetto sviluppato a scopo didattico e sperimentale.