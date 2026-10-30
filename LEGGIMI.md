# multimeter — guida rapida

Visualizzatore audio in tempo reale che gira direttamente nel browser. Basta aprire `index.html` (o avviare un server locale) e caricare un file audio o video: nessuna installazione.

---

## Avvio rapido

1. Apri `index.html` nel browser oppure avvia un server locale:
   ```
   python3 -m http.server 8080
   ```
2. Clicca **[ load audio / video ]** e scegli un file, oppure trascinalo direttamente sulla pagina.
3. Premi **▶** (o la **barra spaziatrice**) per avviare la riproduzione.
4. I quattro moduli di visualizzazione funzionano in tempo reale.

---

## Interfaccia generale

L'interfaccia è divisa in due zone:

- **Area visualizzatori** (sinistra): i quattro moduli visualizer.
- **Pannello controlli** (destra): tutti i parametri, raggruppati in sezioni espandibili. Clicca il titolo di una sezione per aprirla o chiuderla. Il pulsante **☰** in alto a destra nasconde o mostra l'intero pannello.

---

## Trasporto e timeline

La barra in cima alla pagina contiene la forma d'onda del file caricato e i controlli di riproduzione.

| Controllo | Funzione |
|---|---|
| **▶** | Avvia la riproduzione |
| **⏸** | Mette in pausa |
| **■** | Ferma e torna all'inizio |
| **⟳ loop** | Attiva il loop sulla regione selezionata |
| **fit** | Riporta lo zoom della timeline a 1× |
| Slider zoom | Ingrandisce la timeline fino a 40× |
| Display orario | Mostra il tempo corrente e la durata totale |

**Navigazione nella timeline:**
- Clicca in qualsiasi punto della forma d'onda per saltare a quella posizione.
- Scorri con la rotella del mouse per scorrere orizzontalmente.
- Tieni premuto **Ctrl** (o **Cmd**) e scorri per zoomare.
- Tasto destro + trascina per fare pan.

**Regione di loop:**
Quando il loop è attivo, compaiono due maniglie sulla timeline. Trascinale per definire il punto d'inizio e di fine del loop.

---

## Caricamento audio e cronologia

- **[ load audio / video ]** — apre il selettore file. Sono supportati file audio (MP3, WAV, FLAC, AAC…) e video (MP4, WebM…); dall'audio di un video viene estratta solo la traccia sonora.
- **Drag & drop** — trascina un file direttamente sulla pagina.
- **save** — salva il file corrente nella cronologia (max 10 voci, memorizzate nel browser).
- **☰** (accanto a save) — apre la lista dei file salvati. Clicca un nome per ricaricarlo, o il tasto × per eliminarlo.

---

## Gain di ingresso e uscita

Due coppie di slider nel pannello **General** controllano il volume:

- **in:** — guadagno prima dell'analisi (–30 dB … +12 dB).
- **out:** — guadagno del segnale in uscita (–30 dB … +12 dB).

I campi numerici accanto agli slider mostrano il valore in dB e possono essere modificati direttamente.

---

## Layout dei visualizzatori

Nella sezione **General** puoi:

- Scegliere tra tre layout: **1×4** (colonna), **2×2** (griglia), **4×1** (riga).
- Impostare larghezza (**W**) e altezza (**H**) di ogni finestra visualizzatore in pixel.
- Mostrare o nascondere ciascun modulo con le quattro caselle **01 vol / 02 freq / 03 stereo / 04 spec**.
- Riordinare i moduli trascinando i titoli nei moduli o le righe nella lista di ordinamento del pannello.

---

## Palette colori globale

Il menu **global scheme** applica una palette predefinita a tutti i moduli contemporaneamente:

`multi` · `green` · `amber` · `cyan` · `plasma` · `hot` · `rgb` · `triad1` · `triad2`

Dopo aver scelto la palette, clicca **apply to all** per propagarla. I colori di ogni singolo modulo rimangono comunque modificabili individualmente.

---

## Preset

Nella sezione **Presets** puoi salvare e ripristinare l'intera configurazione dell'app:

1. Scrivi un nome nel campo di testo.
2. Clicca **save** per memorizzarlo.
3. Nella lista, clicca **load** per ripristinarlo o **×** per eliminarlo.

Il preset salva tutti i parametri dei quattro moduli, i gain, il layout e l'ordine dei visualizzatori.

---

## Modulo 01 — Volume / Loudness

Mostra il livello del segnale in modo diverso a seconda della modalità selezionata in **mode**:

| Modalità | Cosa mostra |
|---|---|
| **LR** | Livelli separati canale sinistro, destro e stereo combinato |
| **MS** | Livelli Mid (somma), Side (differenza) e stereo combinato |
| **Vol** | RMS istantaneo, media mobile e picco |
| **Loud** | Loudness LUFS: momentary, short-term, integrated (standard ITU-R BS.1770) |

**Parametri principali:**

