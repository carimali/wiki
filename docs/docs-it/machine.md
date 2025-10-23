# Stato della Macchina

La sezione **Stato della Macchina** consente di visualizzare tutte le informazioni operative relative a una singola macchina collegata a **CARIcare**.

<sup style='font-size:15px'>Per accedere alla sezione, selezionare il riquadro</sup> ![Icona occhio](_images/icona-occhio.png) <sup style='font-size:15px'>corrispondente alla macchina desiderata.</sup>

<kbd>![machine-1](_images/machine-1.png)</kbd>

Da questo momento in poi, tutti i dati visualizzati faranno riferimento esclusivo alla macchina selezionata.
L’interfaccia è composta da tre schede principali:

* **Manutenzione**
* **Ricette**
* **Impostazioni**
* **Storici**
* **Parametri** (Solo per linea SilverAce con ultima versione firmware)

---

## Manutenzione

<kbd>![machines-page-6](_images/machines-page-6.png)</kbd>

La scheda **Manutenzione** è un’area informativa che riporta lo stato dei componenti e le scadenze delle manutenzioni programmate.
Le informazioni disponibili includono:


### Modulo Erogazioni

Il modulo **Erogazioni** consente di analizzare in dettaglio l’attività di erogazione della macchina selezionata.
I dati vengono rappresentati in forma grafica per facilitare il monitoraggio delle bevande distribuite in un determinato periodo.

<kbd>![manutenzione-1](_images/manutenzione-1.png)</kbd>

#### Struttura del modulo

Il modulo è composto da tre sezioni principali:

* **Filtri temporali e di selezione**
* **Grafico delle erogazioni**
* **Strumenti di esportazione**



#### Filtri temporali e di selezione

Nella parte superiore sono presenti i campi per impostare il periodo e i criteri di analisi:

* **Intervallo di tempo**
  Permette di selezionare il periodo da analizzare (ultima settimana, ultime due settimane, ultimo mese, periodo personalizzato).
  Il filtro viene applicato automaticamente al grafico una volta premuto **Seleziona date**.

* **Seleziona ricette**
  Consente di limitare la visualizzazione a una o più ricette specifiche tra quelle presenti nella macchina.

* **Tipo di erogazione**
  Permette di filtrare per erogazioni *online* e *offline*



#### Grafici delle erogazioni

Il modulo **Erogazioni** presenta due grafici complementari che mostrano le stesse informazioni su scale temporali differenti, consentendo un’analisi completa dell’attività della macchina.

**Grafico 1**

Rappresenta la quantità totale di bevande erogate per giorno nel periodo selezionato.
Ogni colonna indica una giornata, mentre i colori identificano le diverse ricette o tipologie di bevanda.

* L’asse **orizzontale** mostra i giorni compresi nell’intervallo selezionato.
* L’asse **verticale** riporta il numero totale di erogazioni.

Questo grafico consente di valutare l’andamento generale dell’attività, evidenziando variazioni nel consumo e nei volumi di erogazione nel corso della settimana o del mese.

<kbd>![manutenzione-2](_images/manutenzione-2.png)</kbd>

**Grafico 2**

Mostra la distribuzione delle bevande erogate durante le diverse ore della giornata.
Ogni colonna rappresenta un’ora (da 00:00 a 23:00), e la suddivisione cromatica consente di distinguere le diverse tipologie di bevande.

<kbd>![manutenzione-3](_images/manutenzione-3.png)</kbd>

Questo grafico permette di:

* Identificare le **fasce orarie di maggiore utilizzo** della macchina.
* Analizzare i **picchi di consumo** in relazione al tipo di bevanda erogata.
* Pianificare in modo più efficiente **manutenzioni** o **rifornimenti** in base agli orari di massimo carico operativo.



#### Strumenti di esportazione e analisi

Sotto il grafico **1** sono presenti tre pulsanti di funzione:

* **Raggruppa per ricette**
  Riorganizza il grafico e i dati visualizzati mostrando le erogazioni aggregate per singola ricetta, anziché per data.

