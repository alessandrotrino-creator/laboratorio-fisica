# 🔬 Laboratorio di Fisica 2D

Simulatore di fisica interattivo per la **scuola secondaria di primo grado**, pensato per la LIM e per il computer.
Gli studenti creano palline, muri, molle e perni, e osservano gravità, urti, attrito, energia e **galleggiamento**
con materiali e liquidi reali.

**Apri il simulatore:** https://alessandrotrino-creator.github.io/laboratorio-fisica/

Non serve installare niente: è una pagina web unica, senza librerie esterne, che funziona in qualsiasi browser moderno.

---

## Versioni

L'indirizzo principale apre una **pagina di scelta** da cui si sceglie la versione.

| File | Versione | Stato |
|---|---|---|
| `index.html` | Pagina di scelta tra le versioni | — |
| `versione3.html` | **Versione 3**: un esperimento alla volta, con solo le sue variabili | nuova, in prova |
| `versione2.html` | Versione 2: galleggiamento con materiali reali, molle migliorate | precedente |
| `versione1.html` | Versione 1: il simulatore originale | stabile |

Link diretti:
- https://alessandrotrino-creator.github.io/laboratorio-fisica/versione3.html
- https://alessandrotrino-creator.github.io/laboratorio-fisica/versione2.html
- https://alessandrotrino-creator.github.io/laboratorio-fisica/versione1.html

---

## Cosa si può fare

- **Esperimenti (versione 3):** in alto si sceglie l'esperimento e sotto compaiono **solo le variabili che contano**
  per quell'esperimento, con un riquadro "cosa osservare" che calcola i valori del momento.
  Tutto il resto sta nel pannello chiuso "Tutte le altre impostazioni".

  | Esperimento | Variabili in evidenza |
  |---|---|
  | 🎱 Pendolo di Newton | numero di palline, palline sollevate, angolo, fili rigidi o elastici (con la loro k), elasticità, gravità, energia |
  | 📐 Piano inclinato | inclinazione θ, attrito, elasticità, gravità, energia; calcola a = g·(sin θ − μ·cos θ) |
  | 🌨️ Valanga | numero di palline, attrito, elasticità, gravità |
  | 🌊 Galleggiamento | liquido, materiale o densità teorica, esito, esperimenti pronti |
  | 🔗 Molla che oscilla | rigidità k, massa, smorzamento, gravità, energia; calcola il periodo T = 2π·√(m/k) e l'allungamento m·g/k |
  | 🧪 Laboratorio libero | strumenti, palline, molle, gravità, urti, attrito, visualizzazione, energia |

- **Scene pronte (versioni 1 e 2):** pendolo di Newton, piano inclinato, valanga di palline, galleggiamento.
- **Strumenti:** palla (clic per creare, trascina per lanciare), muro (tasto destro + trascina), molla, perno, elimina.
- **Parametri:** gravità (Terra, Luna, Giove, spazio), elasticità degli urti, attrito, velocità del tempo e rallentatore.
- **Energia in tempo reale:** un grafico mostra l'energia cinetica, quella potenziale e il totale.
- **Galleggiamento (versione 2):**
  1. scegli un **liquido reale** (acqua dolce, acqua di mare, Mar Morto, olio, alcol, miele, mercurio…);
  2. scegli un **materiale reale** (polistirolo, sughero, legni, ghiaccio, uovo, plastica, vetro, metalli, oro…)
     oppure una **densità teorica**, con accanto il materiale reale più simile;
  3. lascia cadere il campione e osserva: il simulatore dice se galleggia o affonda e quanta parte resta immersa.
  - La lista dei materiali ha una **linea dell'acqua**: sopra la linea i materiali galleggiano, sotto affondano.
  - Con **"Nascondi le risposte"** gli studenti fanno prima la previsione e poi la verificano.
  - **Esperimenti pronti:** *Chi galleggia in acqua?*, *L'uovo e il sale*, *L'iceberg*, *Il ferro nel mercurio*.

Scorciatoie da tastiera: `spazio` pausa · `.` un passo · `S` rallentatore · `V` vettori · `R` ricomincia ·
`C` svuota · `1`–`6` esperimenti (versione 3; `1`–`4` nelle precedenti) · `Esc` annulla la molla ·
`Canc` elimina la molla selezionata.

