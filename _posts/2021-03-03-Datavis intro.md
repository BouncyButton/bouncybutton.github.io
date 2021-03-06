---
layout: post
title: Come comunicare i dati di una pandemia: introduzione alla data visualization
---

![image-20210226235139134](C:\Users\berga\AppData\Roaming\Typora\typora-user-images\image-20210226235139134.png)

I recenti avvenimenti attorno al COVID-19 mi hanno portato a riflettere su come l'informatica possa avere un impatto positivo nella società, in particolare contribuendo a comunicare efficacemente al pubblico i pericoli di una pandemia in corso.

# Introduzione

Da mesi medito di completare e diffondere una serie di articoli basati su una ricerca personale svolta presso l'Università di Padova.

Questa ricerca tocca un tema a me molto caro: la **comunicazione** e la **responsabilità** che programmatori, *data scientist* e ricercatori posseggono quando utilizzano i propri strumenti per parlare con il grande pubblico.

Centrale per tutte queste figure è la raccolta, l'elaborazione e la comunicazione dei **dati**: ... 

> Data visualization e informatica possono potenziare la comunicazione e renderla efficace, oppure possono distorcerla completamente.

Il tema che voglio introdurre con questa serie di articoli vuole dare una panoramica accessibile a chiunque, per far capire le decisioni che i professionisti di vari settori devono prendere nel realizzare le proprie...

Questo primo articolo fa un passo indietro: non parleremo di COVID-19, ma parleremo di una disciplina precisa, spesso fraintesa etc.

# Data visualization

La data visualization è una disciplina che coinvolge attivamente diverse aree scientifiche, dalla *data science* in primis a diverse importanti attività come il trattamento dei [big data](https://en.wikipedia.org/wiki/Big_data), l'High-performance computing, o applicazioni **scientifiche**, come in **simulazioni fisiche** o **biologiche**. Questa disciplina ha una sovrapposizione rilevante con la **psicologia** e viene attivamente impiegata nel mondo **economico** al fine di ottenere preziosi insights.

![image-20210226225925203](C:\Users\berga\AppData\Roaming\Typora\typora-user-images\image-20210226225925203.png)



# Quale definizione?

Ma cos'è la data visualization? La comunità scientifica possiede **più definizioni**; partiamo con le parti in comune.

> Data visualization is a way to *represent information graphically*, highlighting **patterns** and **trends** in data and helping the reader to achieve **quick insights** [[Gartner](https://www.gartner.com/en/marketing/glossary/data-visualization)]

> Data visualization is the *graphic representation of data*. It involves producing images that communicate **relationships** among the represented data to viewers of the images. [[Wikipedia](https://en.wikipedia.org/wiki/Data_visualization
> )]

La data visualization si occupa di evidenziare pattern, trend e relazioni negli oggetti che elabora, al fine di dare al lettore una veloce comprensione.

Ma, se uno studente si limitasse a studiare le definizioni di Gartner e Wikipedia, i due primi risultati su Google, rimarrebbe nella **errata concezione** che **informazione** e **dato** siano la stessa cosa.

Questo, e alcuni punti successivi nel mio approfondimento mi hanno portato a chiedermi dunque: ma cosa intendiamo per *dato* e *informazione*? È giusto usarli in modo interscambiabile?

# Dato o informazione?

La differenza tra dato, informazione e ultima istanza conoscenza, è oggetto di discussione, anche filosofica.

Secondo [Ackoff](https://en.wikipedia.org/wiki/Russell_L._Ackoff), un *management scientist*, esiste una [gerarchia](http://faculty.ung.edu/kmelton/Documents/DataWisdom.pdf ) che lega dati, informazioni, conoscenza e *saggezza*.

![image-20210226230828226](C:\Users\berga\AppData\Roaming\Typora\typora-user-images\image-20210226230828226.png)

Secondo la sua visione, i **dati** sono dei simboli, che rappresentano **proprietà di un oggetto**. Per io che programmo un computer, i dati possono essere rappresentati da bit e bytes e li studio per le loro proprietà, se vogliamo "di forma": una foto è descritta come una serie molto lunga, ma ben precisa, di 1 e di 0. Il mio compito può essere, ad esempio, studiare come memorizzarli, elaborarli, condividerli in tempo reale con un mio amico, e via dicendo.

L'informazione invece rappresenta questi dati ad un livello più astratto, compatto e utile. La parola chiave è **funzionale**: l'informazione risponde a delle domande "cosa? quando? quanto?" e ha **significato** per chi la legge. Pensiamo a questo esempio.

![image-20210226232953835](C:\Users\berga\AppData\Roaming\Typora\typora-user-images\image-20210226232953835.png)

Possiamo leggere 

* **Dato**: all'interno di una immagine troviamo il pixel di colore `#ff2133`. rappresentato da 3 bytes. posso applicare operazioni (contrasto, luminosità, etc.)
* **Informazione**:  di che colore è questa immagine? 'rosso'. rappresentato da una stringa, ma la rappresentazione non è importante. Più importante è poter dare una risposta **comprensibile**.
* **Conoscenza**: come posso usare i colori per realizzare una pubblicità attraente? unisce molte informazioni (successo pubblicità, colori predominanti, etc.) e dà in output delle istruzioni.

Questa visione è una delle molte esistenti in letteratura: questa tematica è ancora oggetto di dibattito e non c'è una opinione condivisa; ciò influenza la definizione di data visualization.



# Scientific visualization e Information visualization

> Scientific visualization is concerned with exploring data and information in such a way as to gain understanding and insight.  ([R. A. Earnshaw](https://www.springer.com/gp/book/9783642634703))

> Information visualization [is defined] as visual representations of the semantics, or meaning, of information. In contrast to scientific visualization, information visualization typically deals with nonnumeric, nonspatial, and high-dimensional data. ([C. Chen)](https://ieeexplore.ieee.org/document/1463074)

> The phrase ‘Data Visualization’ is gaining acceptance to include both the scientific and information visualization fields. ([H. Post](https://web.archive.org/web/20091007134531/http://visualisation.tudelft.nl/publications/post2003b.pdf
> ))

Esistono ulteriori materie, come la scientific vis o la infovis, le quali mettono l'accento su aspetti differenti dell'elaborazione di dati e informazioni.

Recentemente tuttavia il termine data visualization sta raggruppando questi campi di studio.

Possiamo vedere con un esempio dunque cosa intendiamo con data visualization e quali di questi possano essere considerati infovis e scivis.

![image-20210227000055185](C:\Users\berga\AppData\Roaming\Typora\typora-user-images\image-20210227000055185.png)



# Vuoi approfondire?

I prossimi articoli:

* Dati, grafici, pandemie e Florence Nightingale: come il passato può aiutare a comprendere il presente

* Comunicazione efficace durante la pandemia: una analisi critica di alcune comunicazioni pubbliche avvenute tra marzo e agosto 2020
* Nuove rappresentazioni grafiche dell’informazione: usare la tecnologia per dare nuove intuizioni
* Creazione di una dashboard: qualche lezione imparata dalla realizzazione di una dashboard per il tracciamento del COVID-19 in Italia






