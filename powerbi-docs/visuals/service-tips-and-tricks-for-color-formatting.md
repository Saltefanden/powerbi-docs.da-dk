---
title: Tip og tricks til formatering i rapporter
description: Tip og tricks til formatering i Power BI-rapporter
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: conceptual
ms.date: 10/29/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 0ab6b799c8c78ab2e76a63a3ec5ee3f37f960b03
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415743"
---
# <a name="tips-and-tricks-for-formatting-in-reports"></a>Tip og tricks til formatering i rapporter

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

Power BI indeholder mange forskellige måder at tilpasse dine rapporter på. Denne artikel indeholder en samling af tip, som kan gøre dine Power BI-visualiseringer mere overbevisende, interessante og tilpasset efter dine behov.

Der findes følgende tip. Har du et andet fantastiske tip? Fantastisk! Send det til os, og vi finder ud af, om det skal føjes til listen.

* Anvend et tema på hele rapporten
* Skift farve på et enkelt datapunkt
* Betinget formatering
* Basér farverne i et diagram på en numerisk værdi
* Basér farven på datapunkter på en feltværdi
* Tilpas farver, der bruges i farveskalaen
* Brug divergerende farveskalaer
* Føj farve til tabelrækker
* Sådan fortryder du i Power BI

Hvis du vil foretage ændringer, skal du have redigeringstilladelser til rapporten. Åbn rapporten i **Rapportvisning** i Power BI Desktop. I Power BI-tjenesten betyder det, at du skal åbne rapporten og vælge **Rediger** på menulinjen, som vist på følgende billede.

![her finder du menuen Rediger](media/service-tips-and-tricks-for-color-formatting/power-bi-editing-view.png)

Når ruderne **Filtre** og **Visualiseringer** vises langs højre side af rapportcanvasset, er du klar til at starte tilpasningen. Hvis ruderne ikke vises, skal du vælge pilen i øverste højre hjørne for at åbne dem.

![rapportcanvas i redigeringsvisning](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-filter.png)

## <a name="apply-a-theme"></a>Anvend et tema
Med rapporttemaer kan du anvende designændringer på hele rapporten, f.eks. bruge virksomhedsfarver, ændre ikonsæt eller anvende ny standardformatering af visualiseringer. Når du anvender et rapporttema, anvendes farver og formatering fra det valgte tema på alle visualiseringer i rapporten. Du kan få mere at vide under [Brug rapporttemaer](../create-reports/desktop-report-themes.md)

![Ikonet Skift tema på menulinjen](media/service-tips-and-tricks-for-color-formatting/power-bi-themes.png)

Her har vi anvendt temaet **Innovativt** på rapporten Salg og marketing.

![Anvendelse af temaet Innovativt](media/service-tips-and-tricks-for-color-formatting/power-bi-theme-innovate.png)

## <a name="change-the-color-of-a-single-data-point"></a>Skift farve på et enkelt datapunkt
Nogle gange kan du få brug for at fremhæve ét bestemt datapunkt. Måske er det et salgstal for lanceringen af et nyt produkt eller højere kvalitetsbedømmelser efter lancering af et nyt program. Med Power BI kan du fremhæve et bestemt datapunkt ved at ændre dets farve.

Følgende visualisering rangordner solgte enheder efter produktsegment. 

![Skift af datafarver til grå](media/service-tips-and-tricks-for-color-formatting/power-bi-format.png)

Forestil dig nu, at du vil fremhæve segmentet **Convenience** for at vise, hvor godt dette nye segment præsterer, ved hjælp af farve. Her er trinnene:

Udvid kortet **Datafarver**, og slå skyderen Til for **Vis alle**. Farverne vises nu for hvert dataelement i visualiseringen. Du kan nu redigere et hvilket som helst datapunkt.

![Formatrude med Vis alle indstillet til Til](media/service-tips-and-tricks-for-color-formatting/power-bi-show-all.png)

Angiv **Convenience** til orange. 

