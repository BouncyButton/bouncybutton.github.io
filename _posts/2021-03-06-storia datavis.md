---
layout: post
title: Dati, grafici, pandemie e Florence Nightingale. Come il passato può aiutare a comprendere il presente
---

![image-20210306110620838](https://bouncybutton.github.io/images/datavis/nightingale-chart.png)

In questo nuovo post affronto due eventi storici per la data visualization. Il primo mostra come nell'Ottocento alcune innovazioni riuscirono a migliorare le condizioni di vita dei soldati dell'esercito britannico, comunicando efficacemente i pericoli delle pandemie in corso. Il secondo, di carattere più tecnico, affronta come negli anni '80 si siano definite delle basi della teoria di questa disciplina.

# Cenni storici della data visualization

Possiamo vedere da questo grafico, realizzato da [The Milestones Project](https://www.datavis.ca/milestones/), come i primi esempi significativi  di data visualization risalgano addirittura al 1500. 

![image-20210306105919282](https://bouncybutton.github.io/images/datavis/history-graph-datavis.png)

*Stima di densità della distribuzione di 248 milestones dal 1500 al 2000.* 

Tuttavia, è solo nel 19esimo secolo che questa scienza ha avuto un rapido incremento nel suo utilizzo, dovuto a tre eventi contemporanei:

* Ragioni **scientifiche**: la formalizzazione e l'avanzamento della teoria della probabilità, con il lavoro di Gauss e Laplace;

* Ragioni **storiche**: lo sviluppo di nazioni con una capacità maggiore nell'acquisizione di dati;

* Ragioni **economico/politiche**: l'interesse crescente di molti economisti politici nel trovare le cause del comportamento sociale.

# Un esempio di rilievo: Florence Nightingale (1820 – 1910)

Ho deciso di studiare la figura storica di Nightingale per il suo impatto non solo nella statistica e medicina, ma anche per il suo impatto sociale. 

![image-20210306110357646](https://bouncybutton.github.io/images/datavis/nightingale.png)

Nightingale ha dedicato la sua vita alla cura delle persone malate, divenendo una infermiera e applicando le scienze statistiche al fine di comunicare al pubblico lo stato dell'health care britannica militare.

Questa figura è stata storicamente importante per cambiare la concezione del tempo che si aveva delle infermiere: infatti, durante l'intero Ottocento esse erano considerate poco più di domestiche. Questa situazione mutò negli anni a venire, come testimoniato da un censo inglese del 1901 dove vediamo come le infermiere [vengano riportate nella categoria "medicina" [1]](http://www.jstor.org/stable/24969329).

Nella sua vita Nightingale guida un ospedale da campo militare, afflitto da epidemie prevenibili quali la colera e il tifo. Senza cambiamenti, il campo sarebbe stato decimato in un anno per le sole malattie presenti, come mostrato dal tasso di mortalità annuale che talvolta superò addirittura il 100%!

Grazie a tecniche di **visualizzazione dati** e alla statistica, Nightingale scosse l'opinione pubblica, arrivando fino al Parlamento e contribuendo così a riformare l'healthcare britannica militare nell'intera nazione.

![image-20210306110620838](https://bouncybutton.github.io/images/datavis/nightingale-chart.png)

Questo grafico raffigura la crescita della pandemia mese per mese, indicando in blu come le malattie contagiose siano la causa di morte predominante rispetto a ferite in guerra (in rosso). Il grafico si sviluppa in senso orario, mostrando mese per mese una area proporzionale al numero dei morti.

Questo è stato uno dei primi **esempi di successo** per la data visualization e la sua storia è incredibilmente attuale: comunicare in modalità grafica un evento complesso può essere determinante per la corretta percezione dell'intera popolazione. Altrettanto importante è come coinvolga questa raffigurazione studi una **pandemia in corso**: vediamo ad esempio come risalti subito la proporzione tra malattie e feriti, un paragone che sarebbe utilissimo in chiave moderna per l'interpretazione dell'impatto del COVID-19.

# Era contemporanea (1980  – oggi)

Ci spostiamo ora all'era moderna, dove tra i paper presenti ho deciso di studiare [la pubblicazione [2]](www.jstor.org/stable/2288400) di William S. Cleveland, un *computer scientist*.

La sua pubblicazione dell'84 lamenta una **mancanza di una teoria** ben fondata e di una metodologia appropriata in grado di testare il livello di percezione umana di **rappresentazioni grafiche dei dati**. Questo paper propone una prima metodologia atta a misurare l'accuratezza della percezione e si interroga come sia possibile incrementare **quantità **e **qualità** dell'informazione percepita.

![image-20210306110620838](https://bouncybutton.github.io/images/datavis/cleveland-perception.png)

Vediamo come Cleveland identifica anche 10 elementi percettivi di base. Riesce ad ordinarli per capacità comunicativa tramite uno studio quantitativo, paragonando la correttezza della percezione di un campione di persone. Vediamo ad esempio come le barre siano preferite ad inclinazioni o area.

Benché per la tecnologia 35 anni siano effettivamente un'eternità, l'importanza di questo paper è cruciale: ogni buon scienziato infatti mentre comunica dovrebbe tenere bene a considerazione *come* lo fa. Esiste un inevitabile **trade-off** tra qualità e quantità dell'informazione: una lista di numeri rappresentanti i contagi giornalieri di COVID-19 per provincia presenta molti dati ma poca informazione ai più; una cartina colorata o dei grafici comparativi danno una lettura profondamente differente e molto più intuitiva.

# Proposta... dal passato

Infine, propongo alcune visualizzazioni, nate dalle considerazioni fatte nei due precedenti paragrafi.

La prima visualizzazione è stata realizzata da Nightingale: confronta il tasso di mortalità annuale, differenziando tra popolazione civile (in nero) e militari (in rosso). Si nota immediatamente come, grazie a questa *baseline*, l'impatto delle condizioni igienico-sanitarie nei militari del tempo. 

![image-20210307155805622](https://bouncybutton.github.io/images/datavis/bar1.png)

*Nightingale, Morti per 1000 viventi, popolazione civile vs militari, per fascia di età tra 20 e 40 anni*

Possiamo realizzare una visualizzazione simile, considerando il tasso di mortalità per la prima metà dell'anno 2019 e la prima metà dell'anno 2020. Consideriamo le fasce d'età della popolazione più esposta, ossia dai 65 anni in su.

![image-20210307155811389](https://bouncybutton.github.io/images/datavis/bar2.png)

*Morti per 1000 viventi, 2019 vs 2020, per fascia di età tra 65 e 85+ anni (Italia)*

La situazione è ancora più drammatica considerando esclusivamente una delle regioni più colpite, la Lombardia, dove esiste una netta separazione tra i due diversi anni.

![image-20210307155822554](https://bouncybutton.github.io/images/datavis/bar3.png)

*Morti per 1000 viventi, 2019 vs 2020, per fascia di età tra 65 e 85+ anni (Lombardia)* 

>  Update: Il 5 marzo 2021 l'ISTAT ha diffuso [un nuovo studio](https://www.istat.it/it/archivio/254507) che realizza un confronto molto simile, evidenziando ancora l'impatto della pandemia nel nostro paese.

# Referenze

* [1] Cohen, I. (1984). Florence Nightingale. *Scientific American,* *250*(3), 128-137. http://www.jstor.org/stable/24969329
* [2] Cleveland, W., & McGill, R. (1984). Graphical Perception: Theory, Experimentation, and Application to the Development of Graphical Methods. *Journal of the American Statistical Association*, *79*(387), 531-554. doi:10.2307/2288400. Retrieved August 30, 2020, from www.jstor.org/stable/2288400.
* [3] Dati demografici italiani, anni 2019-2020, elaborazione Istat. Retrieved August 31, 2020, from https://www.istat.it/it/archivio/240401 and https://www.tuttitalia.it/statistiche/popolazione-eta-sesso-stato-civile-2019/ 