* **Esporta dati di erogazione in CSV**
  Genera un file **CSV** contenente i dati dettagliati delle erogazioni (ricetta, quantità, data e ora).
  Il file può essere utilizzato per analisi statistiche o integrazione con sistemi gestionali esterni.

* **Esporta contatori in CSV**
  Crea un file **CSV** con i contatori globali e parziali della macchina nel periodo selezionato.
  Utile per verificare il consumo complessivo e l’attività operativa in un intervallo definito.

---

### Temperature

<kbd>![manutenzione-4](_images/manutenzione-4.png)</kbd>

Il modulo **Temperature** mostra in tempo reale le temperature rilevate dai sensori principali della macchina:

* **Caffè** – Temperatura della caldaia caffè.
* **Vapore** – Temperatura della caldaia vapore.

Le informazioni sono aggiornate periodicamente e consentono di verificare la stabilità termica del sistema.
Un valore anomalo può indicare un malfunzionamento del gruppo caffè o del circuito di riscaldamento.

---

### Erogazioni

<kbd>![manutenzione-5](_images/manutenzione-5.png)</kbd>

Il modulo **Erogazioni** visualizza i dati relativi al numero di bevande distribuite:

* **Contatore Globale** – Numero totale di erogazioni effettuate dalla macchina.
* **Contatore Parziale** – Numero di erogazioni registrate dall’ultimo azzeramento.

Premendo **Mostra**, è possibile visualizzare il dettaglio completo delle erogazioni suddivise per tipologia di bevanda.
I dati sono aggiornati automaticamente a intervalli regolari.

---

### Lavaggi

<kbd>![manutenzione-6](_images/manutenzione-6.png)</kbd>

Il modulo **Lavaggi** riporta il numero di cicli di lavaggio effettuati dai vari componenti della macchina:

* **All in One** – Numero complessivo di cicli completi.
* **Gruppo** – Cicli di lavaggio eseguiti sul gruppo caffè.
* **Milker** – Cicli di lavaggio del sistema latte.
* **Mixer** – Cicli di lavaggio dei miscelatori interni.

Queste informazioni permettono di monitorare la corretta esecuzione delle operazioni di manutenzione ordinaria.

---

### Calibrazioni

<kbd>![manutenzione-7](_images/manutenzione-7.png)</kbd>

Il modulo **Calibrazioni** mostra i valori correnti di taratura relativi ai dosatori della macchina:

* **Macinino 1 / 2** – Quantità di caffè macinato per secondo (*gr/s*).
* **Solubile 1 / 2** – Quantità di prodotto solubile dosata per secondo (*gr/s*).

I valori di calibrazione consentono di controllare la coerenza tra le impostazioni del software e la resa effettiva dei prodotti, garantendo costanza qualitativa e corretto dosaggio.

---

### Mappa e indirizzo

<kbd>![manutenzione-8](_images/manutenzione-8.png)</kbd>

Il modulo **Mappa e indirizzo** mostra la **posizione geografica della macchina** visualizzata nella scheda di stato.
L’area utilizza l’integrazione con **Google Maps** per fornire una localizzazione precisa e interattiva del punto di installazione.

La mappa può essere visualizzata in due modalità:

* **Mappa** – Mostra la vista standard con strade, luoghi e riferimenti principali.
* **Satellite** – Mostra la vista satellitare con immagini reali del territorio.

Sotto la mappa è riportato l’**indirizzo completo di installazione**, comprensivo di via, numero civico, città e codice postale.
Il pulsante **Naviga** apre la posizione direttamente nell’applicazione di navigazione predefinita del dispositivo.

Premendo **Cambia indirizzo**, è possibile aggiornare la posizione associata alla macchina, ad esempio in caso di spostamento o nuova installazione.
L’aggiornamento viene memorizzato automaticamente nella piattaforma e riflesso in tempo reale sulla mappa.

---

### Manutenzione trimestrale

<kbd>![manutenzione-9](_images/manutenzione-9.png)</kbd>

Il modulo **Manutenzione trimestrale** mostra il tempo rimanente prima dell’intervento di manutenzione periodica.
La barra di avanzamento rappresenta il progresso dei giorni trascorsi rispetto al periodo di riferimento (90 giorni).

