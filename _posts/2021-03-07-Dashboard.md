---
layout: post
title: Cosa ho imparato realizzando una dashboard per la simulazione dei casi di COVID-19 in tempo reale
---

![image-20210306155019827](https://bouncybutton.github.io/images/datavis/dashboard-preview.png)

Durante il mese di marzo 2020 ho realizzato una piccola dashboard, un "cruscotto" per dirla all'italiana, in grado di comunicare lo stato della diffusione dell'epidemia in modo semplice, dal proprio smartphone.

# Introduzione

Ho deciso di mettere l'accento sul fatto che questi dati rappresentino **persone**: tramite un semplice calcolo, ho deciso di visualizzare quindi l'andamento in tempo reale del numero di casi confermati di coronavirus, con un contatore che incrementa ad un intervallo regolare.

Sono contento dell'impatto comunicativo che questo strumento può avere: è in grado di comunicare in un modo più immediato il significato dei dati, comunicando come, secondo per secondo, una nuova persona sia stata infettata.

 <video src="https://bouncybutton.github.io/content/gif/covid19tracker.mp4" autoplay muted loop></video>

*Versione interattiva su GitHub:* [bouncybutton.github.com/covid19tracker](https://bouncybutton.github.io/covid19tracker/). *La versione attualmente online è dismessa e contiene dei dati storici e non aggiornati*.

# Analisi

In primo luogo ho trovato utile considerare un approccio *mobile-first*: questo mi ha permesso di concentrarmi sui **dati essenziali**, tralasciando il superfluo. Non a caso la semplificazione delle interfacce è stata una delle cause di punta di una rapida diffusione degli smartphone, sin dalla prima introduzione dell'iPhone, nel 2008: un'interfaccia leggera e intuitiva riduce il sovraccarico cognitivo degli utenti e permette loro di fruire più comodamente dei propri dispositivi tecnologici. 

La previsione dell'andamento dei casi nei giorni futuri, benché realizzata in maniera elementare, è utile per comprendere se l'epidemia stia **rallentando** o **accelerando**, che è la domanda che ci siamo maggiormente posti in questi mesi. Questa modalità tuttavia non dà la possibilità di confrontare agevolmente il tasso di crescita in date differenti.

Da segnalare come la differenza tra **casi confermati** e **contagiati effettivi** non sia stata sempre recepita, malgrado l'avviso che comunque i dati mostrati rappresentano una stima. 

Altri aspetti sono stati ignorati, come la **percentuale di tamponi positivi** o **nuove rappresentazioni** grafiche. Questi punti nascondono ulteriori insidie, sia tecniche che comunicative: ad esempio, un basso tasso di tamponi positivi è indice di ridotta crescita della pandemia o di una insufficiente quantità di tamponi effettuati?

# Tre punti fondamentali

Senza soffermarmi su ulteriori analisi tecniche (a livello tecnologico c'è poco di interessante) vorrei invece concentrarmi su alcune lezioni che ho imparato a seguito di questo studio.

## Data visualization influenza l'opinione pubblica

Come dimostrato addirittura [200 anni fa](https://bouncybutton.github.io/storia-datavis/), una corretta informazione riesce a scuotere l'opinione pubblica e può essere causa di cambiamento positivo nella società. È dunque responsabilità della comunità scientifica adottare modalità efficaci nella comunicazione dei dati al grande pubblico.

## L'accesso ai dati pubblici deve essere garantito

Viviamo in un periodo storico mai visto prima per la quantità di dati a cui siamo esposti e questo vale altrettanto per la quantità di dis-informazione, ossia informazione non veritiera, non contestualizzata e distorta per negligenza o per malizia.

L'accesso libero ai dati di interesse nazionale deve essere garantito: da una parte per poter essere studiato ed esposto in modo da creare nuova informazione, accessibile e comprensibile da chiunque, dall'altra per contrastare la cattiva informazione, basandosi su dati fattuali. 

Mancare questo obiettivo rischia di creare una divisione tra pochi cittadini che *conoscono* e che forniscono un'informazione distorta dai propri interessi e gli altri cittadini che *non possono conoscere*, come una sorta di analfabetismo del nuovo secolo.

In quest'ottica iniziative che promuovono l'adozione di [Open Data](https://www.dati.gov.it/) sono da incentivare e tenere sempre più in considerazione.

## **C'è un bisogno crescente di una teoria dei metodi grafici di rappresentazione dati**

È mia opinione come la teoria **non riesca a stare al passo** con le nuove possibilità offerte dalla tecnologia. Già 15 anni fa veniva riportato come la data visualization soffra di problemi quali [l'usabilità [1]](https://ieeexplore.ieee.org/document/1463074
) e, ancora [negli anni 80 [2]](https://www.jstor.org/stable/2346220), come sia necessario trovare nuove procedure qualora la tecnologia progredisca.

Con quali nuove modalità possiamo esplorare e comprendere meglio i dati? Un fantastico video di G. Sanderson ("3Blue1Brown"), intitolato "Simulating an epidemic", ci dà un'ottima visione di come possiamo usare la tecnologia per dare nuove, preziose, intuizioni.

<iframe width="560" height="315" src="https://www.youtube.com/embed/gxAaO2rsdIs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



# Vuoi approfondire?

I precedenti articoli:

* [Come comunicare i dati di una pandemia: introduzione alla data visualization](https://bouncybutton.github.io/datavis-intro)

* [Dati, grafici, pandemie e Florence Nightingale: come il passato può aiutare a comprendere il presente](https://bouncybutton.github.io/storia-datavis/)

* Comunicazione efficace durante la pandemia: una analisi critica di alcune comunicazioni pubbliche avvenute tra marzo e agosto 2020

# Referenze

* [1] C. Chen, (2005) "Top 10 unsolved information visualization problems," in *IEEE Computer Graphics and Applications*, vol. 25, no. 4, pp. 12-16, July-Aug. 2005, doi: 10.1109/MCG.2005.91. Retrieved August 30, 2020, from https://ieeexplore.ieee.org/document/1463074
* [2] Cox, D. (1978). Some Remarks on the Role in Statistics of Graphical Methods. *Journal of the Royal Statistical Society. Series C (Applied Statistics),* 27(1), 4-9. doi:10.2307/2346220. Retrieved August 31, 2020, from https://www.jstor.org/stable/2346220