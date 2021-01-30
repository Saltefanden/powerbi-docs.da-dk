---
title: Filtre og fremhævning i Power BI-rapporter
description: Om filtre og markering i Power BI-rapporter
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 01/29/2021
LocalizationGroup: Reports
ms.openlocfilehash: 572bbc8b24fc3ebf8ee2890480eff25eab87d37d
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087815"
---
# <a name="filters-and-highlighting-in-power-bi-reports"></a>Filtre og fremhævning i Power BI-rapporter
 Denne artikel introducerer dig for filtrering og fremhævning i Power BI-tjenesten. Brugeroplevelsen er stort den samme i Power BI Desktop. *Filtre* fjerner alt andet end de data, du vil fokusere på. *Fremhævning* filtreres generelt ikke. I de fleste visuelle elementer fjernes de ikke-relaterede data ikke. I stedet fremhæves delmængden af relaterede data. Resten af dataene forbliver synlige, men nedtonede. Se [ad hoc-kryds filtrering og tværgående fremhævning](#ad-hoc-cross-filtering-and-cross-highlighting) senere i denne artikel for at få flere oplysninger.

Du kan filtrere og fremhæve rapporter i Power BI på mange forskellige måder. Hvis vi havde inkluderet alle oplysningerne i én artikel, ville det være forvirrende, så vi har opdelt dem i følgende afsnit:

* Introduktion til filtre og fremhævning – den artikel, du er ved at læse nu.
* Sådan [opretter og bruger du filtre i Redigeringsvisning](power-bi-report-add-filter.md) i rapporter i Power BI Desktop og Power BI-tjenesten. Når du har redigeringsrettigheder til en rapport, kan du oprette, ændre og slette filtre i rapporter.
* Sådan [filtrerer og fremhæver du visualiseringer i en rapport, der er delt med dig](../consumer/end-user-interactions.md) i Læsevisning i en rapport i Power BI-tjenesten. Her har du færre valgmuligheder, men du har stadig en lang række muligheder for filtrering og fremhævning.  
* En detaljeret rundvisning af [kontrolelementerne til filtrering og fremhævning, som er tilgængelige i Redigeringsvisning](power-bi-report-add-filter.md), i Power BI Desktop og Power BI-tjenesten. I denne artikel får du et detaljeret indblik i forskellige filtertyper, f.eks. dato og klokkeslæt, numerisk og tekst. Den dækker også forskellene mellem grundlæggende og avancerede indstillinger.
* Nu hvor du ved, hvordan filtre og fremhævning fungerer som standard, [kan du lære, hvordan du ændrer den måde, visualiseringer på en side filtreres og fremhæver hinanden på](service-reports-visual-interactions.md)

**Vidste du det?** Power BI indeholder en ny filtreringsoplevelse. Læs mere om [den nye filtreringsoplevelse i Power BI-rapporter](power-bi-report-filter.md).

![Ny filteroplevelse](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading.png)


## <a name="intro-to-the-filters-pane"></a>Introduktion til ruden Filtre

Du kan anvende filtre i ruden **Filtre** eller ved [at foretage valg i udsnitsværktøj](../visuals/power-bi-visualization-slicers.md) direkte på selve rapporten. Ruden Filtre viser de tabeller og felter, der bruges i rapporten, og eventuelle filtre, der anvendes. 

![Ruden Filtre](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

Der findes fire typer filtre.

- **Sidefilter** gælder for alle visuelle elementer på rapportsiden.     
- **Visuelt filter** gælder for et enkelt visuelt element på rapportsiden. Du kan kun få vist filtre på visualiseringsniveau, hvis du har valgt en visualisering på rapportcanvasset.    
- **Rapportfilter** gælder for alle sider i rapporten.    
- **Detaljeadgangsfilter** gælder for en bestemt enhed i en rapport.    

Du kan søge i side-, visual- og rapportfiltre, i læse- eller redigeringsvisning, for at finde og vælge den værdi, du ønsker. 

![Søg i et filter](media/power-bi-reports-filters-and-highlighting/power-bi-search-filter.png)

Hvis filteret er markeret med ordet **Alle**, betyder det, at alle værdierne i feltet er inkluderet i filteret.  **Kæde(Alle)** på skærmbilledet nedenfor betyder f.eks., at denne rapportside inkluderer data om alle butikskæderne.  På den anden side viser filteret på rapportniveau **Regnskabsåret er 2013 eller 2014**, at rapporten kun indeholder data for regnskabsårene 2013 og 2014.

## <a name="filters-in-reading-or-editing-view"></a>Filtre i læse- eller redigeringsvisning
Du kan interagere med rapporter i to forskellige tilstande: [læsevisning](../consumer/end-user-reading-view.md) og redigeringsvisning. Hvilke filterfunktioner der er tilgængelige, afhænger af, hvilken tilstand du arbejder i.

* Du kan tilføje rapport- og sidefiltre samt detaljeadgangs- og visualiseringsfiltre i redigeringsvisning. Filtrene gemmes sammen med rapporten, når du gemmer den, også selv om rapporten er åbnet i en mobilapp. Personer, der åbner rapporten i Læsevisning, kan arbejde med de filtre, du har tilføjet, men kan ikke tilføje nye filtre.
* I læsevisning kan du anvende de eventuelle filtre, som allerede findes i rapporten, og gemme dine valg. Du kan ikke tilføje nye filtre.

### <a name="filters-in-reading-view"></a>Filtre i læsevisning
Hvis du kun har adgang til en rapport i læsevisning, ser ruden Filtre omtrent sådan ud:

![Filtre i læsevisning](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

Denne side i rapporten har seks filtre på sideniveau og et filter på rapportniveau.

Hver visual kan have filtre til alle felterne, og forfatteren til en rapport kan tilføje flere. På billedet nedenfor er der seks filtre på boblediagrammet.

![Filter på visualiseringsniveau](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

Udforsk data ved at ændre eksisterende filtre i læsevisning. De ændringer, du foretager, gemmes sammen med rapporten, også selvom rapporten er åbnet i en mobilapp. Se hvordan ved at [få en præsentation af ruden Rapportfiltre](../consumer/end-user-report-filter.md)

Når du lukker rapporten, gemmes dine filtre. Hvis du vil fortryde filtreringen og vende tilbage til standarden for filtrering, udsnit, detailudledning og sortering som angivet af rapportens forfatter, skal du vælge **Nulstil til standard** på den øverste menulinje.

![Ikon for Nulstil til standard](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

### <a name="filters-in-editing-view"></a>Filtre i redigeringsvisning
Når du har ejerrettigheder til en rapport og åbner den i redigeringsvisning, kan du se, at **Filtre** bare er ét ud af flere felter, du kan bruge til redigering.

![Filtreringsrude i Redigeringsvisning](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

Som i læsevisningen kan vi se, at denne side i rapporten har seks filtre på sideniveau og et filter på rapportniveau. Og ved at vælge boblediagrammet ser vi, at der anvendes seks filtre på visualniveau.

Vi kan udrette mere med filtre og fremhævning i læsevisning. Primært kan vi tilføje nye filtre. Se, hvordan du [tilføjer et filter i en rapport](power-bi-report-add-filter.md) og meget mere.

## <a name="ad-hoc-cross-filtering-and-cross-highlighting"></a>Ad hoc-kryds filtrering og tværgående fremhævning
Vælg en værdi-eller akseetiket i ét visuelt element for at kryds filtrere eller tværgående fremhævning af de relaterede værdier i andre visualiseringer på siden. I de fleste visuelle elementer fjerner du ikke de ikke-relaterede data i de andre visualiseringer, hvis du vælger en værdi i en visualisering. I stedet fremhæves delmængden af relaterede data. De ikke-relaterede data forbliver synlige, men nedtonede. I nogle visuelle elementer fungerer det imidlertid, at hvis du vælger en værdi i en visualisering, fungerer det mere som et filter i de andre visualiseringer. I kurvediagrammer og punktdiagrammer er det f. eks. kun de relaterede data, der forbliver synlige. De ikke-relaterede data er ikke synlige, på samme måde som du ville se med et filter. 

Hvis du vil fjerne fremhævningen, skal du vælge værdien igen eller vælge et blankt område i den samme visualisering. Fremhævning er en sjov og hurtig måde at udforske dataeffekter på. Du kan finde flere eksempler i [afsnittet kryds filtrering og tværgående fremhævning](../consumer/end-user-interactions.md#cross-filtering-and-cross-highlighting) af "hvordan visuelle elementer kryds filtrerer hinanden i en Power BI rapport".

![Animation, der viser kryds filtrering og tværgående fremhævning.](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)

Rapport editorer kan ændre den måde, visualiseringer interagerer på. Hvis du vil finjustere, hvordan tværgående fremhævning fungerer, skal du se [Rediger, hvordan visualiseringer interagerer i rapport](service-reports-visual-interactions.md).

## <a name="next-steps"></a>Næste trin

[Den nye filtreringsoplevelse i Power BI-rapporter](power-bi-report-filter.md)

[Føj et filter til en rapport (i redigeringsvisning)](power-bi-report-add-filter.md)

[Få en præsentation af rapportfiltre](../consumer/end-user-report-filter.md)

[Hvordan visuelle elementer i rapporter kryds filtrerer og kryds fremhævning af hinanden i en rapport](../consumer/end-user-interactions.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