* **Tutto è OK**: la macchina è entro il periodo operativo sicuro.
* **Giorni rimanenti**: indica il numero di giorni prima del prossimo checkup programmato.
* **Azzera contatore**: consente di ripristinare il contatore dopo l’esecuzione della manutenzione.

  > L’azione non è reversibile.

Il prossimo intervento viene pianificato automaticamente in base alla data mostrata accanto alla barra di stato.

---

### Manutenzione annuale

<kbd>![manutenzione-10](_images/manutenzione-10.png)</kbd>

Il modulo **Manutenzione annuale** segue lo stesso principio della manutenzione trimestrale, ma fa riferimento al controllo periodico su base annuale (365 giorni).
Mostra la **data del prossimo checkup**, i **giorni rimanenti** e la **barra di avanzamento temporale** che indica il livello di completamento del periodo operativo.

Anche in questo caso, il pulsante **Azzera contatore** deve essere utilizzato al termine dell’intervento per ripristinare il ciclo di monitoraggio.

---

### Numero di cicli

<kbd>![manutenzione-11](_images/manutenzione-11.png)</kbd>

Il modulo **Numero di cicli** tiene traccia del numero complessivo di **cicli di erogazione effettuati dal gruppo caffè**.
La barra di avanzamento mostra il numero di cicli eseguiti rispetto alla soglia di manutenzione prevista.

* **Cicli rimanenti**: indica quanti cicli mancano al raggiungimento del limite impostato (ad esempio, 50.000).
* Al superamento della soglia, la macchina richiede una verifica del gruppo erogatore o la sostituzione dei componenti soggetti a usura.

---

### Erogazioni nelle ultime 24 ore

<kbd>![manutenzione-12](_images/manutenzione-12.png)</kbd>

Il modulo **Erogazioni nelle ultime 24 ore** confronta il numero di bevande effettivamente erogate con il **limite massimo giornaliero consigliato**.
Il rapporto viene mostrato sia numericamente (es. 108/200) sia tramite una barra di avanzamento.

Questo modulo consente di monitorare il **livello di utilizzo giornaliero** della macchina e individuare eventuali **sovraccarichi operativi** che potrebbero compromettere la qualità delle erogazioni o ridurre la vita utile dei componenti.

---

### Consumo prodotti

Il modulo **Consumo prodotti** visualizza il livello di utilizzo dei prodotti erogati dalla macchina (caffè in grani e prodotti solubili).
I dati vengono mostrati tramite **grafici ad anello**, che evidenziano la **percentuale utilizzata** e quella **rimanente** per ciascun contenitore.

<kbd>![Consumo Prodotti](_images/manutenzione-13.png)</kbd>

Ogni anello rappresenta un singolo componente della macchina (varia in base al numero di macinici e mixer presenti).

* **Macinino 1 / Macinino 2** – Indicano la quantità di caffè in grani utilizzata dai rispettivi macinini.
* **Solubile 1** – Indica la quantità di prodotto solubile (es. cioccolata o latte in polvere) consumata.

La legenda sotto ciascun grafico distingue chiaramente:

* **Utilizzato (in rosso)** – Percentuale di prodotto già erogata.
* **Rimanente (in verde)** – Percentuale di prodotto ancora disponibile.

Un **triangolo arancione di avviso** accanto al nome del componente segnala che il relativo contatore ha raggiunto o superato il limite impostato.
In questo caso, è necessario procedere con il **reset del contatore**.

#### Azzeramento contatori

Cliccando sull’icona di **avviso (triangolo arancione)** accanto a un componente, si apre una finestra di conferma che consente di **azzerare i contatori di consumo** per i prodotti selezionati.

<kbd>![Azzeramento Contatori](_images/manutenzione-14.png)</kbd>

Premendo **Conferma**, il sistema azzera i valori di consumo e ripristina il conteggio per i cicli successivi.
Il pulsante **Cancella** consente invece di annullare l’operazione senza apportare modifiche.

> ⚠️ **Attenzione:** l’azzeramento dei contatori è un’azione permanente e non può essere annullata.
> È consigliato eseguirla solo dopo il reale rifornimento dei prodotti.

