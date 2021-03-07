---
layout: post
title: "Come comunicare i dati di una pandemia: introduzione alla data visualization"
---

I recenti avvenimenti attorno al COVID-19 mi hanno portato a riflettere su come l'informatica possa avere un impatto positivo nella società, in particolare contribuendo a **comunicare efficacemente** al pubblico i **pericoli di una pandemia** in corso.

# Introduzione

> Data visualization e informatica possono potenziare la comunicazione e renderla efficace, oppure possono distorcerla completamente.

Da mesi medito di completare e diffondere una serie di articoli basati su una ricerca personale svolta presso l'Università di Padova. Questa ricerca tocca un tema a me molto caro: la **comunicazione** e la **responsabilità** che programmatori, *data scientist* e ricercatori possiedono quando utilizzano i propri strumenti per parlare con il grande pubblico. Centrale per tutte queste figure è la raccolta, l'elaborazione e la comunicazione dei **dati**: cardine della ricerca sperimentale, questi spesso sono gli unici mezzi che abbiamo per validare o confutare le nostre teorie scientifiche.

Il tema che voglio introdurre con questa serie di articoli vuole dare una panoramica accessibile al più vasto pubblico, per far capire le decisioni che i professionisti di vari settori dovrebbero tenere in considerazione quando utilizzano dei dati per comunicare. In particolare tenterò di coinvolgere l'attuale tematica pandemica: in questa discussione la figura di un "informatico" come la mia può essere utile non tanto nel discutere complessi argomenti di medicina, quanto nel fare chiarezza di come l'enorme mole di dati a cui siamo esposti ogni giorno venga trattata e comunicata.

Parleremo ora di una disciplina precisa, spesso fraintesa o poco considerata: la data visualization, ossia, la **rappresentazione grafica di dati**.

# Data visualization