---

## Ultimi aggiornamenti

### 29 settembre 2026 — Versione 3 (in prova)

**Un esperimento alla volta, meno confusione nel pannello**
- In alto 6 pulsanti per scegliere l'esperimento: Pendolo di Newton, Piano inclinato, Valanga, Galleggiamento,
  Molla che oscilla, Laboratorio libero.
- Sotto compaiono solo le variabili utili per quell'esperimento, con un riquadro "cosa osservare" che si
  aggiorna con i valori scelti. Le altre impostazioni sono raccolte in un pannello chiuso.
- **↺ Ricomincia** fa ripartire l'esperimento tenendo i valori scelti; **Ripristina i valori iniziali** torna a quelli di partenza.

**Nuove variabili per esperimento**
- Pendolo di Newton: numero di palline (3–7), palline sollevate (1–3), angolo di partenza, fili rigidi oppure
  elastici con la rigidità k regolabile.
- Piano inclinato: inclinazione della rampa (10°–60°), con l'accelerazione calcolata. Se l'attrito vince,
  il riquadro spiega perché le palline restano ferme (tan θ < μ).
- Valanga: numero di palline (20–250).

**Nuovo esperimento: Molla che oscilla**
- Una pallina appesa a una molla parte con la molla a riposo, "cade" e oscilla.
- Cursori dal vivo per la rigidità k, la massa (0,1–3 kg) e lo smorzamento; il pulsante "Riporta su e lascia cadere".
- Linee tratteggiate che mostrano la molla a riposo e il punto di equilibrio. Il riquadro calcola il periodo
  T = 2π·√(m/k) e l'allungamento m·g/k. Verificato: il periodo simulato coincide con la teoria.

### 29 settembre 2026 — Versione 2 (in prova)

**Galleggiamento con materiali reali**
- 22 materiali reali e 9 liquidi reali, con le densità vere in g/cm³ e la virgola decimale.
- Una sezione unica "Galleggiamento" in 3 passi: liquido → materiale → osserva.
- Un riquadro con l'esito (galleggia, affonda o resta sospeso), la percentuale immersa e le barre di confronto delle densità.
- La linea dell'acqua nella lista dei materiali e i bollini "galleggia / affonda".
- Cursori di densità logaritmici (comodi sia per i legni sia per i metalli), con il riferimento al materiale o al liquido reale più vicino.
- La modalità "Nascondi le risposte" per far fare la previsione agli studenti.
- Etichette leggibili sopra le palline: nome, densità, percentuale immersa o massa.
- 4 esperimenti pronti.

**Molle**
- Le molle non "esplodono" più con palline leggere o con uno smorzamento alto: la parte di smorzamento è calcolata in modo implicito, stabile, e l'energia della molla si conserva.
- **Trascina** da una pallina all'altra per creare una molla, oppure clicca in sequenza per fare una **catena**.
- **Clic su una molla** per selezionarla: k, smorzamento, lunghezza a riposo e asta rigida valgono solo per lei.
- Un'anteprima con la lunghezza in metri, messaggi chiari e nessun perno inutile lasciato in giro.

**Sito**
- Nuova pagina di scelta tra le versioni (`index.html`). La versione originale è ora in `versione1.html`.

### 19 settembre 2026 — Versione 1
- Prima pubblicazione del simulatore.

---

## Come aggiornare il sito

Il sito è pubblicato con **GitHub Pages** dal ramo `main`: ogni file caricato nel repository finisce online in circa un minuto.

1. Su GitHub, apri il repository e scegli **Add file → Upload files**.
2. Trascina i file modificati (se un file ha lo stesso nome di uno esistente, lo sostituisce).
3. Premi **Commit changes**.
4. Controlla il sito e, se vedi ancora la versione vecchia, ricarica con **Ctrl + F5**.

**Per provare una nuova versione senza toccare quella che usano gli studenti:** salvala come `versione4.html`,
caricala e aggiungi un pulsante nella pagina di scelta (`index.html`).
