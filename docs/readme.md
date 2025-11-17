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
- **Ping potenziato**: se i due pipistrelli pingano insieme, l'eco è più intensa e duratura.
- **Visione limitata**: i giocatori vedono solo una piccola area attorno a loro.
- **Materiali acustici diversi**: ogni parete reagisce al suono in modo unico (basalto, cristalli, metallo, sabbia, ecc.).

## 📦 Struttura del progetto
Il progetto è suddiviso in vari file di documentazione:
- **README.md** – introduzione generale e panoramica del progetto.
- **GAMEPLAY.md** – descrizione dettagliata delle meccaniche di gioco.
- **LEVELS.md** – progettazione, struttura e caratteristiche dei livelli.


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