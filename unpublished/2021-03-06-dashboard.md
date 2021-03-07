---
layout: post
title: Cosa ho imparato realizzando una dashboard per la simulazione dei casi di COVID-19 in tempo reale
---

![image-20210306155019827](C:\Users\berga\AppData\Roaming\Typora\typora-user-images\image-20210306155019827.png)

Durante il mese di marzo 2020 ho realizzato una piccola dashboard, un "cruscotto" per dirla all'italiana, in grado di comunicare la diffusione dell'epidemia in modo semplice, dal proprio smartphone.

# Introduzione

Ho deciso di mettere l'accento sul fatto che questi dati rappresentino **persone**: tramite un semplice calcolo, ho deciso di visualizzare quindi l'andamento in tempo reale del numero di casi confermati di coronavirus, con un contatore che incrementa ad un intervallo regolare.

Sono contento dell'impatto comunicativo che questo strumento può avere: esso secondo me è in grado di comunicare in un modo più immediato il significato dei dati, comunicando come, secondo per secondo, una nuova persona sia stata infettata.

 <video src="https://bouncybutton.github.io/content/gif/covid19tracker.mp4"></video>

*Versione interattiva su GitHub: [bouncybutton.github.com/covid19tracker](https://bouncybutton.github.io/covid19tracker/)*. *La versione attualmente online è dismessa e contiene dei dati storici e non aggiornati*.

# Analisi

Utile considerare un approccio mobile-first: questo mi ha permesso di concentrarmi sui dati essenziali, tralasciando il superfluo.

La previsione dei giorni futuri, benché realizzata in maniera elementare, è utile per comprendere se l'epidemia stia rallentando o accelerando, ossia la domanda maggiormente posta in questi mesi. Questa modalità tuttavia non dà la possibilità di confrontare agevolmente il tasso di crescita in date differenti.

Tra alcuni aspetti negativi troviamo come la differenza tra casi confermati e contagiati effettivi non sia stata sempre recepita: è di fatto un compito non banale (e tuttora oggetto di studi) l'effettivo impatto nella popolazione di questa pandemia.

Altri aspetti sono stati ignorati, come la percentuale di tamponi o nuove rappresentazioni grafiche. Questi punti nascondono ulteriori insidie, come la mancanza di un netto rapporto di casualità tra dati. 

# 3 punti fondamentali

blabla

## Data visualization influenza l'opinione pubblica

Come dimostrato addirittura 200 anni fa, una corretta informazione riesce a scuotere l'opinione pubblica e può essere causa di cambiamento positivo nella società. E' dunque responsabilità della comunità scientifica adottare modalità efficaci nella comunicazione dei dati al grande pubblico.

## **Le cose dovrebbero essere più semplici possibili, ma non "più semplici"**

Se comunichiamo in modo non chiaro, la nostra informazione rischia di venire snobbata in favore della disinformazione, portatrice di risposte chiare e "rassicuranti".

## **C'è un bisogno maggiore di una teoria dei metodi grafici di rappresentazione dati**

È mia opinione come la teoria non riesca a stare al passo con le nuove possibilità offerte dalla tecnologia. Già 15 anni fa veniva riportato come la datavis soffra di problemi quali l'usabilità e, ancora negli anni 80, come sia necessario trovare nuove procedure per la datavis qualora la tecnologia progredisca.