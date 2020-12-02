---
title: Begrænsninger for Spørgsmål og svar i Power BI
description: Aktuelle begrænsninger for Spørgsmål og svar i Power BI
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 09/09/2020
ms.openlocfilehash: 6ad81bc88ee559fa08400b5ed8a74dd1a9b6051f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410016"
---
# <a name="limitations-of-power-bi-qa"></a>Begrænsninger for Spørgsmål og svar i Power BI

Der er i øjeblikket nogle begrænsninger for Spørgsmål og svar i Power BI.

## <a name="data-sources"></a>Datakilder

### <a name="supported-data-sources"></a>Understøttede datakilder

Spørgsmål og svar i Power BI understøtter følgende konfigurationer af datakilder i Power BI-tjenesten:

- Importtilstand
- Liveforbindelse til Azure Analysis Services
- Liveforbindelse til SQL Server Analysis Services (med en gateway)
- Power BI-datasæt.

Sikkerhed på rækkeniveau understøttes i hver af disse konfigurationer.

**DirectQuery-understøttelse for Spørgsmål og svar** (prøveversion)

Spørgsmål og svar understøtter nu SQL DirectQuery-kilder, herunder SQL Server 2019, Azure SQL Database og Azure Synapse Analytics. Du kan bruge Spørgsmål og svar til at stille spørgsmål på et naturligt sprog mod disse datakilder. Der er én lille ændring af funktionsmåden for Spørgsmål og svar i DirectQuery-tilstand: Når du har skrevet dit spørgsmål, skal du vælge knappen **Send**. Denne ændring forhindrer overbelastning af DirectQuery-kilden med unødvendige forespørgsler, mens du skriver.

Andre DirectQuery-kilder understøttes ikke for Spørgsmål og svar. Vi blokerer ikke Spørgsmål og svar fuldstændig, hvis du har andre DirectQuery-kilder i dit datasæt, men nogle spørgsmål besvares muligvis ikke korrekt eller returnerer fejl.

### <a name="data-sources-not-supported"></a>Ikke-understøttede datakilder

Spørgsmål og svar i Power BI understøtter i øjeblikket ikke følgende konfigurationer:

- Sikkerhed på objektniveau med alle typer datakilder
- Sammensatte modeller
- Reporting Services 

## <a name="tooling-limitations"></a>Begrænsninger for værktøjer

Den nye dialogboks for værktøjer giver brugerne mulighed for at tilpasse og forbedre det naturlige sprog i Spørgsmål og svar. Hvis du vil vide mere om værktøjer, kan du læse [Introduktion til værktøjer til Spørgsmål og svar](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Begrænsninger for repetitionsspørgsmål

Spørgsmål, du har stillet til din datamodel, gemmes kun i 28 dage i repetitionsspørgsmålene. Når du bruger den nye egenskab for repetitionsspørgsmål, vil du måske opleve, at nogle spørgsmål ikke er registreret. De registreres ikke som standard, da programmet for naturligt sprog udfører en række trin til rensning af data for at sikre, at alle tastetryk fra en bruger ikke registreres eller vises.

Power BI-administratorer kan bruge indstillingerne for lejer til at administrere muligheden for at gemme spørgsmål. Tilladelserne er baseret på sikkerhedsgrupper. 

Brugerne kan også forhindre, at deres spørgsmål bliver registreret ved at vælge **Indstillinger** > **Generelt** og fjerne markeringen i **Giv Spørgsmål og svar tilladelse til at registrere min ytring**. 

## <a name="teach-qa-limitations"></a>Begrænsninger i Træn Spørgsmål og svar

Med Træn Spørgsmål og svar kan du rette to typer fejl:

- Tildel et ord til et felt.
- Tildel en filterbetingelse til et ord.

I øjeblikket understøtter vi ikke omdefinering af et genkendt begreb eller definering af andre typer betingelser eller sætninger. Når du definerer filtreringsbetingelser, kan du desuden kun bruge en begrænset delmængde af sprog, herunder:

- Land, som er USA
- Land, som ikke er USA
- Produkter > 100
- Produkter større end 100
- Produkter = 100
- Produkter er lig med 100
- Produkter < 100
- Produkter er mindre end 100

> [!NOTE]
> Værktøjer til Spørgsmål og svar understøtter kun importtilstand. De understøtter endnu ikke, at der oprettes forbindelse til en datakilde i det lokale miljø eller en Azure Analysis Services-datakilde. Denne aktuelle begrænsning vil blive fjernet i efterfølgende udgaver af Power BI.

### <a name="statements-not-supported"></a>Sætninger understøttes ikke

- Flere betingelser understøttes ikke. Du kan løse problemet ved at oprette en DAX-beregnet kolonne, der evaluerer en boolesk sætning med flere betingelser og bruge dette felt i stedet.
- Hvis du ikke angiver en filterbetingelse, når Spørgsmål og svar beder om en delmængde af data, kan du ikke gemme definitionen, selvom der ikke er nogen rød understregning under hele sætningen.

## <a name="next-steps"></a>Næste trin

Der er en række bedste praksisser for forbedring af programmet til naturligt sprog. Du kan finde flere oplysninger under [Bedste praksis for Spørgsmål og svar](q-and-a-best-practices.md).
