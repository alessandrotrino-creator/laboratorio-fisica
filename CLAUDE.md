# CLAUDE.md

Istruzioni per Claude (e per chiunque lavori al codice) su questo repository.

## Il progetto

Simulatore di fisica 2D per la **scuola secondaria di primo grado** (studenti di 11–14 anni), usato in classe
sulla LIM. Chi lo mantiene è un insegnante, non uno sviluppatore: spiega le modifiche in italiano semplice
e tieni l'interfaccia chiara per ragazzi di quell'età.

Pubblicato con GitHub Pages: https://alessandrotrino-creator.github.io/laboratorio-fisica/

## Struttura

| File | Ruolo |
|---|---|
| `index.html` | Pagina di scelta tra le versioni (solo HTML e CSS, nessuno script). |
| `versione2.html` | Versione attuale di sviluppo: **è qui che si lavora**. |
| `versione1.html` | Versione originale, congelata. **Non modificarla.** |
| `README.md` | Descrizione per i collaboratori, con la cronologia degli aggiornamenti. |

Ogni versione è **un unico file HTML autonomo** (CSS e JS inline, nessuna libreria, nessun build).
Tienilo così: deve funzionare aprendo il file e con il caricamento via web di GitHub.

**Flusso delle versioni:** una modifica importante va in un nuovo `versioneN.html`, con un pulsante nuovo in
`index.html`. Quella precedente resta com'è finché l'insegnante non decide. Dopo ogni modifica aggiorna la
sezione "Ultimi aggiornamenti" del README.

## Architettura di `versione2.html`

Motore scritto da zero, in un solo `<script>`. Sezioni nell'ordine in cui compaiono:

1. **Costanti e stato:** `PPM = 60` (pixel per metro); `P` contiene tutti i parametri (gravità, attrito,
   `bodyRho`, `mat`, `fluidRho`, `fluid`, `labels`, …); `world = { balls, walls, springs }`.
2. **Dati reali:** `MATERIALS` / `MAT` e `FLUIDS` / `FLU`, con la densità in g/cm³, l'icona e il colore.
   Per aggiungere un materiale o un liquido basta una riga in queste tabelle: la lista, i chip e i
   riferimenti "≈ come" si aggiornano da soli. `MATERIALS` deve restare **ordinato per densità crescente**
   (serve alla linea dell'acqua e a `nearText`).
3. **Fisica** (`substep`), a sottopassi con correzione posizionale dei vincoli:
   - forze → `applySpringForces` (molle di Hooke) e `applyFluid` (Archimede + resistenza);
   - integrazione → contatti (`detect`, `solveContacts`) → aste rigide (`solveRods`);
   - velocità ricavate dallo spostamento → `velocityPass` (restituzione e attrito dinamico).
4. **Rendering su canvas:** `render`, `drawSpring`, `drawFluid`, `drawLabels`.
5. **Scene:** `sceneNewton`, `sceneRamp`, `sceneAvalanche`, `sceneFloat`, `sceneEgg`, `sceneIceberg`,
   `sceneMercury`, registrate nella mappa `scenes` e caricate da `loadScene`.
6. **Interfaccia:** gestori del puntatore (strumenti palla, muro, molla, perno, elimina), pannello e
   sezione galleggiamento (`updateFloatUI` ridisegna lista, chip, verdetto e riferimenti).

### Scelte di fisica da non rompere

- **Molle:** la parte elastica è esplicita (simplettica, conserva l'energia); lo **smorzamento è implicito**.
  La versione esplicita esplodeva con palline leggere e uno smorzamento alto (c·h/m > 2). Un termine implicito
  per la rigidezza si attiva solo se k·h²/m > 1.
- **Densità:** il mondo è 2D, quindi la massa è `m = ρ·π·r²`, con ρ numericamente uguale alla densità reale
  in g/cm³. Così il rapporto ρ_corpo/ρ_liquido, e quindi la frazione immersa, è quello reale.
- **Sottopassi:** `P.substeps` (10–26 a seconda della scena); ogni scena imposta il suo.

## Convenzioni

- **Tutto in italiano:** interfaccia, messaggi (`toast`) e commenti nel codice.
- Numeri mostrati agli studenti con la **virgola decimale** (`fmtN`, `fmtRho`) e densità in **g/cm³**.
- Colori definiti in `:root`; tema scuro.
- **Emoji:** l'insegnante usa Windows 10, che non mostra le emoji Unicode 13 e successive
  (per esempio 🪵 🪨 🫒). Usa solo emoji fino alla versione 12.
- Cursori di densità **logaritmici** (`logTo` / `logFrom`); il valore reale sta in `P`, non nel `value` dello slider.
- Lo stato dell'interfaccia (`ui`) è dichiarato con `const` più avanti rispetto ad alcune funzioni che lo usano:
  quelle funzioni vanno chiamate solo a runtime, mai durante il caricamento dello script.

## Come provare le modifiche

- Nella pagina c'è un hook per i test: `window.SIM`, con `P`, `world`, `step(dt)`, `energy()`, `loadScene`,
  `addBall`, `addSpring`, `subArea`, `fluidSurfaceY`, `dims()` e `PPM`.
- Per i controlli numerici usa `SIM.step(1/60)` in un ciclo, non il tempo reale: `requestAnimationFrame`
  rallenta quando la finestra è nascosta.
- Controlli utili dopo una modifica alla fisica:
  - periodo della molla ≈ 2π√(m/k);
  - energia totale costante senza attrito e senza smorzamento;
  - frazione immersa all'equilibrio ≈ ρ_corpo/ρ_liquido;
  - nessuna pallina che raggiunge `VMAX`.
- Aprire il file da `file://` di solito funziona. Per i test automatici conviene servirlo da un server locale.

## Pubblicazione

Sul PC dell'insegnante non c'è git. Il caricamento si fa dall'interfaccia web di GitHub
(**Add file → Upload files → Commit changes**) e GitHub Pages pubblica in circa un minuto.
Quando prepari dei file, consegnali con i nomi definitivi e scrivi quali caricare.

## Cronologia recente

- **2026-09-29:** versione 2. Galleggiamento con materiali e liquidi reali, verdetto e linea dell'acqua,
  modalità previsione, esperimenti pronti, molle stabili (smorzamento implicito) con catene, selezione e L₀
  regolabile, pagina di scelta tra le versioni. Dettagli nel README.
- **2026-09-19:** versione 1, prima pubblicazione.
