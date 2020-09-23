---
title: Store datasæt, datapunktgrænser og datastrategier
description: Datagrænser for visualiseringer og datareduktionsstrategier
author: mihart
ms.reviewer: justyna
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/10/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 5efe83cfa43c6fcb156501774bbaeae79381ab85
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90857720"
---
# <a name="apply-data-point-limits-and-strategies-by-visual-type"></a>Anvend datapunktgrænser og strategier efter visualiseringstype

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

Når du gengiver en visualisering i Power BI, skal visualiseringen være hurtig og præcis. Det kræver, at der er konfigureret underliggende algoritmer for hver visualiseringstype. Visualiseringer i Power BI skal være fleksible nok til at håndtere forskellige størrelser af datasæt. Nogle datasæt har kun en håndfuld datapunkter, mens andre datasæt har petabyte af datapunkter. I denne artikel forklares de strategier, der bruges af Power BI til at gengive visualiseringer.

## <a name="data-reduction-strategies"></a>Datareduktionsstrategier
Hver enkelt visualisering har en eller flere *datareduktionsstrategier* for at kunne håndtere de potentielt store datamængder, der analyseres. Selv en enkel tabel har en strategi for at undgå indlæsning af hele datasæt til klienten.  Den anvendte reduktiosstrategi varierer afhængigt af visualiseringstypen. Hver enkelt visualisering vælger mellem de understøttede *datareduktionsstrategier* som en del af genereringen af den dataanmodning, der er sendt til serveren. 

Hver enkelt visualisering styrer parametrene for disse strategier for at påvirke den samlede datamængde.   

## <a name="strategies"></a>Strategier
For hver strateg er der er standarder, der er baseret på den form og type af data, der skal visualiseres. Men standardindstillingerne kan tilsidesættes i formateringsruden i Power BI for at give den rette brugeroplevelse. 

* **Datavinduer** (segmentering): Tillad, at brugerne må rulle gennem dataene i en visualisering ved gradvist at indlæse fragmenter af det samlede datasæt.
* **Øverste N**: Vis kun de første N-elementer
* **Enkelt eksempel**: Vis det første og sidste element samt N-elementer jævnt fordelt ind imellem.
* **NedersteN**: Vis kun de sidste N-elementer.  Nyttige til overvågning af ofte opdaterede data.
* **Stikprøvetagning med høj tæthed** – en forbedret stikprøvetagningsalgoritme, der i højere grad respekterer udenforliggende værdier og/eller formen af en kurve.
    * **Stikprøvetagning af grupperede linjer** – eksempeldatapunkter, der er baseret på udenforliggende værdier i grupper på tværs af en akse
    * **Stikprøvetagning af overlappende punkter** – eksempeldatapunkter, der er baseret på overlappende værdier for at bevare udenforliggende værdier

## <a name="statistics"></a>Statistik
Visse modeller kan levere statistikker om antallet af værdier for bestemte kolonner. Når disse oplysninger er til stede, kan vi udnytte disse oplysninger til at give bedre belastningsjustering på tværs af flere hierarkier, hvis en visualisering ikke udtrykkeligt tilsidesætter antallet af værdier for en strategi.

Du kan finde flere oplysninger under [Nyheder i Analysis Services](/sql/analysis-services/what-s-new-in-analysis-services)

## <a name="dynamic-limits"></a>Dynamiske grænser
Ud over ovenfor nævnte strategier bruger visualiseringer med to hierarkier af grupperingskolonner (akse og forklaring eller kategori og serie) yderligere en strategi kaldet *dynamiske grænser*.  Dynamiske grænser er designet til bedre at balancere datapunkter. 

Dynamiske grænser giver en bedre markering af punkter til sparsomme data, end statiske grænser ville gøre. En visualisering kunne f.eks. konfigureres til at vælge 100 kategorier og 10 serier med i alt 1000 punkter. Men de faktiske data har 50 kategorier og 20-serier.  Ved kørsel af forespørgslen vælger en dynamisk grænse alle 20 serier for at udfylde de 1000 punkter, der er anmodet om.

Dynamiske grænser anvendes automatisk, når serveren er funktionsdygtig som beskrevet nedenfor:

* I Power BI Desktop med SSAS-version 2016 eller nyere i det lokale miljø [ved at udnytte serverens SuperDax-funktioner](/archive/blogs/analysisservices/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3)

* I Desktop og Power BI-tjenesten, når der anvendes en importeret model, direkte forespørgsel, direkte forbindelse til tjenesten eller direkte forbindelse til AS PaaS. 

* I Power BI-tjenesten kan vi ikke bruge dynamiske grænser, når der oprettes forbindelse til SSAS i det lokale miljø via en gateway i det lokale miljø. Gatewayen i det lokale miljø understøtter ikke fuldt ud strategien om dynamiske grænser, der returnerer en anden struktur af resultatsæt fra SSAS i det lokale miljø.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Strategier og datapunktgrænser efter visualiseringstype

