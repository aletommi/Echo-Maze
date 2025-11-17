# Gameplay

Il gameplay di **Echo Maze** ruota attorno all'uso dell'ecolocalizzazione per navigare un ambiente completamente buio, pieno di pericoli e ostacoli. Tutte le meccaniche sono pensate per essere **cooperative**, **minimaliste**, ma con grande profondità strategica.

---

# 🎮 1. Movimento dei Pipistrelli
I giocatori controllano due pipistrelli meccanici identici, con le seguenti caratteristiche:
- movimento in 8 direzioni
- velocità costante
- collisione con muri e ostacoli
- piccola area di luce attorno al corpo (visione base)

Non esistono differenze di ruolo: entrambi i giocatori sono equivalenti.

---

# 🔊 2. Il Ping (Ecolocalizzazione)
Il ping è il cuore del gioco. Si tratta di un'onda sonora che parte dal pipistrello e si espande in una direzione con un angolo di 40 gradi


## Effetti del ping
- illumina temporaneamente le pareti colpite
- rivela trappole e mostri
- crea un'eco visiva che permette al giocatore di memorizzare la forma del labirinto

L'ambiente torna buio dopo pochi istanti.

---

# 🤝 3. Ping Potenziato (Cooperazione)
Se le onde direzionali (40°) dei due giocatori **si colpiscono fisicamente nello spazio**:
- Si genera una **"Super-Eco"** circolare dal punto di collisione.
- il raggio aumenta
- la durata aumenta
- i rimbalzi sono più numerosi
- l'illuminazione dura più a lungo
- parte un effetto visivo speciale (risonanza)

Questo sistema incoraggia i giocatori a comunicare e sincronizzarsi.

---

# 🧱 4. Materiali Acustici
Ogni muro può essere costruito con materiali differenti, che influenzano il comportamento dell’onda.

| Materiale | Effetto acustico |
|-----------|------------------|
| Basalto | assorbimento elevato, eco breve |
| Calcare | eco moderata |
| Cristalli | forti riflessioni, eco lunga |
| Metallo | rimbalzi molto intensi e limpidi |
| Sabbia | assorbe quasi tutto, eco minima |
| Materiale morto (zone mute) | cancella completamente il suono |

Il giocatore impara a riconoscere i materiali dal comportamento dell’eco.

---

# 👾 5. Mostri e Comportamento
Sono visibili solo quando colpiti dal ping.

### Tipi di mostri
1. **Stalker** – Segue i giocatori nel buio quando non osservato.
2. **Cieco ("Listener")** – Rimane immobile finché non viene colpito da un ping, poi corre verso la fonte.
3. **Veggente ("Screamer")** – Vede i giocatori al buio ed emette un urlo che illumina tutto e attira altri mostri.

### Reazioni al suono
- seguono l'origine dell’eco
- reagiscono in modo diverso a ping semplice o potenziato
- possono essere depistati con echi lanciati dal compagno

---

# ⚠️ 6. Trappole
Le trappole sono attivate dal suono.

Tipologie:
- **mine sonore** → esplodono quando colpite dal ping
- **campanelli** → attirano mostri
- **barriere acustiche** → si aprono o si chiudono con l’eco
- **zone anti-eco** → l’onda muore non appena entra

---

# 🏆 7. Obiettivo del Gioco
In ogni livello i giocatori devono:
1. esplorare il labirinto
2. evitare mostri e trappole
3. orientarsi grazie all'eco
4. trovare l’uscita

La cooperazione aumenta le possibilità di sopravvivenza.

---

# 🧠 8. Progressione della Difficoltà
Man mano che si avanza:
- le mappe diventano più grandi
- i materiali acustici diventano più complessi
- aumentano mostri e trappole
- appaiono puzzle che richiedono ping sincronizzato
- alcune zone oscurano completamente il suono

---

# 🕹️ 9. Comandi
- **Movimento**: WASD / Frecce
- **Ping**: tasto principale (es. Space / Click)
- **Ping cooperativo**: ping simultaneo da parte dei due giocatori

---

# 🔍 10. Feedback Visivi
Il gioco utilizza solo elementi minimi:
- bagliore attorno ai pipistrelli
- illuminazione temporanea generata dall’eco
- dissolvenza graduale delle superfici
- effetti di risonanza quando il ping è potenziato

---

# 🧩 11. Puzzle Sonori
Alcune sezioni richiedono:
- ping coordinato
- mantenere attiva una risonanza
- illuminare stanze in sequenza
- attirare o evitare mostri per liberare passaggi

---

# 🎯 12. Filosofia di Design
- **Minimalismo totale**: solo ciò che è necessario è visibile.
- **Tensione senza jumpscare**: il pericolo è nel buio.
- **Cooperazione vera**: i giocatori non possono procedere da soli.
- **Ecolocalizzazione realistica**: l’eco è il linguaggio del gioco.

# ⏱️ 13. Tempo e Classifica
Ogni livello include un **timer ufficiale**, che registra la performance della squadra.


## Come funziona il timer
- Inizia quando entrambi i giocatori si muovono nella mappa.
- Si mette in pausa se uno dei due muore temporaneamente (se esiste una meccanica di respawn).
- Finisce quando entrambi raggiungono l’uscita.


## Salvataggio del tempo
Al termine del livello, il backend registra:
- **tempo totale**
- **numero di ping usati**
- **mostri incontrati/evitati**
- **trappole attivate**
- **livello completato**


## Classifica globale
La Leaderboard mostra:
- I migliori tempi
- I nomi dei due giocatori
- Statistiche riassuntive
- Posizione nella classifica


Questo sistema aggiunge **rigiocabilità**, spirito competitivo e incentiva la cooperazione per ottenere il miglior tempo possibile.