---
title: Forhåndsvisning af rapporter i Power BI Report Builder
description: Mens du opretter en sideinddelt rapport i Report Builder, er det nyttigt at få forhåndsvist rapporten ofte for at bekræfte, at rapporten viser det, du ønsker.
author: maggiesMSFT
ms.author: maggies
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
ms.openlocfilehash: d982174d814b3f1042e02dc9beda762848c48086
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416203"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Forhåndsvisning af rapporter i Power BI Report Builder

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Mens du opretter en sideinddelt rapport i Report Builder, er det nyttigt at få forhåndsvist rapporten ofte for at bekræfte, at rapporten viser det, du ønsker. Klik på **Kør** for at få forhåndsvist din rapport. Rapporten gengives i forhåndsvisningstilstand.  
  
 Report Builder forbedrer oplevelsen med forhåndsvisningen ved hjælp af redigeringssessioner, når der er oprettet forbindelse til en rapportserver. Redigeringssessionen opretter en datacache og gør datasættene i cachen tilgængelige for gentagne forhåndsvisninger af rapporten. En redigeringssession er ikke en funktion, du interagerer direkte med, men hvis du forstår, hvornår et datasæt opdateres, vil det hjælpe dig med at forbedre ydeevnen, når du får forhåndsvist en rapport, og forstå, hvorfor rapporten gengives hurtigere eller langsommere.  

  
> [!NOTE]  
> Der er nogle forskelle mellem en forhåndsvisning i Report Builder og visning i en browser. Et kontrolelement i en kalender, som føjes til en rapport, når du angiver en parameter af typen Dato/klokkeslæt, er f.eks. forskellig i Report Builder og i en browser. 
  
## <a name="improving-preview-performance"></a>Forbedring af ydeevnen af forhåndsvisning  
 Den måde, du opretter og opdaterer rapporter på, påvirker den måde rapporter gengives på i en forhåndsvisning. Første gang, du får forhåndsvist en rapport, der er afhængig af en serverreference, oprettes der en redigeringssession for dig, og de data, der bruges, når rapporten køres, føjes til en datacache, som gemmes. Når du foretager ændringer af rapporten, der ikke påvirker dataene, bruges den cachelagrede kopi af dataene af rapporten. Det betyder, at du ikke kan se dataændringer, hver gang du får forhåndsvist rapporten. Hvis du vil se nye data, skal du klikke på knappen **Opdater** på båndet.  
  
 Følgende handlinger opdaterer cachen og sinker gengivelse af rapporten, næste gang du får forhåndsvist rapporten:  
  
-   Tilføj, skift eller slet et datasæt. Det cachelagrede datasæt indeholder alle de datasæt, som en rapport bruger, og ændringer af et hvilket som helst datasæt gør det cachelagrede datasæt ugyldigt. Dette omfatter ændring af navn, forespørgsel eller felter i datasættet.  
  
    > [!NOTE]  
    >  Hvis datasættet indholder et stort antal felter, som du ikke forventer at bruge, bør du overveje at opdatere datasættet for at udelade disse felter. Selvom dette opretter en ny redigeringssession, og den første forhåndsvisning af rapporten er langsommere, er det mindre cachelagrede datasæt overordnet en fordel for ydeevnen af rapportserveren.  
  
-   Tilføj, skift eller slet en datakilde. Dette omfatter ændring af navnet eller egenskaberne for datakilden, dataudvidelsen for datakilden eller egenskaberne for forbindelsen til datakilden.  
  
-   Skift den datakilde, der rapporterer brug, til en anden datakilde.  
  
-   Skift sproget i rapporten.  
  
-   Skift assemblies eller brugerdefineret kode, som rapporten bruger.  
  
-   Tilføj, skift eller slet forespørgselsparametrene i rapporten eller parameterværdierne.  
  
 Ændringer af rapportlayoutet og dataformateringen påvirker ikke det cachelagrede datasæt. Du kan udføre følgende handlinger uden at opdatere det cachelagrede datasæt:  
  
-   Tilføj eller fjern dataområder, f.eks. tabeller, matrixer eller diagrammer.  
  
-   Tilføj eller slet kolonner fra rapporten. Alle felterne i datasættet er tilgængelige til brug i rapporten. Tilføjelse eller fjernelse af felter i rapporten påvirker ikke datasættet.  
  
-   Skift rækkefølgen af felter i tabeller og matrixer.  
  
-   Tilføj, skift eller slet række- og kolonnegrupper.  
  
-   Tilføj, skift eller slet formatering af dataværdier i felterne.  
  
-   Tilføj, skift eller slet billeder, linjer eller tekstfelter.  
  
-   Skift sideskift.  
  
Redigeringssessionen oprettes, første gang du får forhåndsvist en rapport. En redigeringssession varer som standard 7200 sekunder (2 timer). Sessionen nulstilles til to timer, hver gang du kører rapporten. Når redigeringssessionen udløber, slettes datacachen. Hvis redigeringssessionen udløber, oprettes der automatisk en igen, næste gang du får forhåndsvist rapporten.
  
Datacachen kan som standard indeholde op til fem datasæt. Hvis du bruger mange forskellige kombinationer af parameterværdier, har rapporten muligvis brug for flere data. Dette kræver, at cachen opdateres, så gengiver rapporten elementer langsommere, næste gang du få den forhåndsvist. 
  
## <a name="concurrency-of-report-updates"></a>Samtidighed af rapportopdateringer  
Du får ofte forhåndsvist en rapport som en del af en opdatering og derefter lagring af en rapport i Power BI-tjenesten. Når du opdaterer en rapport, er det muligt, at en anden også opdaterer den og derefter gemmer rapporten på samme tid. Den rapport, der gemmes sidst, er den version af rapporten, der er tilgængelige til fremtidige visning og opdatering. Det betyder, at den version af rapporten, som du fik forhåndsvist, muligvis ikke er den version, du åbner igen. Du har mulighed for at gemme rapporten med et nyt navn ved hjælp af indstillingen **Gem som** i menuen i Report Builder.  
  
## <a name="external-report-items"></a>Eksterne rapportelementer  
 Rapporten kan indeholde elementer såsom eksterne billeder, der gemmes separat fra rapporten. Da elementerne gemmes separat, kan de muligvis blive flyttet til en anden placering eller blive slettet. Hvis det sker, kan din rapport muligvis ikke blive forhåndsvist. Du kan opdatere rapporten for at angive den opdaterede placering af elementet, eller hvis elementet blev slettet, kan du erstatte den med et eksisterende element eller fjerne referencen til elementet fra rapporten.  
  
## <a name="next-steps"></a>Næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
