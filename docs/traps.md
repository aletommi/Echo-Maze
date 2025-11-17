# TRAPS.md — Trappole di Echo Maze

Questo documento definisce le trappole presenti in **Echo Maze**. Ogni trappola interagisce direttamente con le meccaniche sonore del gioco, modificando il comportamento dei giocatori e dei mostri.

Le trappole sono pensate per:
- aggiungere tensione
- creare momenti di puzzle
- aumentare la complessità dei livelli
- sfruttare l'ecolocalizzazione come elemento di rischio

---

# 💣 1. Mine Sonore

### **Descrizione**
Piccoli dispositivi nascosti nel pavimento. Non esplodono al contatto, ma **solo quando vengono colpite da un ping**.

### **Attivazione**
- Se un'onda sonora le raggiunge, la mina esplode.
- L'esplosione genera un suono fortissimo.
- L'esplosione illumina brevemente la zona.

### **Effetti**
- infligge danno ai giocatori vicini
- attira mostri in un ampio raggio
- può essere usata strategicamente per:
  - eliminare Listener
  - distrarre Screamer
  - respingere Stalker

### **Note di Design**
Le mine aumentano il rischio del ping. I giocatori devono essere precisi e consapevoli.

---

# 🔔 2. Campanelli

### **Descrizione**
Piccoli oggetti appesi al soffitto o alle pareti. Quando colpiti da un ping, emettono un suono metallico amplificato.

### **Attivazione**
- il suono si genera solo se colpiti dal ping
- il rimbombo può essere molto lungo in stanze con materiali risonanti (Metallo, Cristalli)

### **Effetti**
- attirano i mostri circostanti **verso il campanello**
- possono essere usati per creare trappole invertite (depistaggi)
- lo Stalker risponde poco, lo Screamer e il Listener molto

### **Note di Design**
I campanelli trasformano il ping in una mossa tattica. I giocatori possono creare percorsi falsi.

---

# 🚪 3. Barriere Acustiche

### **Descrizione**
Cancelli o pareti sottili che rispondono al suono. Si aprono o chiudono a seconda del tipo di ping ricevuto.

### **Attivazione**
- **Ping singolo:** apre la barriera per pochi secondi
- **Ping potenziato a due giocatori:** apre la barriera più a lungo
- alcuni livelli prevedono barriere che **si chiudono** invece di aprirsi

### **Effetti**
- possono bloccare passaggi cruciali
- obbligano i due giocatori a coordinarsi
- possono intrappolare o liberare mostri

### **Note di Design**
Le barriere acustiche introducono puzzle cooperativi e aumentano la profondità della navigazione.

---

# ⛔ 4. Zone Anti-Eco

### **Descrizione**
Zone ricoperte da **materiale morto**, completamente insonorizzato. L'eco si spegne istantaneamente al contatto.

### **Attivazione**
- nessuna attivazione: è una proprietà passiva dell'area
- il ping sparisce non appena entra nella zona

### **Effetti**
- i giocatori perdono completamente la visione generata dall'eco
- i mostri possono nascondersi perfettamente al suo interno
- può bloccare l'uso del ping potenziato

### **Note di Design**
Le zone anti-eco sono spazi di puro terrore: il buio è totale.

---

# ✔ Conclusione
Queste trappole creano un ecosistema sonoro complesso, che incoraggia strategia, cooperazione e una comprensione profonda dell'ambiente.