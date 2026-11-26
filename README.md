# Blocky Zoo Royale 🐾

Battle royale in prima persona tra animali a cubo, nel browser: 40 giocatori (i posti liberi li riempiono i bot) su un'isola con 3 villaggi, un paese e 5 fabbriche abbandonate.
Lanciati dall'aereo col paracadute e trova armi e bottino. Esplora paesi, boschi, deserto e fabbriche abbandonate, e stai lontano dai laghetti con i coccodrilli. Resta l'ultimo in piedi.

**Gioca:** apri `index.html` (la pagina d'ingresso con la lobby) oppure `online.html`.

## Multiplayer online (Supabase Realtime)

- Un giocatore fa da **centro**: è il primo entrato nella stanza, e se esce il ruolo passa da solo al successivo. Gli altri gli mandano i propri aggiornamenti su un canale personale, e lui rimanda a tutti una sola "fotografia" della partita.
- La frequenza si adatta al numero di giocatori, per restare sotto il limite del piano gratuito di Supabase (100 messaggi al secondo per progetto).
- **Orologio comune** sincronizzato col centro: aereo, zona e round sono uguali per tutti anche se gli orologi dei dispositivi non coincidono.
- I movimenti degli altri sono **interpolati**, e i giocatori non si passano attraverso.
- I bot li muove un solo giocatore alla volta (il primo entrato nel round), così tutti vedono gli stessi bot.

## Lobby pubblica

La pagina d'ingresso e il menu mostrano le partite aperte: l'*Arena principale* e le stanze create con *Crea una stanza nuova*. Ogni stanza ha il suo link e il suo tipo di squadra (da solo, a 2 o a 3).

## Comandi

| Computer | Telefono |
|---|---|
| WASD muoviti, mouse guarda e spara, tasto destro mira | stick a sinistra (segue il dito), trascina a destra per guardare |
| Spazio salta / lanciati, C accovacciati, Z sdraiati | tasti con icone intorno al tasto di sparo |
| E raccogli, R ricarica, 1-2-3 armi, Q cambia | "Raccogli" compare col nome dell'oggetto vicino |
| 4 bende, 5 kit, 6 siringa, M mappa, Esc menu | nella pausa: sensibilità, grandezza tasti, sparo anche a sinistra |

## Pubblicazione su Cloudflare Pages

1. **Workers & Pages → Create → Pages → Connect to Git**, repository `stiledigitale/zona-rossa`.
2. Framework preset **None**, Build command vuoto, Build output directory `/`.
3. **Save and Deploy**. A ogni push su `main` il sito si aggiorna da solo.
