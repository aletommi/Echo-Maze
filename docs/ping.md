# 🔊 Il Sistema di Ping

Questo documento descrive il funzionamento della meccanica di ecolocalizzazione ("Ping") in **Echo Maze**. Il ping è lo strumento principale del giocatore per mappare l'ambiente, ma attira anche i nemici.

Le meccaniche qui descritte specificano e aggiornano la **Fase 4** della roadmap e la **Sezione 3** del `gameplay.md`.

---

## 1. Ping Base (Giocatore Singolo)

Il ping base è un'azione direzionale e intenzionale.

### 1.1 Attivazione e Forma
Quando il giocatore preme il tasto Ping:
* Viene generata una singola onda sonora.
* **Forma:** L'onda non è circolare, ma un **cono di 40 gradi**.
* **Direzione:** Il cono punta nella direzione in cui il pipistrello sta camminando. Se il giocatore è fermo, usa l'ultima direzione di movimento.

### 1.2 Propagazione e Dissolvenza
* L'onda (il cono) viaggia in avanti dalla posizione del giocatore a velocità costante.
* Ha una **luminosità iniziale** (es. 100% di opacità) e un raggio d'azione massimo.
* Durante il viaggio, la sua luminosità **decrementa gradualmente** fino a scomparire dopo una certa distanza o tempo.

---

## 2. Impatto, Illuminazione e Rimbalzi

Quando l'onda colpisce un ostacolo (un muro), accadono due cose: l'illuminazione e il rimbalzo.

### 2.1 Illuminazione Muri
* **Impatto Diretto:** Il tile del muro colpito dal fronte dell'onda si illumina istantaneamente.
* **Illuminazione "Splash":** Vengono illuminati anche i **5 tile adiacenti** a quello colpito. Questo crea un piccolo "splash" di luce che aiuta a definire la forma della superficie.
* **Durata:** L'illuminazione è temporanea. I tile colpiti restano visibili per 1-2 secondi prima di tornare al buio.

### 2.2 Rimbalzi
* **Calcolo Angolo:** Quando l'onda colpisce un muro, il gioco calcola l'angolo di riflessione (angolo di incidenza = angolo di riflessione).
* **Propagazione Rimbalzo:** L'onda continua il suo viaggio nella nuova direzione.
* **Limite Rimbalzi:** L'onda può rimbalzare un **numero limitato di volte** (es. 2 o 3 rimbalzi).
* **Degradazione:** Ad ogni rimbalzo, l'onda perde energia:
    * La sua luminosità massima diminuisce.
    * L'illuminazione "splash" (i 5 tile) potrebbe ridursi (es. a 3 tile, poi 1).
    * Il raggio massimo rimanente si accorcia.

---

## 3. Ping Potenziato (Cooperativo)

Questa è la meccanica cooperativa fondamentale, che aggiorna quella definita nel `gameplay.md`.

* **Attivazione :** Il ping potenziato si attiva quando le **due onde di 40 gradi dei giocatori si colpiscono fisicamente** nello spazio.
* **Effetto:** Nel punto di collisione delle due onde, si genera una **"Super-Eco"**.
* **Caratteristiche della Super-Eco:**
    * È un'onda **circolare** (omnidirezionale) che parte dal punto di collisione.
    * È **più intensa** (colore diverso, es. oro o azzurro).
    * Ha un raggio e una durata molto maggiori.
    * Quando colpisce i muri, **illumina più pareti** (es. 10-15 tile adiacenti invece di 5).
    * Può essere necessaria per attivare puzzle specifici (es. Porte Acustiche).

> **Nota di design:** Questo sistema incoraggia i giocatori non solo a "pingare insieme", ma a coordinare la loro *posizione* e *direzione* per far incontrare le loro onde, aumentando la cooperazione e l'abilità richiesta.

---

## 4. Interazione con i Materiali

I materiali acustici (definiti nel `gameplay.md` e `levels.md`) influenzano il comportamento dei rimbalzi e dell'illuminazione:

| Materiale | Effetto sul Ping Direzionale (40°) |
| :--- | :--- |
| **Metallo** | Rimbalzo perfetto (angolo preciso), 0% perdita di energia. Illuminazione "splash" massima (5 tile). |
| **Calcare** | Buon rimbalzo, 30% perdita di energia. Illuminazione "splash" media (3 tile). |
| **Basalto** | Rimbalzo debole (angolo un po' "diffuso"), 70% perdita di energia. Illuminazione "splash" minima (1 tile). |
| **Sabbia** | **Nessun rimbalzo**. L'onda viene assorbita. Illumina solo il tile colpito (0 splash). |
| **Materiale Morto** | **Nessun rimbalzo e nessuna illuminazione**. L'onda scompare e basta. |

---

## 5. Sincronizzazione Multiplayer

Il ping deve essere sincronizzato tra i due client.

1.  **Invio:** Giocatore 1 preme "Ping". Il Client 1 invia al Server: `{posizione, direzione}`.
2.  **Replica:** Il Server inoltra l'evento `{posizione, direzione, player_id}` al Client 2.
3.  **Rendering:** Il Client 2 renderizza l'onda del compagno (magari con un colore leggermente diverso per distinguerla).
4.  **Collisione (Co-op):** La collisione tra le due onde per il Ping Potenziato deve essere **calcolata e validata dal Server** per garantire che entrambi i giocatori vedano la Super-Eco nello stesso momento.