![søjlediagram med én orange kolonne](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

Når du har foretaget et valg, får datapunktet **Convenience** en pæn orange nuance, der helt sikkert skiller sig ud.

Selvom du ændrer visualiseringstyper og derefter vender tilbage, kan Power BI huske valget, og **Convenience** er stadig orange.

Du kan ændre farven på et datapunkt for én, flere eller alle dataelementer i visualiseringen. Måske vil du gerne have, at din visualisering får virksomhedens gule, grønne og blå farver. 

![liggende søjlediagram i grønne, gule og blå farver](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Der er forskellige ting, du kan gøre med farver. I det næste afsnit kigger vi på betinget formatering.

## <a name="conditional-formatting-for-visualizations"></a>Betinget formatering af visualiseringer
Visualiseringer drager ofte fordel af en dynamisk farveindstilling baseret på den numeriske værdi i et felt. Ved at gøre dette kan du få vist en anden værdi end normalt for størrelsen på en søjle og få vist to værdier på en enkelt graf. Eller du kan bruge det til at fremhæve datapunkter over (eller under) en bestemt værdi – måske fremhæve områder med lav rentabilitet.

Følgende afsnit viser forskellige metoder til at basere farve på en numerisk værdi.

### <a name="base-the-color-of-data-points-on-a-value"></a>Basér farven på datapunkter på en værdi
Hvis du vil ændre farven på basis af en værdi, skal du vælge en visualisering for at aktivere den. Åbn ruden Formatering ved at vælge malerulleikonet og derefter vælge kortet **Datafarver**. Vælg fx-ikonet under **Standardfarve**.  

![vælg indstillingen Betinget formatering ved at klikke på de tre lodrette prikker](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional.png)

Brug rullemenuerne i ruden **Standardfarve** til at identificere de felter, der skal bruges til betinget formatering. I dette eksempel har vi valgt feltet **Salgsfakta** > **Enheder i alt** og valgt lyseblå for den **laveste værdi** og mørkeblå for den **højeste værdi**. 

![indstillinger for betinget formatering efter datafarve](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![søjlediagram, hvor standardfarver er anvendt](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

Du kan også formatere farven på visualiseringen ved hjælp af et felt, der ikke er en del af visualiseringen. På følgende billede benyttes **Procentvis markedsandel SPLY ÅTD**. 

![søjlediagram med flere nuancer af blå](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


Du kan se, at selvom vi har solgt flere enheder af både **Produktivitet** og **Ekstrem** (deres kolonner er højere), har **Moderation** en større **Procentvis markedsandel SPLY ÅTD** (kolonnen indeholder en mere mættet farve).

### <a name="customize-the-colors-used-in-the-color-scale"></a>Tilpas de farver, der bruges i farveskalaen
Du kan også ændre den måde, som værdierne knyttes til disse farver på. På det følgende billede er farverne for **Minimum** og **Maksimum** indstillet til henholdsvis orange og grøn.

Læg mærke til på dette første billede, hvordan søjlerne i diagrammet afspejler det farveforløb, der vises i bjælken. Den højeste værdi er grøn, den laveste er orange, og hver søjle mellem er farvet med en nuance af spektret mellem grøn og orange.

![søjlediagram, der viser farveforløb for farver fra grøn til orange](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

Lad os nu se, hvad sker der, hvis vi angiver numeriske værdier i værdifelterne **Minimum** og **Maksimum**. Vælg **Brugerdefineret** på rullelisterne for både **Minimum** og **Maksimum**, angiv **Minimum** til 3.500, og angiv **Maksimum** til 6.000.

![Formatér betinget efter tal](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting-numbers.png)

Ved at angive disse værdier anvendes farveforløb ikke længere på værdierne i diagrammet, der er under **Minimum** eller over **Maksimum**. En søjle med en værdi over værdien **Maksimum** har farven grøn, og en søjle med en værdi under værdien **Minimum** har farven rød.

![resultat af betinget formatering efter tal](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

### <a name="use-diverging-color-scales"></a>Brug divergerende farveskalaer
Dine data kan nogle gange have en naturligt divergerende skala. Et tempereret område har for eksempel et naturligt centrum ved frysepunktet, og en rentabilitetsbedømmelse har et naturligt midtpunkt (nul).

Hvis du vil bruge divergerende farveskalaer, skal du markere afkrydsningsfeltet for **Divergerende**. Når **Divergerende** er slået til, vises en yderligere farvevælger, der kaldes **Centrum**, som vist på følgende billede.

![Dialogboksen Standardfarve med Farveskala valgt](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging-colors.png)

Når skyderen **Divergerende** er slået til, kan du angive farverne for **Minimum**, **Maksimum** og **Centrum** separat. På det følgende billede er **Centrum** indstillet til .2 for **Procentvis markedsandel SPLY ÅTD**, hvorfor søjler med værdier over .2 er en gradueret nuance af grøn, og søjler under en er nuancer af rød.

![søjlediagram med røde og grønne søjler](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

## <a name="add-color-to-table-rows"></a>Føj farve til tabelrækker
Tabeller og matrixer indeholder mange muligheder for farveformatering. 

![Skærmbillede, der viser en tabel med rækker i skiftevist hvid og grå.](media/service-tips-and-tricks-for-color-formatting/power-bi-table.png)

En af de hurtigste måder at anvende farver på i en tabel eller matrix er at åbne fanen Formatering og vælge **Typografi**.  På billedet nedenfor har vi valgt **Overskrift med fed skrift og blinkende rækker**.

![Skærmbillede, der viser typografiindstillingen Fed for iøjnefaldende overskriftsrækker, hvilket gør overskriftsrækken sort og de andre rækker lyse- og mørkegrøn.](media/service-tips-and-tricks-for-color-formatting/power-bi-table-style.png)

Eksperimentér med andre indstillinger for farveformatering. På dette billede har vi ændret baggrundsfarven under **Kolonneoverskrifter** og ændret både **baggrundsfarven** og **den alternative baggrundsfarve** for **Værdier** (rækker).

![Skærmbillede, der viser værdivælgere for Baggrundsfarve og Alternativ baggrundsfarve.](media/service-tips-and-tricks-for-color-formatting/power-bi-table-rows.png)

## <a name="how-to-undo-in-power-bi"></a>Sådan fortryder du i Power BI
Som mange andre Microsoft-tjenester og -software giver Power BI en nem måde at fortryde den seneste kommando på. Lad os for eksempel antage, at du ændrer farven på et datapunkt eller en serie af datapunkter, og du ikke kan lide farven, når den vises i visualiseringen. Du kan ikke huske præcis, hvilken farve det havde før, men du ved, du vil farven tilbage!

Hvis du vil **fortryde** din sidste handling, eller de sidste par handlinger, skal du blot trykke på CTRL+Z.

Hvis du vil kassere alle de ændringer, du har foretaget på kortet Formatering, skal du vælge **Gendan standardindstillingerne**.

![Kortet Formatering med Gendan standardindstillingerne vist nederst](media/service-tips-and-tricks-for-color-formatting/power-bi-revert.png)

## <a name="give-us-your-feedback"></a>Giv os din feedback
Har du et tip, du vil dele? Send det til os, og vi finder ud af, om det skal medtages her.

## <a name="next-steps"></a>Næste trin
[Introduktion til farveformatering og akseegenskaber](service-getting-started-with-color-formatting-and-axis-properties.md)

[Deling af rapporter](../collaborate-share/service-share-reports.md).

