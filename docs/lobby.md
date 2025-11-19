# LOBBY.md — Sistema di Lobby di Echo Maze

Questo documento descrive il funzionamento completo della **lobby multiplayer** di Echo Maze, incluse:
- creazione della partita
- join tramite codice
- gestione partecipanti
- sistema di "Pronto"
- permesso per l'host di avviare la partita
- stile dell’interfaccia

La lobby è progettata per essere semplice, pulita e coerente con l’estetica scura e luminosa del gioco.

---

# 🎮 1. Interfaccia iniziale della Lobby
Quando un giocatore entra nella lobby (prima di creare o unirsi a una partita) vede:

- **Bottone: CREA PARTITA**
- **Input: Inserisci codice partita**
- **Bottone: PARTECIPA** (vicino all'input)

### ⚫ Stile
La pagina ha uno stile **scuro**, quasi completamente al buio.
- I pulsanti emettono un **alone luminoso** al passaggio del mouse.
- Il cursore illumina leggermente l’area attorno ad esso.
- Gli input hanno bordi che reagiscono alla tipografia.

---

# 🆕 2. Creazione di una Partita
Quando l'utente preme **CREA PARTITA**:

1. I pulsanti **CREA PARTITA** e **PARTECIPA** scompaiono.
2. Viene generato un **codice di lobby**:
   - 8 caratteri
   - alfanumerico (A–Z, a–z, 0–9)
   - nessun simbolo speciale
3. Compare:
   - Il codice partita ben visibile
   - La lista dei partecipanti (massimo 2)
   - Il pulsante **ESCI DALLA PARTITA**
   - Il pulsante **PRONTO** (per l'host stesso)

L'host occupa automaticamente il primo slot della lista.

---

# 👥 3. Partecipazione a una Partita
Il secondo giocatore inserisce il codice e preme **PARTECIPA**.

Se la lobby esiste e non è piena:
- entra nella partita
- appare nella lista dei partecipanti
- gli viene mostrato il pulsante **ESCI DALLA PARTITA**
- compare anche il pulsante **PRONTO**

Se la lobby è piena o non esiste → errore visuale (rosso luminoso).

---

# 📜 4. Lista Partecipanti
Mostra massimo **2 giocatori**:

```
[HOST] Giocatore 1 — Stato: (Pronto / Non pronto)
Giocatore 2 — Stato: (Pronto / Non pronto)
```

Gli stati si aggiornano in tempo reale.

---

# ✔ 5. Sistema di "Pronto"
Ogni giocatore ha un pulsante **PRONTO**.

Quando un giocatore preme "PRONTO":
- il suo nome si illumina in verde
- l’altro giocatore vede subito il cambiamento
- il pulsante diventa "NON PRONTO"

### Regole
- la partita **non può partire finché entrambi non sono pronti**
- solo l’**host** vede il pulsante: **AVVIA PARTITA**

---

# 🚀 6. Avvio della Partita
Quando entrambi i giocatori sono "Pronti":
- l’host può cliccare **AVVIA PARTITA**
- la lobby si blocca
- viene inviato al server il comando per iniziare il livello
- entrambi i giocatori vengono portati alla scena di gioco

---

# 🚪 7. Uscita dalla Lobby
Il pulsante **ESCI DALLA PARTITA**:
- permette di abbandonare la lobby
- se lascia l’host → la lobby si scioglie
- se lascia il secondo giocatore → la lobby resta attiva

Entrambi tornano alla schermata iniziale della lobby.

---

# ✨ 8. Stile Visivo (dettagliato)
La lobby adotta lo **stile buio e minimale** tipico del gioco.

### Illuminazione dinamica
- Attorno al cursore c’è una luce tenue.
- I pulsanti hanno bordi luminosi che reagiscono al movimento del mouse.
- Il testo dei pulsanti si illumina brevemente al click.

### Feedback visivi
- errori in rosso (alone pulsante)
- stato "Pronto" in verde neon
- stato "Non pronto" in arancione

### Font consigliati
- Monospace futuristico / minimal
- Colori: bianco, grigio chiaro, verde neon

---

# ✔ Conclusione
La lobby è semplice, intuitiva e coerente con l’estetica di Echo Maze. Permette a due giocatori di coordinarsi velocemente e prepara al gameplay cooperativo che segue.