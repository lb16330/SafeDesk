# SafeDesk
Evitare spostamenti ed assembramenti per accedere ad uno sportello.

*"Fare la fila è un esercizio di pazienza aspettando che sia il tuo turno."*  però **non deve essere un esercizio pericoloso** come lo è diventato in questo periodo nel quale spostamenti e assembramenti sono, se possibile da evitare.

Da questa riflessione nasce la proposta di realizzare una soluzione, possibilmente open source da offrire fin da subito.

La soluzione può essere perfezionata e può creare un nuovo mercato basato sulla capacità di personalizzare ove necessario sulla base delle peculiarietà dello sportello.

Lancio quindi un appello alla websphera che legge quanto scrivo per proporre il formarsi di un community con l'obiettivo di raffinare/migliorare la proposta e di porla a disposizione del mercato.
# Esigenze

Ridurre quanto possibile spostamenti e presenze presso uffici (pubblici e privati) di operatori ed utenti, mantenendo comunque elevata l’interazione umana.

Abilitare l’adozione di un orario flessibile di fruizione degli sportelli all’utenza sorpassando i limiti dovuti dalla logistica del luogo fisico di lavoro.
# Proposta

Realizzazione di una soluzione basata su strumenti digitali per la “remotizzazione” degli sportelli.

# Riferimenti normativi

DECRETO-LEGGE 19 maggio 2020, n. 34 art 263 comma 1

...A tal fine,(NDR le amministratzioni) organizzano il lavoro dei propri dipendenti e l'erogazione dei servizi attraverso la flessibilita' dell'orario di lavoro, rivedendone l'articolazione giornaliera e settimanale, introducendo modalita' di interlocuzione programmata, anche attraverso soluzioni digitali e non in presenza con l'utenza.

# La soluzione

Dispiegare un “gestore di sportello” (simile ai servizi “taglia coda” o “waiting room”) che permetta all’utente di selezionale il servizio/sportello di interesse.

Il gestore di sportello mette in attesa l’utente, segnalando quanti altri utenti sono presenti in coda e debbano essere servizi prima del proprio turno.

Il gestore dello sportello permette agli operatori di dichiararsi disponibili ad accettare un nuovo utente,in questo caso il gestore dello sportello crea una stanza di video conferenza dedicata alla sessione di sportello e vi indirizza dia l’operatore che il primo utente presente in coda


# Applicazione pratiche


Lo sportello remoto può avere varie applicazioni pratiche, dalla sanità all'urp, ma puà essere offerto anche agli enti del territorio e addirittura come supporto all'imprenditoria privata e agli sportelli privati.

Inoltre, per l’utenza che necessita di supporto o priva di strumenti di accesso o di connessione internet è possibile realizzare delle postazioni dedicate e assistite presso tutti gli uffici pubblici o presso i privati disponibili per permettere di “avvicinare” lo sportello all’utenza abbattendo la distanza ed il tempo di esposizione duramte gli spostamenti



# I componenti tecnologici
## Il gestore di sportello

SW sviluppato appositamente con la funzione di tenere traccia delle code e di interagire con il sistema di video conferenza per la creazione della stanza e l’indirizzamento a questa dell'utente e dell'operatore.

## Il sistema di video conferenza

Si propone l’adozione di una soluzione open come Jitsi (sul quale è stato realizzato il Proof of Concept) in quanto presenta API di semplice utilizzo e non espone a costi di licenza e permette la fruizione sia da browser che da app.

# Infrastruttura

I due componenti possono essere dispiegati presso datacenter diversi, in particolare riguardo al sistema di video conferenza (che espone ad un maggior carico di rete) è possibile (e consigliabile in caso di grandi accessi) che questo sia ridondato (senza necessità di realizzare un cluster) su nodi posti anche su datacenter diversi.

A titolo di esempio, il proof of concept è stato eseguito su un pc (per la parte del gestore di sportello) e su 3 t2.micro Aws (1 processore, banda da low a moderate) dislocate a Parigi, Milano e Londra sostenendo 100 sessioni di sportelli simulati in parallelo per un costo totale di pochi centesimi di euro per ora di servizio.


# Possibili evolutive

- il riconoscimento dell'utente tramite strumenti forti che sostituiscono il "mi faccia vedere un documento" fatto allo sportello
- la possibilità di registrare la conferenza ( mostrando all' utente un messaggio che comunica che la conferenza è registrata)
- inserimento in una app
- la possibilità di sottoscrivere documenti (FEA)
- il supporto alla compilazione dei formulari da remoto (condividendo la finestra)