### <a name="area-chart"></a>Områdediagram
Se [Sådan fungerer stikprøvetagning af linjer](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Søjlediagrammer/liggende søjlediagrammer
- I kategoritilstand
    - Kategorier: Virtualisering ved hjælp af vindue på 500 rækker ad gangen
    - Serie: Øverste 60
    - I skalartilstand (dynamiske grænser kan anvendes)
        - Maksimumpunkter: 10.000
        - Kategorier: Eksempel på 500 værdier
        - Serie: Øverste 20-værdier

### <a name="card-multirow"></a>Kort (flere rækker) 
- Værdier: Virtualisering ved hjælp af vindue på 200 rækker ad gangen

### <a name="combo-chart"></a>Kombinationsdiagram
 Bruger de samme strategier som søjlediagram. Bemærk, at linjen i **kombinationsdiagrammet** ikke bruger samme algoritme med høj tæthed som **kurvediagrammet**.

### <a name="power-bi-visuals"></a>Power BI-visualiseringer
Kan få op til 30.000, men det er op til forfatterne af visualiseringen at angive, hvilke strategier der skal bruges. Standardgrænsen er 1.000, men forfatteren af visualiseringen kan ændre dette, op til maksimalt 30.000.

### <a name="doughnut"></a>Krans
- Maksimumpunkter: 3,500
- Gruppe: Øverste 500
- Detaljer: Øverste 20

### <a name="filled-map-choropleth"></a>Udfyldt fladekort 
Det udfyldte kort kan bruge statistikker eller dynamisk grænser. Power BI forsøger at bruge reduktion i følgende rækkefølge: dynamiske grænser, statistik og endelig konfiguration. 
- Maksimumpunkter: 10.000
- Kategorier: Øverste 500
- Serie (når både X og Y er til stede): Øverste 20

### <a name="funnel"></a>Tragt
- Maksimumpunkter: 3,500
- Kategorier: Øverste 3.500

### <a name="kpi"></a>KPI
- Tendensakse
- Nederste 3.500

### <a name="line-chart"></a>Kurvediagram
Se [Sådan fungerer stikprøvetagning af linjer](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Kurvediagram, høj tæthed
Se [Stikprøvetagning med høj tæthed](../create-reports/desktop-high-density-sampling.md)

### <a name="map"></a>Kort 
- Maksimumpunkter: 3,500

Afhængigt af konfigurationen kan et kort have:
- Placering: Øverste 3.500
- Placering, størrelse: Øverste 3.500
- Samlinger af placering, breddegrad og længdegrad (+/-størrelse): Øverste 3.500
- Længdegrad, breddegrad: se [punktdiagram med høj tæthed](../create-reports/desktop-high-density-scatter-charts.md)
- Breddegrad, længdegrad, størrelse: Øverste 3.500
- Forklaring, længdegrad, breddegrad: se [punktdiagram med høj tæthed](../create-reports/desktop-high-density-scatter-charts.md)
- Forklaring, breddegrad, længdegrad, størrelse: Øverste 233-forklaringer, øverste 15-breddegrad og -længdegrad (kan bruge statistikker eller dynamiske grænser)
- Placering, forklaring, breddegrad og længdegrad som samlinger (+/-størrelse): Øverste 233-placeringer, øverste 15-forklaringer (kan bruge statistikker eller dynamiske grænser)

### <a name="matrix"></a>Matrix
- Rækker: Virtualisering ved hjælp af vindue på 500 rækker ad gangen
- Kolonner: Øverste 100-grupperingskolonner 
- Værdier: Flere værdier tæller ikke i forhold til datareduktionen

### <a name="powerapps-visual"></a>Visualisering i PowerApps
Kan få op til 30.000, men det er op til forfatterne af visualiseringen at angive, hvilke strategier der skal bruges. Standardgrænsen er 1.000, men forfatteren af visualiseringen kan ændre dette, op til maksimalt 30.000.

### <a name="radial-gauge"></a>Radial måler
Ingen reduktionsstrategi

### <a name="slicer"></a>Udsnit
- Værdier: Virtualisering ved hjælp af vindue på 200 rækker ad gangen

### <a name="scatter-chart-high-density"></a>Punktdiagram (høj tæthed)
Se [punktdiagram med høj tæthed](./desktop-high-density-scatter-charts.md)

### <a name="pie"></a>Cirkel
- Maksimumpunkter: 3,500
- Gruppe: Øverste 500
- Detaljer: Øverste 20

### <a name="r--python-visuals"></a>R- og Python-visualiseringer
Begrænset til 150.000 rækker. Hvis der er valgt flere end 150.000 rækker, bruges kun de øverste 150.000 rækker

### <a name="ribbon-chart"></a>Bånddiagram
- I kategoritilstand
    - Kategorier: Virtualisering (datavindue) ved hjælp af vindue på 500 rækker ad gangen
    - Serie: Øverste 60
    - I skalartilstand (dynamiske grænser kan anvendes)
        - Maksimumpunkter: 10.000
        - Kategorier: Eksempel på 500 værdier
        - Serie: Øverste 20-værdier

### <a name="shape-map-preview"></a>Figurkort (prøveversion)
Figurkortet kan bruge statistikker eller dynamiske grænser. 
- Maksimumpunkter: 1.500
- Kategorier: Øverste 500

### <a name="table"></a>Tabel
- Værdier: Virtualisering (datavindue) ved hjælp af vindue på 500 rækker ad gangen

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>Trækort (kan bruge statistikker eller dynamiske grænser)
- Maksimumpunkter: 3,500
- Gruppe: Øverste 500
- Detaljer: Øverste 20

### <a name="waterfall-chart"></a>Vandfaldsdiagram
- Når der kun er kategoribucket
    - Maksimumpunkter: 3,500
    - Kun kategori – øverste 3.500
- Når både kategori og opdeling er til stede
    - Kategori: Virtualisering (datavindue) ved hjælp af vindue på 30 rækker ad gangen
    - Opdeling – Øverste 200 værdier


## <a name="next-steps"></a>Næste trin
[Visualiseringstyper](power-bi-report-visualizations.md)
