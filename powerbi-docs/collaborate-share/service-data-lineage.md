---
title: Dataafstamning
description: I moderne BI-projekter (Business Intelligence) er det en vigtig udfordring for mange kunder at forstå flowet af data fra datakilden til destinationen.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
LocalizationGroup: ''
ms.openlocfilehash: 8b119f5134fdaf4e251f9a8da560a2a3f7f3a4eb
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2020
ms.locfileid: "97492098"
---
# <a name="data-lineage"></a>Dataafstamning
I moderne BI-projekter (Business Intelligence) kan det være en udfordring for mange kunder at forstå flowet af data fra datakilden til destinationen. Udfordringen er endnu større, hvis du har oprettet avancerede analyseprojekter, der strækker sig over flere datakilder, artefakter og afhængigheder. Spørgsmål som "Hvad sker der, hvis jeg ændrer disse data?" eller "Hvorfor er denne rapport ikke ajourført?" kan være vanskelige at besvare. Det kan være nødvendigt med et team af eksperter eller en grundig undersøgelse for at forstå dem. Vi har designet en dataafstamningsvisning for at hjælpe dig med at besvare disse spørgsmål.

![Afstamningsvisning i Power BI](media/service-data-lineage/service-data-lineage-view.png)
 
Power BI har flere artefakttyper, f.eks. dashboards, rapporter, datasæt og dataflows. Mange datasæt og dataflows har forbindelse til eksterne datakilder, f.eks. SQL Server, og til eksterne datasæt i andre arbejdsområder. Når et datasæt er eksternt for et arbejdsområde, som du ejer, kan det være i et arbejdsområde, der ejes af en person i it-afdelingen eller en anden analytiker. Eksterne datakilder og datasæt gør det i sidste ende svært at vide, hvor dataene kommer fra. I forbindelse med mere eller mindre komplekse projekter introducerer vi afstamningsvisningen.

I afstamningsvisningen kan du få vist afstamningsrelationer mellem alle artefakterne i et arbejdsområde og alle dens eksterne afhængigheder. Den viser forbindelser mellem alle arbejdsområdeartefakter, herunder forbindelser til dataflows, både upstream og downstream.    

<iframe width="560" height="315" src="https://www.youtube.com/embed/rUj06dqB98g" frameborder="0" allowfullscreen></iframe>

## <a name="explore-lineage-view"></a>Udforsk afstamningsvisningen

Hvert arbejdsområde, uanset om det er nyt eller klassisk, har automatisk en afstamningsvisning. Du skal mindst have rollen som bidragyder i arbejdsområdet for at kunne få vist visningen. Se [Tilladelser](#permissions) i denne artikel for at få flere oplysninger.

* Du åbner afstamningsvisning ved at gå til listevisningen i arbejdsområdet. Tryk på pilen ud for **Listevisning**, og vælg **Afstamningsvisning**.

   ![Skift til afstamningsvisning](media/service-data-lineage/service-data-lineage-view-select.png)

I denne visning kan du se alle arbejdsområdeartefakter, og hvordan dataene flyder fra artefakt til artefakt.

**Datakilder**

Du får vist de datakilder, som datasæt og dataflows henter deres data fra. På datakildekortene får du vist flere oplysninger, der kan hjælpe med at identificere kilden. For Azure SQL Server får du f.eks. også vist navnet på databasen.

![Afstamningsvisning i en datakilde uden en gateway](media/service-data-lineage/service-data-lineage-data-source-card.png)
 
**Gateways**

Hvis en datakilde har forbindelse via en gateway i det lokale miljø, føjes gatewayoplysningerne til datakildekortet. Hvis du har tilladelser som enten gatewayadministrator eller som datakildebruger, får du vist flere oplysninger, f.eks. gatewaynavnet.

![Afstamningsvisning i en datakilde med en gateway](media/service-data-lineage/service-data-lineage-data-gateway-card.png)

**Datasæt og dataflows**
 
I datasæt og dataflow kan du se tidspunktet for den seneste opdatering, og om datasættet eller dataflowet er certificeret eller fremhævet.

![Fremhævede og certificerede datasæt i afstamningsvisning](media/service-data-lineage/service-data-lineage-promoted-certified.png)
 
Hvis en rapport i arbejdsområdet er baseret på et datasæt eller et dataflow i et andet arbejdsområde, får du vist navnet på kildearbejdsområdet på kortet for datasættet eller dataflowet. Vælg navnet på kildearbejdsområdet for at gå til det pågældende arbejdsområde.

* For en hvilken som helst artefakt skal du vælge **Flere indstillinger** (...) for at få vist menuen med indstillinger. Den indeholder alle de samme handlinger, der er tilgængelige i listevisningen.

Hvis du vil have vist flere metadata for en vilkårlig artefakt, skal du vælge selve artefaktkortet. Der vises flere oplysninger om artefakten i en siderude. På billedet nedenfor vises sideruden med metadataene for et markeret datasæt.

![Siderude med flere oplysninger](media/service-data-lineage/service-data-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Vis afstamning for alle artefakter 

Lad os sige, at du vil have vist afstamningen for en bestemt artefakt.

* Vælg dobbeltpilene under artefakten.

   ![Fremhæv afstamning for en bestemt artefakt](media/service-data-lineage/service-data-lineage-specific-artifact.png)

   Power BI fremhæver alle de artefakter, der er relateret til denne artefakt, og nedtoner resten. 

## <a name="navigation-and-full-screen"></a>Navigation og fuld skærm 

Afstamningsvisning er et interaktivt lærred. Du kan bruge musen og touchpad'en til at navigere på lærredet samt til at zoome ind eller ud.

* Hvis du vil zoome ind og ud, skal du enten bruge menuen i det nederste højre hjørne eller din mus eller touchpad.
* Hvis du vil have mere plads til selve grafen, skal du bruge indstillingen til fuld skærm i nederste højre hjørne. 

    ![Zoom ind eller ud eller fuld skærm](media/service-data-lineage/service-data-lineage-zoom.png)

## <a name="permissions"></a>Tilladelser

* Du skal have en Power BI Pro-licens for at få vist afstamningsvisningen.
* Afstamningsvisningen er kun tilgængelig for brugere med adgang til arbejdsområdet.
* Brugerne skal have rollen som administrator, medlem eller bidragyder i arbejdsområdet. Brugere med læseadgang kan ikke skifte til afstamningsvisning.


## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

- Afstamningsvisning er ikke tilgængelig i Internet Explorer. Se [Understøttede browsere til Power BI](../fundamentals/power-bi-browsers.md) for at få mere at vide.

## <a name="next-steps"></a>De næste trin

* [Introduktion til datasæt på tværs af arbejdsområder (prøveversion)](../connect-data/service-datasets-across-workspaces.md)
* [Effektanalyse af datasæt](service-dataset-impact-analysis.md)
