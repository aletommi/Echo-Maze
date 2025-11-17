# MONSTERS.md — Mostri di Echo Maze

Questo documento definisce i tre mostri principali presenti in **Echo Maze**, insieme al loro comportamento, le loro abilità e le regole di interazione con i giocatori.

I mostri sono progettati per sfruttare le meccaniche di buio, suono ed ecolocalizzazione, creando tensione e interazioni uniche.

---

# 👁️‍🗨️ 1. Il Veggente ("The Screamer")

### **Descrizione Generale**
Creatura silenziosa ma dotata di un potentissimo senso della vista nel buio totale. Quando individua uno dei due pipistrelli emette un **urlo accecante-sonoro** che illumina l'intera mappa per un breve istante, rivelando tutti i muri, stanza dopo stanza.

### **Comportamento**
- Rimane fermo e vigila la sua zona.
- Ha un **campo visivo ampio** e vede i giocatori anche nel buio.
- Se vede un giocatore:
  - emette un **urlo luminoso** → illumina l'intera mappa per 0,5–1s.
  - lancia l'allarme ai mostri vicini.
  - inizia a **correre verso il giocatore** finché non lo perde di vista.

### **Come si evita**
- evitare linee di vista dirette
- usare l'ombra dei corridoi
- pingare dietro gli angoli per capire dov'è

### **Note di Design**
Il Veggente insegna ai giocatori a gestire **linee di vista** e crea momenti di panico.

---

# 👂 2. Il Cieco ("The Listener")

### **Descrizione Generale**
Un mostro completamente cieco che percepisce solo il suono. Rimane completamente immobile e passivo finché non sente un rumore diretto.

### **Comportamento**
- Non si muove mai finché non sente un suono.
- Se un ping lo colpisce:
  - individua la posizione del ping
  - corre **esattamente nella direzione da cui è partito il ping**
  - continua finché non sbatte contro un muro o raggiunge la posizione stimata
- Dopo aver corso, ritorna lentamente alla posizione iniziale.

### **Come si evita**
- non pingarlo direttamente
- attirarlo intenzionalmente verso corridoi ciechi
- usare il ping potenziato sincronizzato per controllare la sua direzione

### **Note di Design**
Il Cieco è un mostro puzzle: obbliga a ragionare **prima di pingare**.

---

# 🕵️‍♂️ 3. Lo Stalker

### **Descrizione Generale**
Creatura sottile, rapida e silenziosa. Segue i giocatori nel buio quando non viene osservato. Se riesce a toccare un giocatore, lo trascina immediatamente nella sua "stanza nativa".

### **Comportamento**
- segue i giocatori solo quando **non lo stanno guardando**.
- se osservato dalla luce del giocatore:
  - si immobilizza
  - indietreggia lentamente
- se riesce a toccare un giocatore:
  - teletrasporta il giocatore nella sua stanza
  - scompare e torna alla stanza stessa

### **Come si scaccia**
Quando individuato:
- i giocatori devono eseguire **una serie di ping diretti verso di lui** (2–4 ping)
- il mostro si spaventa e corre da solo verso la sua tana

### **Note di Design**
Lo Stalker introduce meccaniche di:
- paranoia nel buio
- controllo dello spazio
- cooperazione tra i giocatori per tenerlo d'occhio

---

# 🧠 Interazioni Comuni tra Mostri
- tutti i mostri possono essere rivelati dal **ping**
- tutti i mostri ritornano alla loro "stanza nativa" dopo aver perso il giocatore
- i materiali acustici influenzano come i ping rivelano i mostri
- il Veggente può accidentalmente attivare il Cieco tramite il suo urlo

---

# ✔ Conclusione
Questi tre mostri coprono tre stili diversi di pericolo:
- **visivo** (Veggente)
- **sonoro** (Cieco)
- **stealth** (Stalker)

Creano una progressione ricca, varia e basata sulle meccaniche audio-visive del gioco.