---
title: Sideinddelte rapporter i Power BI-tjenesten
description: Dokumentation, der beskriver sideinddelte rapporter, og hvordan du får dem vist ie Power BI-tjenesten
author: mihart
ms.reviewer: christopher.finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/11/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 15482b575d7fc923059964ea47a173fda6c7f600
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/13/2020
ms.locfileid: "91983163"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Sideinddelte rapporter i Power BI-tjenesten

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Du har lært om [Power BI-rapporter](end-user-reports.md), og det er de typer rapporter, der er størst sandsynligvis for, at du støder på. Power BI-rapporter er optimeret til udforskning og interaktivitet. En salgsrapport, hvor forskellige sælgere vil opdele dataene i den samme rapport for deres specifikke område/branche/kunde og se, hvordan tallene ændres, vil fungere bedst som en Power BI-rapport.

Der er dog en anden type rapport, som kaldes en *sideinddelt rapport*. Modtagelse og visning af sideinddelte rapporter kræver en Power BI Pro-licens, for at rapporten kan gemmes i Premium-kapacitet.  [Få mere at vide om licenser](end-user-license.md).  

## <a name="identify-a-paginated-report"></a>Identificer en sideinddelt rapport

På indholdslister og på landingssiden for startsiden kan sideinddelte rapporter identificeres via deres ikon ![ikon for sideinddelt rapport](media/end-user-paginated-report/power-bi-report-icon.png).  En sideinddelt rapport kan deles med dig direkte eller som en del af en [Power BI-app](end-user-apps.md). Hvis rapport*designeren* har givet dig tilladelser, kan du dele den sideinddelte rapport igen og oprette abonnement til dig selv og andre.


![Rapportliste med én standardrapport og én sideinddelt rapport.](./media/end-user-paginated-report/power-bi-report-lists.png)

## <a name="what-is-a-paginated-report"></a>Hvad er en sideinddelt rapport?

Disse rapporter kaldes *sideinddelte*, fordi de er formateret til at passe til udskrevet side. Én fordel er, at de alle viser alle dataene i en tabel, selvom tabellen strækker sig over flere sider. Sideinddelte rapporter kaldes også nogle gange "perfekt pixel", fordi *rapportdesignere* kan styre deres rapportsidelayout helt præcist.

Sideinddelte rapporter er bedst til scenarier, hvor der kræves megen formatering og perfekt pixeleret output, der er optimeret til udskrivning eller generering af PDF. Et driftsregnskab er et godt eksempel på den type rapport, du sandsynligvis ville se som en sideinddelt rapport.

## <a name="how-do-paginated-reports-work"></a>Hvordan fungerer sideinddelte rapporter?

Når rapport*designere* opretter en sideinddelt rapport, opretter de faktisk en *rapportdefinition*. Den indeholder ikke dataene. Den angiver, hvor dataene skal hentes, hvilke data der skal hentes, og hvordan dataene skal vises. Når du kører rapporten, bruger rapportbehandleren den rapportdefinitionen, henter dataene og kombinerer det med rapportlayoutet for at generere rapporten. Nogle gange viser rapporten standarddata. Andre gange skal du angive parametre, før rapporten kan vise nogen data. 

Vælg en sideinddelt rapport for at åbne den i Power BI-tjenesten. Hvis den indeholder parametre, skal du vælge dem, før du kan få vist rapporten.

   ![Parametre for rapporten](./media/end-user-paginated-report/power-bi-select-parameters.png)

Det er typisk omfanget af interaktionen, der angiver parametrene. Hvis du er faktureringsanalytiker, kan du bruge sideinddelte rapporter til at oprette eller udskrive fakturaer. Hvis du er salgschef, kan du bruge sideinddelte rapporter til at få vist ordrer efter butik eller sælger. 

Denne enkle sideinddelte rapport genererer profit efter år, når du har valgt parameteren **Year**. 

![Enkel rapport med én parameter](./media/end-user-paginated-report/power-bi-one-parameter.png)

Sammenlignet med sideinddelte rapporter er Power BI-rapporter meget mere interaktive. Power BI rapporter giver mulighed for ad hoc-rapportering og understøtter mange flere typer visuals, herunder brugerdefinerede visuals.



