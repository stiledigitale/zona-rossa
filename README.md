# Zona Rossa 3D

Battle royale 3D low poly nel browser, con animali a cubo, in prima e terza persona. Realizzato con Three.js (r128) in un unico file HTML per versione.

## Come si gioca

- `index.html`: pagina d'ingresso per scegliere la modalità.
- `online.html`: modalità classica. Si entra e si gioca con chi è collegato. Usa Supabase Realtime come centralino.
- `p2p.html`: modalità con host. Un giocatore crea la partita e condivide il codice di 4 cifre; gli altri entrano con il codice. Usa PeerJS (WebRTC) per il collegamento diretto con l'host.

In tutte e due le modalità c'è anche l'allenamento contro i bot.

## Comandi

| Azione | Computer | Telefono |
|---|---|---|
| Muoversi | WASD | Stick a sinistra |
| Guardare | Mouse (clic per catturarlo) | Trascina a destra |
| Sparare | Clic sinistro | Tasto SPARA |
| Mirare | Tasto destro | Tasto Mira |
| Saltare / lanciarsi dall'aereo | Spazio | Salta / LANCIATI |
| Accovacciarsi / sdraiarsi | C / Z | Tasti Accov. / Sdraiati |
| Raccogliere | E | Raccogli |
| Ricaricare | R | Ricarica |
| Bende / kit / siringa | 4 / 5 / 6 | Tocca le scorte in alto |
| Cambiare visuale (partite Misto) | V | Vista |
| Mappa grande | M | Tocca la minimappa |
| Menu | Esc | Esc · Menu |

## Pubblicazione

Il sito è servito con GitHub Pages dal ramo `main`, cartella principale. I file vanno aperti da un indirizzo web, non con doppio clic dal computer.

## Note tecniche

- Modalità P2P: il server gratuito di PeerJS serve solo a far trovare i giocatori. Con alcune reti (operatori mobili, reti aziendali) il collegamento diretto può non riuscire senza un server TURN.
- Modalità online: la chiave usata è quella pubblica (anon) di Supabase, pensata per stare nel codice lato browser. Il piano gratuito limita i messaggi al secondo.

## Lobby pubblica

La pagina d'ingresso e i menu di gioco mostrano le **partite aperte in tempo reale**:

- **ONLINE**: l'*Arena principale*, sempre disponibile, e le stanze create con *Crea una stanza nuova*. Una stanza ha il suo link, quindi lo puoi anche mandare agli amici.
- **AMICI**: le partite P2P che l'host ha lasciato visibili (casella *Mostra la mia partita nella lobby pubblica*). Basta premere *Entra*, senza scrivere il codice.

Funziona con la **presence di Supabase Realtime** sul canale `zr3-lobby`. Non servono tabelle: una partita sparisce da sola dalla lista quando l'host chiude la pagina.

## Pubblicazione su Cloudflare Pages

1. Nel pannello di Cloudflare: **Workers & Pages → Create → Pages → Connect to Git**.
2. Scegli il repository `stiledigitale/zona-rossa`.
3. Framework preset: **None**. Build command: vuoto. Build output directory: `/`.
4. **Save and Deploy**. A ogni push su `main` il sito si aggiorna da solo.
