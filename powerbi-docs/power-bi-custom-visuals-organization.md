---
title: Brug af brugerdefinerede visualiseringer til virksomheder i Power BI
description: Brug, administrer og opret brugerdefinerede visualiseringer til virksomheder i Power BI
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/06/2018
ms.author: maghan
LocalizationGroup: Visualizations
ms.openlocfilehash: 6f7827f7804fcd52e7d922ebc8ffad5a8036b33c
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 02/24/2018
---
# <a name="using-organization-custom-visuals-in-power-bi-preview"></a>Brug af brugerdefinerede visualiseringer til virksomheder i Power BI (prøveversion)

Du kan bruge brugerdefinerede visualiseringer i Power BI til at oprette unikke visualiseringer, som er skræddersyet til dig eller de dataindsigter, du forsøger at gengive. Denne type brugerdefineret visualisering oprettes ofte af udviklere, og de oprettes ofte, når mængden af visualiseringer, der er inkluderet i Power BI, ikke opfylder deres behov. 

I nogle virksomheder er brugerdefinerede visualiseringer endnu vigtigere: De kan være nødvendige for at gengive bestemte data eller indsigter, der er unikke for virksomheden; de kan have særlige datakrav; eller de kan fremhæve private forretningsmetoder. Sådanne virksomheder har brug for at udvikle brugerdefinerede visualiseringer, dele dem i hele virksomheden og sikre, at de bliver vedligeholdt korrekt. Med brugerdefinerede visualiseringer i Power BI (nu en prøveversion) kan virksomheder gøre lige præcis det. 

På følgende billede vises processen for, hvordan den brugerdefinerede visualisering til virksomheder (prøveversion) i Power BI kommer fra administratoren, fortsætter via udvikling og vedligeholdelse og ender hos dataanalytikeren.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

## <a name="how-to-enable-organizational-custom-visuals-preview"></a>Sådan aktiverer du brugerdefinerede visualiseringer til virksomheder (prøveversion)

Brugerdefinerede visualiseringer til virksomheder er i øjeblikket en prøveversion, så du skal aktivere funktionen i Power BI Desktop. Du aktiverer denne funktion i prøveversion ved at vælge Fil > Indstillinger > Indstillinger på båndet. Vælg derefter Prøveversion i ruden til venstre, og markér derefter afkrydsningsfeltet ud for Mine brugerdefinerede visualiseringer til virksomheder, som vist på følgende billede.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-02.jpg)

Visualiseringer til virksomheder udrulles og administreres af Power BI-administratoren via Administrationsportalen. Når visualiseringerne er udrullet i virksomhedens lager, kan brugerne nemt finde dem og importere de brugerdefinerede visualiseringer til virksomheder i deres rapporter direkte fra Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Brug af brugerdefinerede visualiseringer til virksomheder

Du kan få mere at vide om, hvordan du bruger brugerdefinerede visualiseringer til virksomheder i de rapporter, du har oprettet, i følgende artikel: [Få mere at vide om, hvordan du importerer visualiseringer til virksomheder i dine rapporter](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Administration af brugerdefinerede visualiseringer til virksomheder

Du kan få mere at vide om, hvordan du administrerer og udruller brugerdefinerede visualiseringer til virksomheder i din virksomhed i følgende artikel: [Få mere at vide om udrulning og administration af brugerdefinerede visualiseringer til virksomheder](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> En brugerdefineret visualisering kan indeholde kode, der kan udgøre en risiko for sikkerheden eller beskyttelse af personlige oplysninger. Sørg for, at du har tillid til forfatteren af og kilden til en brugerdefineret visualisering, før du udruller den i virksomhedens lager. 
> 

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger
 
Da brugerdefinerede visualiseringer til virksomheder er en prøveversion, er der nogle overvejelser og begrænsninger, som du skal være opmærksom på og tage højde for.
 
Administrator:

* Ældre brugerdefinerede visualiseringer (f.eks. brugerdefinerede visualiseringer, som ikke er bygget oven på de nye versionerede API'er) understøttes ikke.

* Direkte opdatering understøttes endnu ikke. Hvis du vil opdatere en visualisering, skal du uploade en ny version af visualiseringen til virksomhedens lager. Sørg for, at den har det samme visualiserings-id i PBIVIZ-filen. Forfattere af rapporter kan derefter importere den nye version i deres rapport og foretage en direkte erstatning af den aktuelle version af visualiseringen i rapporten.

* Hvis en brugerdefineret visualisering slettes fra lageret, gengives alle eksisterende rapporter, som bruger den slettede visualisering, ikke. Du kan ikke fortryde en sletning.
 
Slutbruger:

* Brug af den samme visualisering (det samme visualiserings-id) fra den offentlige markedsplads (AppSource) og fra virksomhedens lager understøttes ikke. I sådanne tilfælde bruges den visualisering, som blev importeret sidst.

* Ekstern deling af visualiseringer til virksomheder på dashboards og i rapporter understøttes ikke. Brugere uden for virksomheden, som får vist et dashboard med en brugerdefineret visualisering, ser en tom visualisering. 

* Arbejdsområdesamling i Power BI understøttes ikke for visualiseringer til virksomheder.

* Brugerdefinerede visualiseringer til virksomheder i rapporter, der er publiceret på internettet, gengives ikke.

* Visio-visualiseringen, PowerApps-visualiseringen og GlobeMap-visualiseringen fra AppSource-markedspladsen gengives ikke, hvis de udrulles via virksomhedens lager.

* Hvis administratoren sletter en brugerdefineret visualisering fra lageret, og denne visualisering bruges i en rapport, så gengives visualiseringen ikke længere, og den skal fjernes fra rapporten, før rapporten kan gemmes.