- **scale min / max** — intervallo dB visualizzato.
- **threshold** — linea rossa di clipping (soglia configurabile).
- **target** — linea di riferimento loudness (default –14 dB).
- **peak hold** — quanto a lungo rimane visibile il marker di picco (in secondi); attiva **fix** per tenerlo fermo a tempo indefinito.
- **avg time** — finestra temporale per la media del livello.
- **response** — velocità di risposta del metro (smoothing EMA).
- **show avg / peak val** — mostra i valori numerici nel canvas.

**Colori:** i tre color picker regolano le barre, la linea di clipping, la linea target e il colore dello 0 dB.

**Interazione diretta sul modulo:**
- Trascina verticalmente per spostare il contenuto.
- Doppio clic per azzerare la posizione (o resettare il LUFS in modalità Loud).

---

## Modulo 02 — Analizzatore di frequenze

Visualizza lo spettro di frequenza del segnale.

**Modalità (mode):**

| Modalità | Descrizione |
|---|---|
| **bars** | Barre verticali con gradiente di colore |
| **line** | Linea continua con area riempita sotto |
| **mirror** | Barre speculari rispetto all'asse centrale |

**Parametri principali:**

- **FFT size** — risoluzione dell'analisi: valori più alti (4096, 8192) danno più dettaglio ma sono più pesanti.
- **smooth** — smorzamento temporale: valori alti rendono il movimento più fluido.
- **fmin / fmax** — intervallo di frequenze mostrato (Hz).
- **peak hold** — durata del marker di picco; **fix** per bloccarlo.
- **height / hscale** — scala verticale delle barre.
- **vis min / max** — intervallo dB dell'asse verticale.
- **freq markers** — numero di etichette di frequenza sull'asse orizzontale (0–5).
- **dB scale** — mostra la scala dB a sinistra, a destra o la nasconde.

**Colori:** due color picker regolano il gradiente dalle basse alle alte frequenze.

**Interazione diretta sul modulo:**
- Trascina verticalmente per spostare il contenuto.
- Doppio clic per azzerare la posizione.

---

## Modulo 03 — Campo stereo

Analizza la relazione spaziale tra i canali sinistro e destro.

**Tipi di visualizzazione (type):**

| Tipo | Descrizione |
|---|---|
| **lissajous** | Oscilloscopio XY ruotato di 45°: segnale mono → linea verticale, antifase → linea orizzontale |
| **polar** | Rappresentazione polare Mid/Side: mono → verso l'alto, ampiezza stereo → verso l'esterno |
| **correlation** | Misuratore a scorrimento della correlazione: +1 = perfettamente in fase, –1 = perfettamente in antifase |

**Parametri principali:**

- **zoom** — ingrandisce o rimpicciolisce la figura.
- **decay** — persistenza della scia: valori bassi = scia lunga, valori alti = aggiornamento rapido.
- **mid / side gain** — amplifica o attenua indipendentemente il canale Mid o Side prima della visualizzazione.
- **plane opacity** — opacità delle linee di riferimento di sfondo.

**Colori:** due color picker per Mid e Side.

**Interazione diretta sul modulo:**
- Trascina per fare pan.
- Doppio clic per azzerare la posizione.

---

## Modulo 04 — Spettrogramma

Mostra l'evoluzione dello spettro nel tempo.

**Viste disponibili (view):**

| Vista | Descrizione |
|---|---|
| **3d graphic** | Vista tridimensionale: asse X = frequenza, asse Z = tempo, altezza Y = livello |
| **2d-tf** | Waterfall 2D: asse X = tempo, asse Y = frequenza, colore = intensità |

**Parametri comuni:**

- **FFT size** — risoluzione spettrale.
- **fmin / fmax** — intervallo di frequenze visualizzato.
- **window** — quanti secondi di storia vengono mantenuti (2–30 s).
- **db min / max** — intervallo dB per la mappatura del colore.

**Parametri specifici della vista 3D:**

- **zoom** — distanza della camera.
- **rx / ry / rz** — rotazione della scena sui tre assi. Doppio clic su uno slider per tornare alla posizione di default.
- **height scale** — altezza verticale delle creste.
- **axes opacity** — visibilità degli assi T/F/dB.

**Colori:** tre color picker (basse, medie, alte frequenze) definiscono il gradiente di intensità.

**Interazione diretta sul modulo:**
- Trascina per fare pan.
- Doppio clic per azzerare la posizione.

---

## Export video

Clicca **↓ export** per aprire la finestra di esportazione.

| Opzione | Valori disponibili |
|---|---|
| **format** | WebM (compatibile con tutti i browser) · MP4 (se supportato) |
| **fps** | 24 · 30 · 60 |

Premi **↓ start**: l'app riproduce il file dall'inizio e registra i visualizzatori sincronizzati con l'audio. Al termine scarica automaticamente il file video.

> Il video viene generato in formato portrait (1080×1920 px) con sfondo nero.

---

## Scorciatoie da tastiera

| Tasto | Azione |
|---|---|
| **Barra spaziatrice** | Play / Pausa (se non si sta digitando in un campo di testo) |

---

## Dati salvati nel browser

Multimeter usa il `localStorage` del browser per salvare:

- **Cronologia audio** — ultimi 10 file caricati.
- **Preset** — configurazioni salvate manualmente.

Cancellare la cache o i dati del sito rimuove queste informazioni.