La data visualization è una disciplina che coinvolge attivamente diverse aree scientifiche, dalla *data science* in primis a diverse importanti attività come il trattamento dei [big data](https://en.wikipedia.org/wiki/Big_data), l'High-performance computing, o applicazioni **scientifiche**, come in **simulazioni fisiche** o **biologiche**. Questa disciplina ha una sovrapposizione rilevante con la **psicologia** e viene attivamente impiegata nel mondo **economico** per ottenere preziose intuizioni.

![image-20210226225925203](https://bouncybutton.github.io/images/datavis/bubble-datavis.png)

# Quale definizione?

Ma cos'è la data visualization? Nel web troviamo **più definizioni**; partiamo con le parti in comune.

> La Data visualization è un modo per rappresentare *informazione in modo grafico*, evidenziando **pattern** e **andamenti** nei dati e aiutando il lettore a raggiungere **veloci intuizioni**. [[Gartner](https://www.gartner.com/en/marketing/glossary/data-visualization)]

> La Data visualization è la *rappresentazione grafica di dati*. Include la produzione di immagini che comunicano **relazioni** tra i dati rappresentati ai lettori delle immagini. [[Wikipedia](https://en.wikipedia.org/wiki/Data_visualization
> )]

Possiamo riassumere che la data visualization si occupa di evidenziare pattern, trend e relazioni negli oggetti che elabora, al fine di dare al lettore una veloce comprensione.

Ma, se uno studente si limitasse a studiare le definizioni di Gartner e Wikipedia, i due primi risultati su Google, rimarrebbe nella **errata concezione** che **informazione** e **dato** siano la stessa cosa. Penso sia dunque istruttivo avventurarsi in modo più profondo in questi concetti: cosa intendiamo per *dato* e *informazione*? Quando dobbiamo preferire uno o l'altro termine?

# Dato o informazione?

La differenza tra dato, informazione e ultima istanza conoscenza, è oggetto di discussione, anche filosofica.

Secondo [Ackoff](https://en.wikipedia.org/wiki/Russell_L._Ackoff), un *management scientist*, esiste una [gerarchia [1]](http://faculty.ung.edu/kmelton/Documents/DataWisdom.pdf ) che lega dati, informazioni, conoscenza e *saggezza*.

![image-20210226225925203](https://bouncybutton.github.io/images/datavis/piramid1.png)

Secondo la sua visione, i **dati** sono dei simboli, che rappresentano **proprietà di un oggetto**. Per io che programmo un computer, i dati possono essere rappresentati da bit e bytes e li studio per le loro proprietà, se vogliamo "di forma": una foto è descritta come una serie molto lunga, ma ben precisa, di 1 e di 0. Il mio compito può essere, ad esempio, studiare come memorizzarli, elaborarli, condividerli in tempo reale con un mio amico, e via dicendo.

L'informazione invece rappresenta questi dati ad un livello più astratto, compatto e utile. La parola chiave è **funzionale**: l'informazione risponde a delle domande "cosa? quando? quanto?" e ha **significato** per chi la legge. Pensiamo a questo esempio.

![image-20210226225925203](https://bouncybutton.github.io/images/datavis/piramid3.png)

* **Dato**: un dato è anonimo: guardando al numero 1944, potremmo immaginare che si tratti di una data, di un orario o di un conto salato dal meccanico. Con i dati è possibile fare moltissime operazioni: posso sommarli, calcolare la media, creare un modello predittivo e tanto altro.
* **Informazione**: la possiamo rappresentare in più modi: tramite una stringa di testo, una barra di dimensioni adeguate, un colore in una cartina. Non è importante la rappresentazione per definire se stiamo definendo informazione, ma è più importante è poter dare una risposta **comprensibile** alle nostre domande. In questo senso il **contesto** è essenziale: data, luogo e significato dei dati contenuti all'interno dell'informazione devono essere resi espliciti. È importante dunque indicare sia l'oggetto che stiamo descrivendo, sia l'ambiente in cui si trova.
* **Conoscenza**: questa richiede un passo di comprensione ulteriore: oltre ad una comprensione quantitativa, è necessario raggiungere una comprensione qualitativa. Ad esempio, potremmo interrogarci sull'andamento dei casi di COVID-19. Per rispondere a questa domanda, dobbiamo unire differenti informazioni (di data diversa, di provincie diverse, etc.) e metterle in relazione tra di loro.

Questa visione è una delle molte esistenti in letteratura: questa tematica è ancora oggetto di dibattito e non c'è una opinione condivisa; ciò influenza la definizione di data visualization.

# Esistono molti tipi di visualizzazioni

Esistono ulteriori materie, come la *scientific visualization* o la *information visualization*, le quali mettono l'accento su **aspetti differenti** dell'elaborazione di dati e informazioni. Recentemente, il termine data visualization sta raggruppando questi campi di studio.

> The phrase ‘Data Visualization’ is gaining acceptance to include both the scientific and information visualization fields. ([H. Post](https://web.archive.org/web/20091007134531/http://visualisation.tudelft.nl/publications/post2003b.pdf
> ))

Possiamo vedere con un esempio dunque cosa intendiamo con data visualization e quali di questi possano essere considerati information visualization e scientific visualization.

![image-20210226225925203](https://bouncybutton.github.io/images/datavis/more-datavis.png)

## Scientific visualization

> Scientific visualization is concerned with exploring data and information in such a way as to gain understanding and insight.  ([R. A. Earnshaw](https://www.springer.com/gp/book/9783642634703))

La scientific visualization mira a realizzare visualizzazioni a scopo scientifico e indagano prevalentemente fenomeni fisici in modo da dare una visualizzazione concreta di fenomeni complessi. Ad esempio, nel 2019 ha destato scalpore la simulazione di un buco nero, [realizzata dalla Nasa]([NASA Visualization Shows a Black Hole's Warped World | NASA](https://www.nasa.gov/feature/goddard/2019/nasa-visualization-shows-a-black-hole-s-warped-world/)). La realizzazione di queste visualizzazioni è basata su un ingente quantità di dati, elaborata e sintetizzata in una immagine.

## Information visualization

> Information visualization [is defined] as visual representations of the semantics, or meaning, of information. In contrast to scientific visualization, information visualization typically deals with nonnumeric, nonspatial, and high-dimensional data. ([C. Chen)](https://ieeexplore.ieee.org/document/1463074)

L'information visualization invece si occupa di studiare informazione più astratta alla quale proviamo a dare una interpretazione, se vogliamo, con "un paio di occhiali differenti" (citando le lezioni di un importante [professore](https://en.wikipedia.org/wiki/Massimo_Marchiori) che ho avuto la fortuna di seguire).

L'informatica per questo è centrale nella costruzione di questi occhiali: ci dà i mezzi per processare e rappresentare in modo grafico grandi quantità di dati, in modo da sintetizzarne informazioni utili.

Un ottimo esempio di quest'ultima materia si può trovare al sito [internet-map.net](https://internet-map.net/), dove i maggiori siti web sono rappresentati in una mappa, dove vengono rappresentate le relazioni tra diversi siti.

# Vuoi approfondire?

I prossimi articoli:

* [Dati, grafici, pandemie e Florence Nightingale: come il passato può aiutare a comprendere il presente](https://bouncybutton.github.io/storia-datavis/)

* Comunicazione efficace durante la pandemia: una analisi critica di alcune comunicazioni pubbliche avvenute tra marzo e agosto 2020
* [Creazione di una dashboard: qualche lezione imparata dalla realizzazione di una dashboard per il tracciamento del COVID-19 in Italia](https://bouncybutton.github.io/dashboard/)

# Referenze

* [1] Ackoff, R. (1989). From Data to Wisdom. Retrieved August 30, 2020, from http://faculty.ung.edu/kmelton/Documents/DataWisdom.pdf 
* [2] Chen, et al. (2009). Data, Information, and Knowledge in Visualization. Computer Graphics and Applications, IEEE. 29. 12 - 19. 10.1109/MCG.2009.6. Retrieved August 30, 2020, from https://dl.acm.org/doi/10.5555/1669271.1669274




