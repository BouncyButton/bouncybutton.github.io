---
layout: post
title: "Dati, grafici, pandemie e Florence Nightingale: come il passato può aiutare a comprendere il presente"
---

In questo nuovo post affronto due pietre miliari per la data visualization. Nella prima mostro come nell'Ottocento alcune innovazioni riuscirono a migliorare le condizioni di vita dei soldati dell'esercito britannico, comunicando efficacemente i pericoli delle pandemie in corso. Il secondo affronta come negli anni '80 furono definite le basi della teoria di questa disciplina.

# Cenni storici della data visualization

Possiamo vedere da questo grafico, realizzato da [The Milestones Project](https://www.datavis.ca/milestones/), come i primi esempi significativi di data visualization risalgano addirittura al 1500. 

![image-20210306105919282](https://bouncybutton.github.io/images/datavis/history-graph-datavis.png)

*Stima di densità della distribuzione di 248 milestones dal 1500 al 2000.* 

Tuttavia, è solo nel 19esimo secolo che questa scienza ebbe un rapido incremento nel suo utilizzo, dovuto a tre cause contemporanee: in primo luogo, per cause **scientifiche**: infatti in questo periodo venne formalizzata ed evoluta la teoria della probabilità, con il lavoro di Gauss e Laplace; in secondo luogo per ragioni **storiche**: lo sviluppo del potere nazionale fu essenziale per determinare una capacità maggiore nell'acquisizione di dati; infine, cause **economico/politiche**: molti economisti politici ebbero un interesse crescente nel trovare le cause del comportamento sociale, determinato da queste nuove opportunità.

# Un esempio di rilievo: Florence Nightingale (1820 – 1910)

Ho deciso di studiare la figura storica di Nightingale per il suo impatto non solo nella statistica e medicina, ma anche per il suo impatto sociale. 

![image-20210306110357646](https://bouncybutton.github.io/images/datavis/nightingale.png)

Nightingale dedicò la sua vita alla cura delle persone malate, divenendo una infermiera e applicando le scienze statistiche al fine di comunicare al pubblico lo stato dell'health care britannica militare.

Questa figura fu storicamente importante per cambiare la concezione del tempo che si aveva delle infermiere: infatti, durante l'intero Ottocento esse erano considerate poco più di domestiche. Questa situazione mutò negli anni a venire, come testimoniato da un censo inglese del 1901 dove vediamo come le infermiere [vennero riportate nella categoria "medicina" [1]](http://www.jstor.org/stable/24969329).

Nella sua vita Nightingale guidò un ospedale da campo militare, afflitto da epidemie prevenibili quali la colera e il tifo. Senza cambiamenti, il campo sarebbe stato decimato in un anno per le sole malattie presenti, come mostrato dal tasso di mortalità annuale che talvolta superò addirittura il 100%!

Grazie a tecniche di **visualizzazione dati** e alla statistica, Nightingale scosse l'opinione pubblica, arrivando fino al Parlamento e contribuendo così a riformare l'healthcare britannica militare nell'intera nazione.

![image-20210306110620838](https://bouncybutton.github.io/images/datavis/nightingale-chart.png)

*Questo grafico raffigura la crescita della pandemia mese per mese, indicando in blu come le malattie contagiose siano la causa di morte predominante rispetto a ferite in guerra, mostrate in rosso. Il grafico si sviluppa in senso orario, mostrando mese per mese una area proporzionale al numero dei morti.*

Questo fu uno dei primi **esempi di successo** per la data visualization e la sua storia è incredibilmente attuale: comunicare in modalità grafica un evento complesso può essere determinante per la corretta percezione dell'intera popolazione. Altrettanto importante è come questa raffigurazione studi una **pandemia in corso**: vediamo ad esempio come risalti subito la proporzione tra malattie e feriti, un paragone che sarebbe utilissimo in chiave moderna per interpretare l'impatto del COVID-19.

# Era contemporanea (1980 – oggi)

Ci spostiamo ora al secolo scorso, dove tra i paper presenti ho deciso di studiare [la pubblicazione [2]](www.jstor.org/stable/2288400) di William S. Cleveland, un *computer scientist*.

La sua pubblicazione dell'84 lamentò una **mancanza di una teoria** ben fondata e di una metodologia appropriata in grado di testare il livello di percezione umana di **rappresentazioni grafiche dei dati**. Questo paper propose una prima metodologia atta a misurare l'accuratezza della percezione e si interrogò su come sia possibile incrementare **quantità** e **qualità** dell'informazione percepita.

![image-20210306110620838](https://bouncybutton.github.io/images/datavis/cleveland-perception.png)

Cleveland identificò anche 10 elementi percettivi di base. Riuscì ad ordinarli per capacità comunicativa tramite uno studio quantitativo, paragonando la correttezza della percezione di un campione di persone. Vediamo ad esempio come le barre siano preferite ad inclinazioni o area.

Benché per la tecnologia 35 anni siano effettivamente un'eternità, l'importanza di questo paper è cruciale: ogni buon scienziato infatti mentre comunica dovrebbe tenere bene a considerazione *come* lo fa. Esiste inoltre un inevitabile **trade-off** tra qualità e quantità dell'informazione: una lista di numeri rappresentanti i contagi giornalieri di COVID-19 per provincia presenta molti dati ma poca informazione ai più; una cartina colorata o dei grafici comparativi danno una lettura profondamente differente e molto più intuitiva.

# Proposta... dal passato

Infine, propongo alcune visualizzazioni, nate dalle considerazioni fatte nei due precedenti paragrafi.

La prima visualizzazione venne realizzata da Nightingale: confrontò il tasso di mortalità annuale, differenziando tra popolazione civile (in nero) e militari (in rosso). Si nota immediatamente come, grazie a questa *baseline*, l'impatto delle condizioni igienico-sanitarie nei militari del tempo. Come sottolinea Cleveland, l'utilizzo di barre allineate è molto efficace rispetto a forme grafiche differenti.

![image-20210307155805622](https://bouncybutton.github.io/images/datavis/bar1.png)

*Nightingale, Morti per 1000 viventi, popolazione civile vs militari, per fascia di età tra 20 e 40 anni*

Possiamo realizzare una visualizzazione simile, considerando il tasso di mortalità per la prima metà dell'anno 2019 e la prima metà dell'anno 2020. A differenza di Nightingale, consideriamo le fasce d'età della popolazione più esposta, ossia dai 65 anni in su.

![image-20210307155811389](https://bouncybutton.github.io/images/datavis/bar2.png)

*Morti per 1000 viventi, 2019 vs 2020, per fascia di età tra 65 e 85+ anni (Italia)*

La situazione è ancora più drammatica considerando esclusivamente una delle regioni più colpite, la Lombardia, dove esiste una netta separazione tra i due diversi anni.

![image-20210307155822554](https://bouncybutton.github.io/images/datavis/bar3.png)

*Morti per 1000 viventi, 2019 vs 2020, per fascia di età tra 65 e 85+ anni (Lombardia)* 

>  Update: Il 5 marzo 2021 l'ISTAT ha diffuso [un nuovo studio](https://www.istat.it/it/archivio/254507) che realizza un confronto molto simile, evidenziando ancora l'impatto della pandemia nel nostro paese.

# Vuoi approfondire?

I precedenti articoli:

* [Come comunicare i dati di una pandemia: introduzione alla data visualization](https://bouncybutton.github.io/datavis-intro)

I prossimi articoli:

* [Dati, grafici, pandemie e Florence Nightingale: come il passato può aiutare a comprendere il presente](https://bouncybutton.github.io/storia-datavis/)

* Comunicazione efficace durante la pandemia: una analisi critica di alcune comunicazioni pubbliche avvenute tra marzo e agosto 2020
* [Creazione di una dashboard: qualche lezione imparata dalla realizzazione di una dashboard per il tracciamento del COVID-19 in Italia](https://bouncybutton.github.io/Dashboard/)

# Referenze

* [1] Cohen, I. (1984). Florence Nightingale. *Scientific American,* *250*(3), 128-137. [http://www.jstor.org/stable/24969329](http://www.jstor.org/stable/24969329)
* [2] Cleveland, W., & McGill, R. (1984). Graphical Perception: Theory, Experimentation, and Application to the Development of Graphical Methods. *Journal of the American Statistical Association*, *79*(387), 531-554. doi:10.2307/2288400. Retrieved August 30, 2020, from [www.jstor.org/stable/2288400](www.jstor.org/stable/2288400).
* [3] Dati demografici italiani, anni 2019-2020, elaborazione Istat. Retrieved August 31, 2020, from [https://www.istat.it/it/archivio/240401](https://www.istat.it/it/archivio/240401) and [https://www.tuttitalia.it/statistiche/popolazione-eta-sesso-stato-civile-2019/](https://www.tuttitalia.it/statistiche/popolazione-eta-sesso-stato-civile-2019/ ) 