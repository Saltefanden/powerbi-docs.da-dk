---
title: Brug naturligt sprog til import, Live Connect og DirectQuery
description: I denne artikel ser vi nærmere på, hvordan funktionen til Spørgsmål og svar fungerer med de forskellige typer datakilder, der er tilgængelige i Power BI. Vi ser også nærmere på koncepterne for indeksering og cachelagring.
author: mohaali
ms.author: mohaali
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: 23ecc8edd82f6c1694c850f73fef2a892230ff14
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418963"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>Brug naturligt sprog til import, Live Connect og DirectQuery

Funktionen til Spørgsmål og svar i Power BI giver dig mulighed for at få svar fra dine data hurtigt ved at bruge naturligt sprog til at stille spørgsmål om dataene. Denne artikel indeholder en beskrivelse af, hvordan indeksering og cachelagring bruges til at forbedre ydeevnen af hver understøttede konfiguration.

## <a name="what-data-sources-are-supported-in-qa"></a>Hvilke datakilder understøttes i Spørgsmål og svar?

Spørgsmål og svar understøttes i følgende konfigurationer:

- Importtilstand
- Live Connect-tilstand – Brug af SQL Server Analysis Services, Azure Analysis Services eller Power BI-datasæt i det lokale miljø
- DirectQuery – Azure Synapse, Azure SQL og SQL Server 2019. Selvom andre kilder kan fungere i DirectQuery-tilstanden, understøtter vi ikke disse kilder officielt.

Spørgsmål og svar er som standard aktiveret i en rapport, hvis du bruger visualiseringen for Spørgsmål og svar. Der vises en meddelelse, hvis du bruger DirectQuery eller Live Connect. Du kan slå funktionaliteten til naturligt sprog til/fra eksplicit for en rapport ved at gå til indstillinger.

![Indstillinger for Spørgsmål og svar på skrivebordet](media/qna-desktop-options.png)

Du kan finde flere oplysninger under [Begrænsninger for Spørgsmål og svar i Power BI](q-and-a-limitations.md).

## <a name="how-does-indexing-work-with-qa"></a>Hvordan fungerer indeksering med Spørgsmål og svar?

Når du aktiverer Spørgsmål og svar, oprettes der et indeks, så der hurtigt kan leveres feedback i realtid til brugeren og for at hjælpe med at fortolke brugerens spørgsmål. Det kan tage noget tid at oprette indekset, og der er følgende elementer og begrænsninger.

- Alle kolonnenavne og -tabeller indsættes i indekset, medmindre det er blevet slået fra eksplicit i værktøjet til Spørgsmål og svar.
- Alle tekstværdier med mindre end 100 tegn indekseres. Tekstværdier med mere end 100 tegn indekseres ikke. 
- Der gemmes maksimalt 5 millioner entydige værdier i indekset i Spørgsmål og svar. Hvis du overskrider denne grænse, indeholder indekset ikke alle potentielle værdier, hvilket kan reducere nøjagtigheden af de resultater, du modtager fra Spørgsmål og svar.
- Hvis der opstår fejl under indekseringen, forbliver indekset i en delvis tilstand og genoprettes ved den næste opdatering, som beskrevet i næste afsnit.

## <a name="how-often-is-the-index-refreshed-and-cached"></a>Hvor ofte opdateres og cachelagres indekset?

I Power BI Desktop oprettes indekset på det tidspunkt, du bruger Spørgsmål og svar. Der vises et lille ikon, som giver dig besked om, at indekset oprettes. I denne periode kan det tage lidt tid at indlæse visualiseringen for Spørgsmål og svar, herunder forslag.

I Power BI-tjenesten genoprettes indekset ved publicering/genpublicering og opdatering. Indekset i Spørgsmål og svar oprettes ikke altid automatisk og er nogle gange baseret på behov for at optimere opdateringerne af datasættet. I forbindelse med DirectQuery indekseres dataene højst én gang om dagen for at reducere indvirkningen på kilden til DirectQuery.

## <a name="next-steps"></a>Næste trin

Du kan integrere et naturligt sprog i dine rapporter på flere forskellige måder. Du kan finde flere oplysninger i disse artikler:

* [Visualisering for Spørgsmål og svar](../visuals/power-bi-visualization-q-and-a.md)
* [Bedste praksis for Spørgsmål og svar](q-and-a-best-practices.md)