## <a name="interact-with-a-paginated-report"></a>Interager med en sideinddelt rapport

Den måde, du interagerer med en sideinddelt rapport på, adskiller sig fra den måde, du interagerer med andre rapporter på. Du kan f. eks. udskrive, oprette bogmærker, eksportere og kommentere, men der er mindre interaktivitet. Sideinddelte rapporter kræver ofte input fra dig, hvis du vil udfylde rapportlærredet.  Andre gange vises der standarddata i rapporten, og du kan angive parametre for at få vist andre.

### <a name="print-a-paginated-report"></a>Udskriv en sideinddelt rapport

*Sideinddelte* rapporter formateres, så de passer til en side og kan udskrives. Det, du ser i browseren, er det, du får vist, når du udskriver. Og hvis rapporten har en lang tabel, udskrives hele tabellen, også selvom den spænder over flere sider. 

Sideinddelte rapporter kan indeholde mange sider. Denne rapport indeholder f.eks. 563 sider. Hver side viser præcis én side pr. faktura og har gentagne sidehoveder og sidefødder. Når du udskriver denne rapport, får du sideskift mellem fakturaer.

   ![Side ét i en sideinddelt rapport til Tailspin Toys](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>Naviger i den sideinddelte rapport

I denne salgsordrerapport er der tre parametre: Business type, Reseller og Order number. 

![rapport med tre parametre](./media/end-user-paginated-report/power-bi-parameter-bar.png)

Hvis du vil ændre de oplysninger, der vises, skal du angive nye værdier for de tre parametre og vælge **Vis rapport**. Her har vi valgt **Specialty bike shop**, **Alpine Ski House** og ordrenummer **SO46085**. Hvis du vælger **Vis rapport** opdateres vores rapportlærred med denne nye salgsordre.

![rediger parametrene](./media/end-user-paginated-report/power-bi-orders.png)

Den nye salgsordre vises med de parametre, vi har valgt. 

![en ny salgsordre](./media/end-user-paginated-report/power-bi-new-orders.png)

Nogle sideinddelte rapporter kan indeholde mange sider.  Brug sidekontrolelementerne til at navigere i rapporten. 

![sidekontrolelementer](./media/end-user-paginated-report/power-bi-page-control.png)

### <a name="export-the-paginated-report"></a>Eksporter den sideinddelte rapport
Du har en række forskellige muligheder for eksport af sideinddelte rapporter, herunder PDF, Word, XML, PowerPoint, Excel med mere. Når du eksporterer, bevares så meget af formateringen som muligt. Sideinddelte rapporter, der eksporteres til Excel, Word, PowerPoint, MHTML og PDF, så du kan f. eks. bevare formateringen "perfekt pixel". 

![Skærmbillede, der viser en eksporteret sideinddelt rapport.](./media/end-user-paginated-report/power-bi-export-choices.png)

![fire forskellige eksporttyper](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>Abonner på den sideinddelte rapport
Når du abonnerer på en sideinddelt rapport, sender Power BI dig en mail med rapporten som en vedhæftet fil. Når du konfigurerer dit abonnement, vælger du ofte, hvordan du vil modtage mails: dagligt, ugentligt, hver time eller månedligt. Abonnementet indeholder en vedhæftet PDF-fil med hele outputtet, op til 25 MB, for rapporten. Eksportér hele rapporten, eller vælg parametrene i forvejen. Vælg mellem mange forskellige typer vedhæftede filer, herunder Excel, PDF, PowerPoint og meget mere.  

![Formater for abonnement](./media/end-user-paginated-report/power-bi-export-choices.png)

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

- En sideinddelt rapport kan være tom, indtil du vælger parametre og vælger **Vis rapport**.

- Hvis du ikke har nogen sideinddelte rapporter, kan det skyldes, at ingen har delt denne type rapport med dig. Det kan også betyde, at systemadministratoren ikke har aktiveret sideinddelte rapporter for dig. 

 

## <a name="next-steps"></a>Næste trin
- [Power BI-rapporter](end-user-reports.md)
- [Sideinddelte rapporter i Power BI: Ofte stillede spørgsmål](../paginated-reports/paginated-reports-faq.md)
- Har du flere spørgsmål? Prøv at spørge [Power BI-community'et](https://community.powerbi.com/).