---

## Ricette

  <kbd>![machines-page-7](_images/machines-page-7.png)</kbd>

La scheda **Ricette** consente di gestire le ricette installate sulla macchina, modificare i parametri di erogazione, esportare o importare configurazioni e inviare le modifiche direttamente al dispositivo connesso.


### Struttura del menu

La parte superiore mostra la macchina selezionata e il menu a tendina **Importare un set di ricette**, da cui è possibile caricare un set precedentemente salvato.

<kbd>![Importa Ricette](_images/ricette.png)</kbd>

Sotto è visibile una finestra che mostra le **ricette disponibili** (*abilitate* e *disabilitate*), visualizzabili in due modalità:

* **Vista griglia**: anteprime grafiche delle bevande, corrisponde alla visualizzazione lato utente in macchina.

<kbd>![Lista Ricette](_images/ricette-1.png)</kbd>

* **Vista elenco**: con visualizzazione testuale ordinata.

<kbd>![Lista Ricette](_images/ricette-2.png)</kbd>

È possibile definire il **numero di ricette per pagina** e selezionare una specifica bevanda per modificarne i parametri.

Attivando l’opzione **Mostra disabilitate**, vengono visualizzate anche le ricette momentaneamente non abilitate.


### Parametri generali della ricetta

La parte superiore della scheda di configurazione contiene i **parametri comuni a tutte le ricette**, indipendentemente dal tipo di bevanda o modello di macchina.


* **Etichetta**
  Indica il **nome visualizzato** della bevanda nel menu della macchina.
  Può essere modificato liberamente per adattarsi alla lingua o alla nomenclatura del cliente (es. *Espresso corto*, *Doppio espresso*, *Latte caldo*).

* **Abilitato / Disabilitato**
  Definisce se la ricetta è **attiva** e quindi visibile all’utente sulla macchina.
  Le ricette disabilitate restano salvate nel sistema ma non appaiono nel menu principale della macchina.

* **Icona**
  Permette di selezionare l’**immagine rappresentativa** della bevanda tra quelle disponibili.
  L’icona scelta sarà mostrata sul display della macchina o nella vista ricette del portale.

* **Numero di prodotti**
  Specifica il **numero di ingredienti o componenti** coinvolti nella ricetta (ad esempio: caffè + latte, caffè + cioccolata).
  Il valore impostato influisce sui parametri successivi, che varieranno in base al numero di prodotti selezionato.


### Parametri specifici della ricetta

La parte inferiore della scheda di configurazione contiene i **parametri specifici**, che variano in base al **tipo di prodotto** selezionato nei campi generali.

<kbd>![Parametri Specifici Ricetta](_images/ricette-4.png)</kbd>

Questi parametri definiscono il **comportamento tecnico dell’erogazione** e le **caratteristiche operative** del singolo ingrediente (ad esempio latte, caffè o prodotti solubili).
Ogni prodotto dispone di un insieme dedicato di voci.

I valori impostati determinano le **sequenze di lavoro della macchina** durante la preparazione della bevanda e influenzano direttamente la **qualità finale del prodotto erogato**.

> **Nota:** la struttura e il numero dei parametri visualizzati dipendono dal tipo di macchina e dal prodotto selezionato.
> Per una descrizione dettagliata dei singoli campi, fare riferimento al **manuale tecnico del modello**.


Le modifiche possono essere applicate direttamente dal pannello e sono equivalenti a quelle effettuabili dalla macchina fisica.
Al termine della configurazione, è necessario **salvare o inviare le modifiche** utilizzando i pulsanti presenti in basso.


### Operazioni disponibili

<kbd>![Pulsanti Ricette](_images/ricette-5.png)</kbd>

* **Salva le ricette**
  Registra il set di ricette attualmente configurato e lo aggiunge all’elenco disponibile nel menu **Importa set di ricette**.

* **Invia le ricette alla macchina**
  Trasmette in tempo reale le impostazioni modificate alla macchina selezionata, sovrascrivendo quelle precedenti.

