# Levels

Questo documento descrive in dettaglio la struttura, la generazione e la progressione dei cinque livelli di **Echo Maze**. Ogni livello presenta variazioni nella dimensione della mappa, nei materiali acustici, nei pericoli e nelle meccaniche richieste ai giocatori.

---

# 🗺️ 1. Struttura Generale dei Livelli
Ogni livello è composto da:
- una **mappa generata proceduralmente**
- materiali acustici differenti
- trappole e mostri distribuiti con logiche specifiche
- un **punto di uscita** da raggiungere

La difficoltà aumenta in modo progressivo attraverso:
- mappa più grande
- eco più complessa
- nemici più aggressivi
- presenza di zone che assorbono il suono
- puzzle sonori più elaborati

---

# 🎚️ 2. Parametri Configurabili
Ogni livello può modificare:
- **dimensioni mappa** (larghezza, altezza)
- **densità dei corridoi**
- **percentuale dei diversi materiali acustici**
- **numero e tipo di mostri**
- **numero e tipo di trappole**
- **posizione delle zone anti-eco**
- **frequenza di apparizione delle camere grandi** (che generano echi multipli)
- **intensità massima del ping** per quel livello

Questi parametri consentono di creare facilmente nuovi livelli o modalità extra.

---

# 🧱 3. Materiali Acustici nei Livelli
Ogni livello include almeno 2 materiali acustici. Dal terzo livello in poi compaiono tutti.

| Livello | Materiali principali | Note |
|---------|----------------------|------|
| 1 | Calcare, Basalto | eco semplice, assorbimento moderato |
| 2 | Calcare, Metallo | rimbalzi più forti, prime deviazioni complesse |
| 3 | Metallo, Cristalli | echi multipli, maggiore difficoltà di lettura |
| 4 | Cristalli, Sabbia | zone mute, eco irregolare |
| 5 | Tutti | massima complessità acustica |

---

# 🧩 4. Dettaglio dei 5 Livelli

## **Livello 1 — "La Caverna delle Origini"**
- **Dimensioni**: piccole
- **Obiettivo**: introdurre movimento e ping
- **Pericoli**: nessuno
- **Materiali**: basalto e calcare
- **Trappole**: nessuna
- **Note**: ideale per insegnare ai giocatori come funziona l'eco

---

## **Livello 2 — "La Galleria Risonante"**
- **Dimensioni**: medie
- **Obiettivo**: imparare a usare l'eco potenziata
- **Pericoli**: primi mostri semplici (Cieco)
- **Materiali**: calcare e metallo
- **Trappole**: campanelli acustici
- **Note**: introduce rimbalzi sonori più complessi

---

## **Livello 3 — "Il Labirinto Vibrante"**
- **Dimensioni**: grandi
- **Obiettivo**: gestire mostri sensibili al suono
- **Pericoli**: Stalker, Cieco
- **Materiali**: metallo e cristalli
- **Trappole**: mine sonore
- **Note**: gli echi multipli rendono difficile memorizzare il percorso

---

## **Livello 4 — "Le Camere Silenziose"**
- **Dimensioni**: molto grandi
- **Obiettivo**: gestire zone che assorbono l'eco
- **Pericoli**: tutti i mostri
- **Materiali**: cristalli e sabbia
- **Trappole**: barriere acustiche
- **Note**: presenza di aree completamente mute

---

## **Livello 5 — "Il Nucleo Oscuro"**
- **Dimensioni**: enormi
- **Obiettivo**: completare puzzle sonori complessi
- **Pericoli**: combinazioni di tutti i mostri e trappole
- **Materiali**: tutti
- **Trappole**: tutte
- **Note**: progettato per la massima cooperazione possibile

---

# 🔧 5. Generazione Procedurale del Labirinto
Ogni livello usa un algoritmo di procedural generation (a scelta tra DFS Maze, Prim, Eller, ecc.) con modifiche per:
- generare camere grandi
- inserire zone mute
- distribuire materiali acustici
- generare corridoi stretti (effetto tunnel)
- creare percorsi alternativi

---

# 🏁 6. Uscita del Labirinto
L'uscita può essere:
- un portale
- una fenditura luminosa
- un varco acustico attivabile con ping potenziato

Appare sempre in una zona relativamente sicura.

---

# 🎯 7. Obiettivo della Progressione
Completando tutti i livelli, i giocatori dimostrano:
- padronanza dell'eco
- capacità di cooperare
- comprensione dei materiali acustici
- gestione dei mostri
- memorizzazione spaziale senza luce

Il design dei livelli costruisce queste competenze in modo naturale.