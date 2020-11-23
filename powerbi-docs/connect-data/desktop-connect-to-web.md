---
title: Opret forbindelse til en webside fra Power BI Desktop
description: Opret nemt forbindelse til og brug data på en webside i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f2e61617e060d90a30aebd1ddc47a72b712c271c
ms.sourcegitcommit: 029aacd09061a8aa45b57f05d0dc95c93dd16a74
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/12/2020
ms.locfileid: "94559830"
---
# <a name="connect-to-webpages-from-power-bi-desktop"></a>Opret forbindelse til websider fra Power BI Desktop

Du kan oprette forbindelse til en webside og importere data i Power BI Desktop for at bruge dem i dine visualiseringer og datamodeller.

Vælg **Hent data > Web** på båndet **Hjem** i Power BI Desktop.

![Skærmbillede af Power BI Desktop, hvor valget Web vises.](media/desktop-connect-to-web/connect-to-web-01.png)

Der vises en dialogboks, hvor du bliver bedt om at angive URL-adressen på den webside, hvorfra du vil importere data.

![Skærmbillede af dialogboksen Web, hvor feltet URL-adresse vises.](media/desktop-connect-to-web/connect-to-web-02.png)

Når du har skrevet eller indsat URL-adressen, skal du vælge **OK**. I Power BI Desktop bliver du bedt om at angive, hvordan du vil oprette adgang til webindholdet.

![Legitimationsoplysninger, der skal bruges, når der oprettes forbindelse til internettet](media/desktop-connect-to-web/connect-to-web-03.png)

Power BI Desktop opretter forbindelse til websiden og præsenterer derefter sidens tilgængelige data i vinduet **Navigator**. Når du vælger et af de tilgængelige dataelementer, f.eks. en tabel over hele siden, vises der et eksempel på disse data i højre side af vinduet **Navigator**.

![Skærmbillede af dialogboksen Navigator, der viser en prøveversion af den valgte tabels data.](media/desktop-connect-to-web/connect-to-web-04.png)

Du kan vælge knappen **Transformér data**, hvilket starter **Forespørgselseditor**, hvor du kan udforme og transformere dataene på den pågældende webside, før du importerer den til Power BI Desktop. Du kan også vælge knappen **Indlæs** og importere alle dataelementer, du har valgt i venstre rude.

Når du vælger **Indlæs**, importerer Power BI Desktop de valgte elementer og gør dem tilgængelige i ruden **Felter**, som du finder i højre side af visningen Rapporter i Power BI Desktop.

![Skærmbillede af ruden Felter, der viser listen over valgte tabeller.](media/desktop-connect-to-web/connect-to-web-05.png)

Så nemt er det at oprette forbindelse til en webside og hente sidens data ind i Power BI Desktop.

Herfra kan du trække felterne til Rapportcanvas og oprette alle de visualiseringer, du vil. Du kan også bruge dataene fra denne webside på samme måde som andre data – du kan f.eks. forme dem, oprette relationer mellem dem og andre datakilder i din model og udføre andre handlinger for at oprette præcist den Power BI-rapport, du ønsker.

Hvis du vil se yderligere oplysninger om, hvordan du opretter forbindelse til en webside, skal du se [guiden Introduktion til Power BI Desktop](../fundamentals/desktop-getting-started.md).

## <a name="certificate-revocation-check"></a>Kontrol af certifikattilbagekaldelse

Der anvendes sikkerhed til webforbindelser i Power BI for at beskytte dine data. I nogle scenarier, f. eks. hentning af webanmodninger med Fiddler, fungerer webforbindelser muligvis ikke korrekt. Hvis du vil give mulighed for disse scenarier, skal du fjerne markeringen i afkrydsningsfeltet **Aktivér kontrol af certifikattilbagekaldelse** i Power BI Desktop og derefter genstarte Power BI Desktop. 

Du kan ændre denne indstilling ved at vælge **Filer > Indstillinger** og derefter vælge **Sikkerhed** i ruden til venstre. Du kan se afkrydsningsfeltet på følgende billede. Hvis du fjerner markeringen i afkrydsningsfeltet, bliver webforbindelser mindre sikre. 

![Aktivér eller deaktiver kontrol af certifikattilbagekaldelse](media/desktop-connect-to-web/connect-to-web-06.png)


## <a name="next-steps"></a>Næste trin
Du kan oprette forbindelse til mange forskellige typer data ved hjælp af Power BI Desktop. Du kan finde flere oplysninger om datakilder i følgende ressourcer:

* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Opret forbindelse til Excel-projektmapper i Power BI Desktop](desktop-connect-excel.md)   
* [Opret forbindelse til CSV-filer i Power BI Desktop](desktop-connect-csv.md)   
* [Angiv data direkte i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
