# Algoritmo di Generazione del Labirinto — Echo Maze

Questo file descrive l’algoritmo completo per generare i labirinti di **Echo Maze**, includendo:
- generazione procedurale della struttura
- segmentazione delle zone
- template di stanze
- materiali acustici
- distribuzione di mostri e trappole
- particolarità per ogni livello

È pensato per una implementazione **server-side**, con output in formato JSON da inviare ai client Phaser.js.

---

# 🧩 FASE 1 — Generazione della Struttura Base
Si utilizza un algoritmo di generazione classico:
- **DFS Maze** (labirinto organico)
- **Prim** (più naturale e cavernoso)
- **Eller** (ottimo per grandi mappe)

**Output:** matrice di tile con muri e corridoi.

---

# 🗺️ FASE 2 — Segmentazione in Zone
La mappa viene divisa in zone tramite:
- flood-fill
- voronoi su griglia

Ogni zona diventa potenzialmente:
- stanza normale
- corridoio
- stanza mostro
- stanza tematica

---

# 🧱 FASE 3 — Materiali Acustici
Ogni stanza riceve 3 materiali:
- **70% dominante**
- **20% secondario A**
- **10% secondario B**

### Materiali disponibili
| Materiale | Effetto |
|-----------|---------|
| Basalto | assorbimento elevato, eco breve |
| Calcare | eco moderata |
| Cristalli | eco lunga e riflessioni multiple |
| Metallo | rimbalzi intensi, eco limpida |
| Sabbia | assorbe quasi totalmente |
| Materiale morto | cancella completamente il suono (zone mute) |

### Distribuzione per livello
- **Livello 1:** Calcare + Basalto
- **Livello 2:** Calcare + Metallo
- **Livello 3:** Metallo + Cristalli
- **Livello 4:** Cristalli + Sabbia + Zone mute
- **Livello 5:** Tutti i materiali miscelati

Zone mute sempre in cluster (4×4 o 5×5 tile).

---

# 👾 FASE 4 — Inserimento Stanze dei Mostri
### Quantità e difficoltà per livello (progressione bilanciata)

### Livello 1
* **Dimensioni Mappa:** Piccole.
* **Stanze Mostro:** Nessuna.
* **Focus Stanze:** Interamente composto da Stanze Normali e Corridoi per introdurre la meccanica del ping.

### Livello 2
* **Dimensioni Mappa:** Medie.
* **Stanze Mostro:** 1 stanza mostro **SEMPLICE**:
    * **Stanza del Listener — versione "light"**.
* **Focus Stanze:** Il resto della mappa è composto da Stanze Normali (che introducono i primi campanelli) e Corridoi.

### Livello 3
* **Dimensioni Mappa:** Grandi.
* **Stanze Mostro:** 3 stanze mostro (introduzione completa):
    * **Stanza del Listener — normale**.
    * **Stanza dello Stalker — light**.
    * **Stanza del Screamer — introduttiva**.
* **Focus Stanze:** Aumento significativo del numero di Stanze Normali e Corridoi per ospitare le 3 stanze mostro e aumentare l'esplorazione. Introduzione delle Mine Sonore.

### Livello 4
* **Dimensioni Mappa:** Molto Grandi.
* **Stanze Mostro:** 4 stanze mostro (una per tipo), versione **hard**:
    * Stanza del Listener (Hard).
    * Sala dello Stalker (Hard).
    * Arena del Screamer (Hard).
    * Una stanza ibrida o ripetizione a scelta.
* **Focus Stanze:** Mappa espansa con molte Stanze Normali, Corridoi, e introduzione di Aree Mute (Sabbia) e Barriere Acustiche.

### Livello 5
* **Dimensioni Mappa:** Enormi.
* **Stanze Mostro:** 10 stanze totali **(versioni estreme)**:
    * 4 Screamer (Extreme).
    * 3 Listener (Extreme).
    * 3 stalker  (Extreme).
* **Focus Stanze:** Mappa labirintica con un'alta densità di Stanze Normali, Corridoi, puzzle sonori complessi, e una combinazione di tutti i materiali e trappole.

## Tipi di stanze (versioni aggiornate)

-- visualizzare **rooms.md** per maggiori informazioni sulle stanze

# ⚠️ FASE 5 — Inserimento Trappole
### Quantità per livello (per 1000 tile):
- **Livello 1:** 0
- **Livello 2:** 10–20
- **Livello 3:** 25–40
- **Livello 4:** 50–70
- **Livello 5:** 80–120

### Tipologie:
- **Mine sonore** (40%)
- **Campanelli** (25%)
- **Barriere acustiche** (20%)
- **Zone anti-eco** (15%)

### Regole:
- Corridoi: 30% probabilità di trappole
- Mai nella Stanza Dormiente
- Zone mute sempre in cluster

---

# 🧱 FASE 6 — Template delle Stanze
### Stanze normali
- dimensioni variabili
- mostri secondo probabilità del livello
- trappole secondo densità del livello

### Corridoi
- altezza fissa: 3 tile
- lunghezza variabile
- materiali spesso rimbalzanti (metallo, cristalli)

---

# 🔧 FASE 7 — Rielaborazione Connessioni
Per ogni stanza:
1. Identificare ingressi ed uscite create dal generatore principale.
2. Convertire tali punti in corridoi.
3. Se la stanza è troppo isolata, aggiungere corridoi extra.

---

# 🌌 FASE 8 — Aree Speciali
- Camere grandi con eco multiplo
- Zone mute (materiale morto)
- Aree di risonanza (cristalli)
- Porte acustiche attivabili con ping potenziato

---

# 🚪 FASE 9 — Posizionamento Uscita
Regole:
- Mai in una stanza mostro
- Mai troppo vicina allo spawn
- Preferibilmente in aree ampie
- Materiali sonori riconoscibili (cristalli o metallo)

---

# 🧠 OUTPUT FINALE
Il generatore restituisce un JSON con:
```
{
  width,
  height,
  tiles: [...],
  rooms: [...],
  corridors: [...],
  materials: [...],
  traps: [...],
  monsters: [...],
  spawnPoints: [...],
  exitPoint: {...}
}
```

Questo file viene inviato ai client Phaser.js per:
- rendering livello
- posizionamento mostri
- attivazione trappole
- gestione ping e rimbalzi

---

# ✔ Conclusione
Questo algoritmo definisce un sistema completo, modulare e altamente configurabile per generare labirinti ricchi, coerenti e perfettamente adatti alle meccaniche sonore di **Echo Maze**.
