# Indice

* [Elementi necessari](#elementi-necessari)
* [Identificare i dati corrotti](#identificare-i-dati-corrotti)
* [Come rimuovere i dati corrotti](#come-rimuovere-i-dati-corrotti)
* ["La soluzione abituale"](#la-soluzione-abituale)
* [Prevenire la corruzione dei dati](#prevenire-la-corruzione-dei-dati)
* [Altre risorse](#altre-risorse)

> **Esegui un backup completo dei tuoi file di salvataggio prima di tentare uno qualsiasi di questi passaggi!**

---

# Elementi necessari

## Cartella delle mod di Steam Workshop (Workshop Mods)

* È possibile accedervi facendo clic sull'icona della cartella di una mod di Steam Workshop nel menu Mod di Paralives.
* Navigando fino a:

**Windows:**

```text
C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
```

**Mac:**

```text
~/Library/Application Support/Steam/steamapps/workshop/content/1118520
```

## Cartella di Paralives (Mod locali)

* È possibile accedervi facendo clic sull'icona della cartella di una mod locale nel menu Mod di Paralives.
* Navigando fino a:

**Windows:**

```text
C:\Users\USER\AppData\LocalLow\Paralives\Paralives
```

**Mac:**

```text
~/Library/Application Support/com.Paralives.Paralives/
```

## Paralives\Player.Log

* Può essere letto con qualsiasi programma per la lettura di file di testo, come Notepad o Notepad++.
* Si trova nella cartella Paralives\Paralives.
* Fornisce i log della sessione di Paralives corrente o dell'ultima sessione giocata.

## Cartella Paralives\MySavedGames.mod

* Cartella contenente tutti i salvataggi correnti e i salvataggi automatici.
* Si trova nella cartella Paralives\Paralives.
* Questa cartella è più importante di qualsiasi altra.
* Crea regolarmente una copia completa di questa cartella e conservala in un luogo sicuro al di fuori dei file del gioco!

## Cartella Paralives\MyPremadeHouseholds.mod

* Famiglie salvate nella libreria.

## Cartella Paralives\MyPremadeLot.mod

* Lotti salvati nella libreria.

## Cartella Paralives\MyPremadeOutfits.mod

* Outfit salvati nella libreria.

## Cartelle Paralives\Local.mod e 0.mod

* Memorizzano le impostazioni del gioco, come le varianti di colore personalizzate.

---

# Identificare i dati corrotti

I dati corrotti sono costituiti da file che sono stati modificati e non si trovano più nella forma o nella sequenza che il gioco si aspetta.

## File obsoleti

* Il gioco è stato aggiornato e questi file non rispettano più la sintassi attuale.
* Anche se questo può accadere occasionalmente con le mod, quasi tutti i plugin BepInEx di code injection diventano obsoleti dopo un aggiornamento del gioco.
* Se un plugin BepInEx è installato ma le mod continuano a non funzionare, il plugin potrebbe causare più problemi che benefici.

## File modificati in modo errato

* Questi file sono stati modificati da un giocatore, un modder o persino dal motore di gioco e ora sono errati.
* Questo può accadere quando mod o plugin vengono utilizzati e poi rimossi.

Ad esempio, una mod utilizzata per aggiungere un outfit personalizzato può essere rimossa mentre l'outfit continua a essere identificato nei file del gioco.

Potrebbe essere impossibile rimuovere alcune mod senza danneggiare un file di salvataggio.

## File spostati in modo errato

* I file vengono spesso spostati dal giocatore, dal motore di gioco o da Steam e alcune parti del file vengono lasciate indietro o eliminate.

## Come farà il gioco a indicarmi quali file sono corrotti?

Il motore di gioco cercherà di informare l'utente quando si verifica un errore tramite notifiche dirette e indirette.

### Dirette:

* Popup sullo schermo
* Notifiche nella console
* Eventi nel player.log

### Indirette:

* Sfarfallio
* Lampeggiamenti
* Scatti
* Lag
* Arresti anomali
* Operazioni annullate

## Leggere la console degli errori e Player.Log

I report della console degli errori e di player.log si sovrappongono solo parzialmente, quindi è importante controllare entrambi quando si cerca di identificare un errore.

È importante identificare l'errore iniziale e ignorare gli errori aggiuntivi causati dal primo errore. Quando leggi il registro degli errori, cerca di risolvere gli errori dall'alto verso il basso in ordine sequenziale.

Se vengono introdotti più errori contemporaneamente, può essere molto difficile effettuare una diagnosi. È importante apportare solo un piccolo numero di modifiche tra un test e l'altro.

Se il gioco funziona senza problemi, prendi nota degli errori nel log in modo da poterli escludere in seguito quando qualcosa smette di funzionare.

### CONSOLE DEGLI ERRORI

* La console degli errori è accessibile nel gioco come scheda del menu dei trucchi.
* Non può essere utilizzata se il gioco non si avvia.

1. Premi Ctrl+Shift+C per aprire il menu dei trucchi.
2. Premi la carota per passare alla scheda della console.
3. La console è suddivisa in tre categorie di importanza.
4. Solo gli errori rossi sono importanti per questo tutorial.

### PLAYER.LOG E PLAYER-PREV.LOG

* Questo file registra le azioni eseguite dal motore di gioco Unity che esegue Paralives.
* Player.log viene sovrascritto ogni volta che il gioco viene avviato e spostato in Player-prev.log.
* Si trova nella cartella delle mod locali Paralives\Paralives.
* È possibile inserire più informazioni nel log abilitando le opzioni nel pannello di controllo. Troppe opzioni possono far aumentare rapidamente le dimensioni del log.
* Se qualcosa nel log è importante, fanne una copia!

### Errori buoni (almeno non cattivi):

```text
+ Meta cache is expired
+ Loaded asset database (No metacache) of mod Local.mod in 0.06581748 seconds
+ The referenced script on this Behaviour (Game Object 'SlackService') is missing!
+ Serialization depth limit 10 exceeded
+ Loaded asset database of mod MyPremadeLot.mod in 0.04702377 seconds
+ Unloading 10 unused Assets to reduce memory usage
```

### Errori cattivi:

```text
- NullReferenceException: Object reference not set to an instance of an object
- Material builder got given parameters that don't match any shaders
- Could not resolve 'ProceduralRig/ReachWithLeftArm/ArmLChainIK/TargetArmLChainIK'
- FileNotFoundException
- Failed to find setting class
- Could not register Paralives Town.saved
```

> Nota: nella versione 1.7 ci sono tre nuovi errori rossi nella console e nel player.log che non sembrano influire negativamente sulle prestazioni del gioco.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Nota: nella versione 1.8A, l'importatore .fbx non funzionava correttamente e rimaneva bloccato nella schermata di importazione degli asset.

---

# Tipi di errori

I tipi di problemi che si verificano a livello tecnico.

## Riferimento nullo

* A volte chiamato riferimento a puntatore nullo.
* Qualsiasi errore relativo a un'impostazione, un elemento, una mesh o un valore che non è stato trovato.
* Il gioco fa riferimento a un oggetto che non riesce a trovare oppure non ha capito cosa ha trovato.

> Nota: il gioco è in grado di gestire alcuni riferimenti nulli e diversi di essi fanno parte della versione Early Access del gioco.

## Fuori dai limiti

* Al gioco è stato fornito un valore al di fuori dell'intervallo previsto.
* Se il gioco si aspetta un valore compreso tra 0 e 10 ma riceve il valore 10842, potrebbe verificarsi un errore.

## Traduzione

* Il gioco ha cercato di correggere un file che aveva determinato essere danneggiato, ma il risultato non era corretto.

Ad esempio, un problema con i file .tmp, ⁠.mod.meta e .tmp

## Sintassi

* Il gioco è stato aggiornato e la mod non è più conforme agli standard stabiliti dal gioco. È più comune con i plugin BepInEx di code injection.
* Ad alcune mod create quando il gioco è stato lanciato mancano i due punti nel file di testo.

---

# Categorie dei sintomi

Quando la causa dell'errore è sconosciuta, l'obiettivo è correlare i sintomi a una causa specifica. Dopo aver risolto ogni errore, il gioco dovrebbe funzionare. Queste sono categorie arbitrarie per aiutare a raggruppare errori simili in gruppi.

È importante identificare l'errore iniziale e ignorare gli errori aggiuntivi causati dal primo errore.

## Cat A — Avvio del gioco

### Sintomi

* Il gioco non riesce ad arrivare al menu principale di Paralives
* Lo schermo è nero
* Il gioco si arresta in modo anomalo quando viene avviato da Steam
* Viene visualizzato un errore quando si avvia il gioco da Steam
* Il gioco rimane bloccato su un'immagine di nuvole.

### Possibili soluzioni

* Verifica che l'hardware soddisfi i requisiti minimi per giocare a Paralives.
* Un file critico utilizzato durante l'avvio del gioco è corrotto, illeggibile o inaccessibile.
* Inizia verificando i file del gioco.
* Crea un'eccezione per Paralives nell'antivirus.
* Controlla player.log nella cartella delle mod locali paralives/paralives per verificare la presenza di errori.

## Cat B — Importazione degli asset

### Sintomi

* Bloccato durante l'importazione degli asset

### Possibile causa

Un file di una mod è illeggibile.

### Possibili soluzioni

* Rimuovi le mod più recenti dalla cartella delle mod locali paralives/paralives o dalle cartelle di Steam Workshop fino a quando il problema non viene risolto.
* Verifica i file del gioco.

## Cat C — Selezione di un salvataggio

### Sintomi

* Il gioco torna al menu principale quando si tenta di caricare un salvataggio
* Il file di salvataggio è bianco

### Possibile causa

Il file di salvataggio ha nomi di file errati, mancano dei file oppure il file non è leggibile.

### Possibile soluzione

Inizia controllando che il nome del salvataggio corrisponda ai file meta al suo interno e che il salvataggio contenga tutti i componenti necessari.

## Cat D — Caricamento di un salvataggio

### Sintomi

* Il gioco si blocca durante il caricamento del salvataggio
* Il gioco rimane per sempre nella schermata di caricamento

### Possibile causa

Una mod corrotta, una mod rimossa in modo errato o la corruzione del file di salvataggio, come un errore di riferimento nullo.

Potrebbe essere impossibile rimuovere alcune mod senza danneggiare un file di salvataggio.

### Possibile soluzione

Verifica se gli errori persistono in un nuovo salvataggio.

## Cat E — Modalità Live

### Sintomi

* Il gioco si blocca o si congela quando si apre un menu in modalità Live
* Il gioco si blocca o si congela quando si esegue un'azione specifica in modalità Live

### Possibile causa

Una mod corrotta, una mod rimossa in modo errato o la corruzione del file di salvataggio, come un errore di riferimento nullo.

Potrebbe essere impossibile rimuovere alcune mod senza danneggiare un file di salvataggio.

### Possibile soluzione

Verifica se gli errori persistono in un nuovo salvataggio.

## Cat F — Menu

### Sintomi

* Il menu del gioco non si apre quando viene cliccato
* Il menu del gioco è vuoto quando viene cliccato
* Il menu del gioco non si chiude

### Possibile causa

Una mod corrotta, una mod rimossa in modo errato o la corruzione del file di salvataggio, come un errore di riferimento nullo.

Potrebbe essere impossibile rimuovere alcune mod senza danneggiare un file di salvataggio.

### Possibile soluzione

Verifica se gli errori persistono in un nuovo salvataggio.

## Cat G — Installazione delle mod

### Sintomi

* Le mod non si installano

### Possibili soluzioni

* Controlla le cartelle delle mod di Steam e locali per verificare la presenza di file parziali.
* Elimina i file di mod corrotti che impediscono il download.

## Cat H — Mod mancanti

### Sintomi

* Le mod installate non vengono visualizzate nel menu delle mod
* Le mod installate vengono visualizzate nel menu delle mod ma non nel gioco

### Possibili soluzioni

* Controlla la presenza di mod corrotte.
* Controlla la presenza di file di mod duplicati.

## Cat I — Convalida delle mod

### Sintomi

* Gli elementi delle mod installate non vengono visualizzati quando vengono equipaggiati a un personaggio
* Gli elementi delle mod installate sono scomparsi
* Un personaggio con elementi di una mod è scomparso
* Gli elementi delle mod hanno un aspetto strano
* Gli elementi delle mod interagiscono in modo imprevisto
* Gli elementi delle mod hanno il colore, la forma o le dimensioni errate

### Possibile soluzione

Controlla la presenza di mod corrotte.

---

> **Esegui un backup completo dei tuoi file di salvataggio prima di tentare uno qualsiasi di questi passaggi!**

---

# Come rimuovere i dati corrotti

Ordinato per livello di difficoltà e complessità.

## Facile

### Disattivare e riattivare le mod

* A volte le mod non vengono inizializzate correttamente e questo può essere risolto disattivando e riattivando una sola mod utilizzando il menu delle mod nel gioco.

### Riavviare Paralives

* Il gioco dispone di protezioni contro i dati corrotti che si attivano quando il gioco viene avviato.
* Può sembrare sciocco, ma riavviare il gioco più volte può essere efficace in alcuni casi.

### Avviare un nuovo salvataggio

* Se gli errori sono troppo complicati o non possono essere risolti, iniziare un nuovo salvataggio potrebbe essere l'opzione migliore.

### Verificare i file del gioco o reinstallare il gioco utilizzando Steam

* Nel client Steam, con il gioco chiuso:

  * Steam > Paralives > Proprietà > Verifica integrità dei file di gioco

### Iscriversi nuovamente a tutte le mod per eliminare i file corrotti

1. Aggiungi tutte le mod a cui sei iscritto a una raccolta personalizzata
2. Annulla l'iscrizione a tutte le mod
3. Iscriviti a tutte le mod della raccolta

### Rimuovere le mod finché la mod corrotta non viene rimossa

* Rimuovi una mod alla volta oppure utilizza il metodo 50/50 per rimuovere metà delle mod finché non viene identificata quella corrotta.
* Le mod possono continuare a causare bug anche quando sono disattivate. Devono essere rimosse completamente spostando, annullando l'iscrizione o eliminando i file delle mod.
* Potrebbe essere necessario riavviare il gioco tra un test e l'altro per assicurarsi che i file memorizzati nella cache vengano eliminati.
* Documenta i risultati e annota quali mod funzionano!

### Iscriversi nuovamente alle mod lentamente per assicurarsi che vengano installate correttamente

* La teoria è che installare troppe mod contemporaneamente causi errori, quindi installa le mod lentamente.
* Il gioco è progettato per installare rapidamente le mod, ma forse c'è qualcosa di vero in questo.

---

## Intermedio

### Spostare le mod di Steam Workshop nella cartella delle mod locali Paralives\Paralives

* Le mod installate localmente vengono interpretate in modo diverso dal motore di gioco, il che potrebbe risolvere l'errore.
* Quando il gioco non è in esecuzione, apri Esplora file e torna alla cartella delle mod di Steam Workshop:

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```
* Inserisci ".mod" nella barra di ricerca. Se non ottieni risultati, prova "*.mod".
* Verranno visualizzate le cartelle contenenti le mod all'interno della cartella Steam Mods.
* Seleziona, taglia e incolla tutte le cartelle .mod nella cartella delle mod locali Paralives\Paralives.
* Tutte le cartelle devono essere spostate contemporaneamente.
* Quindi annulla l'iscrizione alle mod per impedire a Steam di copiarle nuovamente.
* Assicurati che la copia nella cartella delle mod di Steam Workshop sia stata eliminata correttamente, poiché avere due copie della stessa mod può causare errori.

### Eliminare eventuali file rimasti nelle cartelle delle mod di Steam Workshop

* Torna a workshop\content\1118520\ e rimuovi tutti i file che non sono stati eliminati correttamente.
* Presta attenzione ai dettagli, poiché piccoli errori saranno difficili da trovare in seguito.
* È molto probabile che i file residui causino errori quando il gioco non li prevede.

### Utilizzare i comandi della console per riparare un salvataggio corrotto rimuovendo i dati corrotti

* `CLEARALLOCCUPATIONS` eliminerà tutti i lavori e la cronologia lavorativa del para selezionato e non può essere annullato.
* `CLEARCHARACTEROUTFITS` eliminerà tutti gli outfit del para selezionato e non può essere annullato.
* `CLEARINVENTORY` svuota l'inventario del para selezionato e non può essere annullato.
* Il tutorial collegato di seguito spiega i comandi cheat disponibili.

Tutorial per i comandi cheat ⁠Console and Cheat Commands

### Installare un plugin di code injection per gestire gli errori delle mod

* Questi plugin funzionano dando al motore di gioco più tempo per elaborare ogni file di mod e aiutando il motore di gioco a diagnosticare gli errori.
* I plugin possono anche causare ulteriore corruzione dei dati se non vengono mantenuti e aggiornati correttamente.
* Si spera che i plugin diventino inutili man mano che gli sviluppatori di Paralives aggiungeranno al gioco più codice per la correzione degli errori.

Paralines Launcher Plugin ⁠Paraline Launcher [Help | Bug R…

---

## Avanzato

### Eliminare la cartella delle mod locali

* Questo è necessario per ottenere un nuovo inizio completo.
* Potrebbe essere necessario disattivare Steam Cloud per impedire il ripristino dei file corrotti durante i test.

1. Taglia e incolla la cartella delle mod locali in un luogo sicuro al di fuori dei file del gioco, come il desktop
2. Verifica i file del gioco utilizzando Steam
3. Riavvia il gioco. All'avvio, Paralives rigenererà l'intera cartella delle mod locali da zero.
4. Verifica che sia stata generata una nuova cartella delle mod locali.
5. Controlla se il problema è stato risolto.

   * Sì: reintroduci i file importanti dalla copia creata al passaggio 1.
   * No: prova altri metodi per risolvere il problema prima di reintrodurre i vecchi file.
6. Aggiungi alla cartella Paralives appena generata solo i file ritenuti sicuri per ridurre la possibilità di copiare file di dati corrotti.

### Modificare direttamente i file di salvataggio per rimuovere i dati corrotti

* I file di salvataggio sono file di testo e possono essere modificati direttamente.
* È possibile utilizzare qualsiasi editor di testo, ma è preferibile Notepad++ con un plugin per la formattazione dei file JSON.
* Il tutorial collegato di seguito spiega come sono formattati i file di salvataggio.

Spiegazione della cartella delle mod locali ⁠Mod Folder/Save Folder

### Spostare parti sicure di un salvataggio in un nuovo file di salvataggio

* Quando non è possibile identificare il problema del salvataggio, sposta piccole parti in un nuovo salvataggio.
* Questo metodo può essere utile quando si cerca di identificare i file corrotti.
* Ad esempio, le cartelle delle famiglie possono essere trascinate tra i salvataggi con una perdita di dati relativamente minima.
* Il tutorial collegato di seguito spiega come sono formattati i file di salvataggio.

Spiegazione della cartella delle mod locali ⁠Mod Folder/Save Folder

### Utilizzare i comandi della console per ricostruire i personaggi in un nuovo salvataggio

* Quando tutto è perduto, forse è meglio ricominciare da capo con un nuovo salvataggio, ma con un piccolo vantaggio iniziale.
* Comandi come `SETMONEY` possono essere utilizzati per aggiungere denaro.
* I comandi possono essere utilizzati per ripristinare abilità, ricette e altro.
* Il tutorial collegato di seguito spiega i comandi cheat disponibili.

Tutorial per i comandi cheat ⁠Console and Cheat Commands

---

> **Esegui un backup completo dei tuoi file di salvataggio prima di tentare uno qualsiasi di questi passaggi!**

# "La soluzione abituale"

Il metodo drastico per risolvere la maggior parte dei problemi eliminando ogni file associato al gioco per ottenere il miglior nuovo inizio possibile. Non consiglio questa soluzione per tutti i problemi perché potrebbe rendere ingiocabili i vecchi salvataggi modificati senza le mod da cui dipendono per funzionare correttamente.

## Eliminare tutti i file del gioco per un nuovo inizio

1. Elimina i file del gioco tagliando e incollando l'intera cartella delle mod locali paralives/paralives sul desktop.
2. Annulla l'iscrizione a tutte le mod di Steam Workshop ed elimina eventuali file di mod rimasti.
3. Verifica i file del gioco utilizzando Steam oppure reinstalla il gioco.
4. Riavvia Paralives.
5. Avvia un nuovo salvataggio.
6. Se ora il gioco funziona, annulla lentamente le modifiche finché il problema non si ripresenta e saprai quale ne è la causa.

---

# Prevenire la corruzione dei dati

## Fai copie di TUTTO e SPESSO

* Crea una copia fisica dei file importanti in un luogo sicuro, come il desktop, al di fuori dei file del gioco.
* I file accessibili dal motore di gioco di Paralives possono sempre essere danneggiati.

> Nota: il comando ZIPSAVEFILE creerà una copia del salvataggio corrente sul desktop. Potrebbe sovrascrivere la vecchia copia se il comando viene utilizzato due volte.

Tutorial per i comandi cheat ⁠Console and Cheat Commands

`ZIPSAVEFILE` crea uno ZIP del file di salvataggio corrente sul desktop.

## Leggi le recensioni delle mod

* E lascia anche tu delle recensioni!
* I commenti sulle mod sono il modo in cui i modder e gli altri utenti condividono informazioni sulle mod.
* Se la mod sembra non funzionare, informa il modder in modo che possa risolvere il problema!

## Disattivare Steam Cloud

* Steam Cloud è ottimo per proteggere i file importanti, ma a volte causa problemi difficili da individuare.
* Steam Cloud tende a riportare indietro file scaduti senza avvisare nessuno e semplicemente li inserisce lì perché tu li trovi in seguito.

## Rimuovere correttamente le mod

* Le mod aggiungono riferimenti agli oggetti nel gioco.
* Ogni istanza di questi oggetti deve essere rimossa manualmente dal salvataggio PRIMA di rimuovere la mod.
* È molto più facile rimuovere gli oggetti delle mod nel gioco piuttosto che modificando un file di salvataggio.
* Elimina quel divano elegante e quel maglione divertente prima di rimuovere la mod!

## Aggiornare i driver

* Per questo tutorial, il driver su cui concentrarsi è quello della scheda grafica (GPU).
* Su Windows, scarica l'app Nvidia o AMD e installa il nuovo driver ogni pochi mesi.

## Aggiornare il sistema operativo

* Sì, che schifo, ma è importante!
* Esegui regolarmente software di aggiornamento integrati come Windows Update.

## Installa le mod lentamente e controlla le mod installate singolarmente o in piccoli gruppi

* Questo potrebbe aiutare il gioco a elaborare ogni file senza commettere errori.

## Manutenzione preventiva dell'hardware

* Prenditi cura del computer e lui si prenderà cura di te.
* Installa ed esegui software anti-malware ottenuto in modo sicuro.
* Controlla la presenza di danni fisici e pulisci la polvere.
* Esegui i programmi integrati per controllare lo stato e la stabilità dei componenti.

---

# Altre risorse

## Discussioni sui problemi delle mod (dove trovo i miei soggetti di test)

* Consigli degli sviluppatori per la risoluzione dei problemi
  https://steamcommunity.com/app/1118520/discussions/1/569288683937662349/
* Mega thread sulle mod mancanti
  https://discord.com/channels/595045400805769238/1517352862395404499
* Le mod non vengono caricate
  https://discord.com/channels/595045400805769238/1517449529174130779
* Errori di riferimento nullo
  https://discord.com/channels/595045400805769238/1517532031662424154
* Errori di riferimento nullo
  https://discord.com/channels/595045400805769238/1513991069379858515/1517000216207822899
* File di mod corrotti
  https://discord.com/channels/595045400805769238/1517266950944981062
* Wiki di Paralives
  https://paralives.wiki.gg/wiki/Portal:Modding_guides
* Registro delle modifiche di Paralives
  https://www.paralives.com/news
* Sviluppo di Paralives
  https://www.paralives.com/development
* Roadmap di Paralives
  https://paralives.notion.site/f138c4f6cb234604be16fe4198d17f51
* Bug noti
  https://discord.com/channels/595045400805769238/1508927230154244216
* Roadmap di Paralives
  https://paralives.notion.site/f138c4f6cb234be16fe4198d17f51
* Bug noti
  known-issues-and-bugs
