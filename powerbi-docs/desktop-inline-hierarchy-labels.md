---
title: Brug indbyggede hierarkietiketter i Power BI Desktop
description: Brug indbyggede hierarkietiketter i Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 470b25af4ee59542d010d3e649d25da7305319ad
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/15/2017
---
# <a name="use-inline-hierarchy-labels-in-power-bi-desktop"></a>Brug indbyggede hierarkietiketter i Power BI Desktop
**Power BI Desktop** understøtter brugen af **indbyggede hierarkietiketter**, som er den første af to funktioner, der skal bruges til at forbedre den hierarkiske detailudledning. Den anden funktion, som i øjeblikket er under udvikling, er muligheden for at bruge indlejrede hierarkietiketter (hold øje med den – der sker jævnligt opdateringer).   

## <a name="how-inline-hierarchy-labels-work"></a>Sådan fungerer indbyggede hierarkietiketter
Med indbyggede hierarkietiketter kan du se hierarkietiketter, når du udvider visuelle elementer ved hjælp af funktionen **Udvid alle**. En af fordelene ved at se disse hierarkietiketter er, at du også kan vælge at **sortere** efter disse forskellige hierarkietiketter, når du udvider dine hierarkiske data.

### <a name="using-the-built-in-expand-all-feature-without-sorting-by-hierarchy-labels"></a>Brug den indbyggede funktion Udvid alle (uden at sortere efter hierarkietiketter)
Før vi kigger på, hvordan indbyggede hierarkietiketter fungerer, skal vi se på, hvordan standardfunktionen **Udvid alle** fungerer. Det hjælper os med at forstå (og sætte pris på), hvor nyttige indbyggede hierarkietiketter kan være.

På følgende billede vises et visuelt element i et liggende søjlediagram for årligt salg. Når du højreklikker, du kan vælge **Udvid alle**.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_4.png)

Når **Udvid alle** er markeret, udvider det visuelle element datohierarkiet fra *År* til *Kvartal*, som vist på følgende billede.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_5.png)

Bemærk, at etiketterne *År* og *Kvartal* vises indlejret sammen. Dette etiketskema fortsætter, efterhånden som du bruger **Udvid alle** ned til bunden af hierarkiet.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_6.png)

Sådan fungerer det indbyggede *Dato*-hierarki, der er knyttet til felter, som har datatypen *dato/klokkeslæt*. Lad os gå videre til næste afsnit og se på, hvordan den nye funktion for indbyggede hierarkietiketter adskiller sig.

### <a name="using-inline-hierarchy-labels"></a>Brug indbyggede hierarkietiketter
Lad os nu se på en anden diagramtype – ved hjælp af data med uformelle hierarkier. I det følgende visuelle element har vi et liggende søjlediagram med **Salgsbeløb**, der bruger *Farve* som akse. I disse data udgør *Farve* og *Klasse* et uformelt hierarki. Her kan du igen vælge *Udvid alle* for at analysere ned i hierarkiet.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_7.png)

Hvis du vælger **Udvid alle**, vises næste niveau med indbygget visning af hierarkietiketter. Som standard er indbyggede hierarkier sorteret efter måleværdien – i dette tilfælde **Salgsbeløb**. Hvis indbyggede hierarkietiketter er aktiveret, kan du også vælge at sortere disse data efter hierarki ved at vælge ellipsen i øverste højre hjørne (**...** ) og derefter vælge **Sortér efter > Farveklasse** som vist på følgende billede.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_8.png)

Når **Farveklasse** er valgt, sorteres dataene på baggrund af det valgte uformelle hierarki som vist på følgende billede.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_9.png)

> [!NOTE]
> Funktionen for indbyggede hierarkietiketter tillader endnu ikke, at det indbyggede tidshierarki sorteres efter værdi. Det kan kun sorteres efter hierarkiets rækkefølge.
> 
> 

## <a name="troubleshooting"></a>Fejlfinding
Det kan ske, at dine visuelle elementer er fastlåst i en tilstand, hvor det indbyggede hierarkiniveau er udvidet. I nogle tilfælde er nogle af de visuelle elementer fastlåst i den tilstand, hvor de blev udvidet, og i dette tilfælde virker det ikke at fjerne sig fra detaljerne. Det kan ske, hvis du har udført følgende trin (løsningen på dette problem findes *under* disse trin):

Trin, der kan forårsage, at dine visuelle elementer er fastlåst i udvidet tilstand:

1. Du aktiverer funktionen for **indbyggede hierarkietiketter**
2. Du opretter nogle visuelle elementer med hierarkier
3. Derefter vælger du **Udvid alle** og gemmer din fil
4. Derefter *deaktiverer* du funktionen for **indbyggede hierarkietiketter** og genstarter Power BI Desktop
5. Så åbner du filen igen

Hvis du kommer til at udføre disse trin, og dine visuelle elementer er fastlåst i udvidet tilstand, kan du gøre følgende for at løse problemet:

1. Aktivér funktionen for **indbyggede hierarkietiketter** igen, og genstart derefter Power BI Desktop
2. Åbn din fil igen, og gå tilbage til toppen af de berørte visuelle elementer
3. Gem filen
4. Deaktiver funktionen for **indbyggede hierarkietiketter** igen, og genstart derefter Power BI Desktop
5. Åbn filen igen

Du kan også bare slette det visuelle element og oprette det igen.