> **Nota:** le modifiche devono essere salvate o inviate prima di uscire dalla sezione, altrimenti i dati non verranno mantenuti.

### Accessibilità e permessi

Tutti i set di ricette salvati sono condivisi tra gli utenti del gruppo CARIcare con **livello di autorizzazione adeguato**.
Le funzioni di esportazione e invio alla macchina sono riservate ai **ruoli tecnici o amministrativi** abilitati.

---

## Impostazioni

<kbd>![machines-page-8](_images/machines-page-8.png)</kbd>

La scheda **Impostazioni** consente di visualizzare i parametri generali della macchina, la versione attuale del firmware, configurazioni e soglie di consumo, nonché accedere a dati tecnici e operativi.
Tutte le impostazioni riguardano la singola macchina selezionata e vengono sincronizzate automaticamente con il sistema **CARIcare**.


### Configurazione della macchina

<kbd>![Impostazioni](_images/impostazioni-1.png)</kbd>

Visualizza le **informazioni tecniche principali** relative al modello, tra cui:

* Numero di serie
* Tipo di macchina
* Versione software e firmware
* Tipologia di display
* Stato operativo

> **Nota:** questa sezione è **visualizzabile solo selezionando una macchina superautomatica** (attualmente linea *SilverAce*).


### Firmware

<kbd>![Impostazioni](_images/impostazioni-2.png)</kbd>

Mostra la **versione firmware attualmente installata** e la **data dell’ultimo aggiornamento**.


### Sistema di pagamento

<kbd>![Impostazioni](_images/impostazioni-3.png)</kbd>

Indica il **sistema di pagamento configurato** sulla macchina (es. libero, a gettoni o con tessera).
Le informazioni sono di sola lettura e variano a seconda della configurazione locale.

> **Disponibile solo per macchine superautomatiche.**


### Lingua

<kbd>![Impostazioni](_images/impostazioni-4.png)</kbd>

Permette di impostare la **lingua principale** visualizzata sull’interfaccia della macchina, selezionandola dal menù a tendina.
Nei modelli compatibili è possibile configurare anche una **seconda lingua**.


### Fuso orario

<kbd>![Impostazioni](_images/impostazioni-5.png)</kbd>

Consente di sincronizzare il **fuso orario** tra la macchina e il browser.
In questo modo gli orari delle erogazioni, delle manutenzioni e degli aggiornamenti vengono registrati in modo coerente con la zona impostata.


### Brewer

<kbd>![Impostazioni](_images/impostazioni-6.png)</kbd>


Mostra i **parametri tecnici del gruppo caffè**, inclusi tipo, configurazione e stato del modulo.
Queste informazioni sono utili per la diagnostica e la manutenzione.

> **Disponibile solo per macchine superautomatiche.**


### Consumo prodotti

<kbd>![Impostazioni](_images/impostazioni-7.png)</kbd>

Permette di impostare la **quantità di prodotto (kg)** iniziale per ogni contenitore, al fine di monitorarne il consumo residuo.
Dopo aver inserito o aggiornato i valori, premere **Salva** per applicare le modifiche.

> **Disponibile solo per macchine superautomatiche.**


### Data prevista per la manutenzione straordinaria

<kbd>![Impostazioni](_images/impostazioni-8.png)</kbd>

Consente di **pianificare la data della prossima manutenzione** e di aggiungere eventuali note operative.
I dati vengono salvati e visualizzati anche nella sezione **Manutenzione** della macchina.


### Azzeramento e aggiornamento dei contatori

<kbd>![Impostazioni](_images/impostazioni-9.png)</kbd>

Questa sezione permette di eseguire azioni di manutenzione o sincronizzazione sui contatori macchina:

* **Azzera contatori** – Riporta tutti i contatori a zero.
* **Aggiorna contatori ricetta** – Aggiorna solo i contatori relativi alle erogazioni.
* **Aggiornamento completo** – Sincronizza tutte le informazioni macchina con il server.
* **Aggiorna configurazione macchina** – Ricarica la configurazione salvata.
* **Aggiorna parametri** – Aggiorna solo i parametri tecnici, senza modificare i contatori.

---
