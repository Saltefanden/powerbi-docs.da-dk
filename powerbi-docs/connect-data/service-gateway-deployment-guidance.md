---
title: Vejledning i at installere en datagateway til Power BI
description: Få de bedste praksisser og overvejelser ved installation af en gateway til Power BI.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: a3921590787895d20ff03781de2efa93c08f71d0
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410315"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Vejledning i at installere en datagateway til Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Denne artikel indeholder en vejledning til og nogle overvejelser om udrulning af en datagateway til Power BI i dit netværksmiljø.

Du kan finde oplysninger om, hvordan du downloader, installerer, konfigurerer og administrerer datagateway'en i det lokale miljø, i [Hvad er en datagateway i det lokale miljø?](/data-integration/gateway/service-gateway-onprem). Du kan også få mere at vide om datagatewayen i det lokale miljø og Power BI ved at besøge [Microsoft Power-bloggen](https://powerbi.microsoft.com/blog/) og [Microsoft Power BI-community'et](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Overvejelser ved installationen af datagatewayen i det lokale miljø

Før du installerer datagateway'en i det lokale miljø for din Power BI-cloudtjeneste, er der nogle ting, du skal være opmærksom på. I de følgende afsnit beskrives disse overvejelser.

### <a name="number-of-users"></a>Antal brugere

Antallet af brugere, som forbruger en rapport, der bruger gateway'en, er en vigtig metrikværdi i forbindelse med beslutningen om, hvor gateway'en skal installeres. Her er nogle spørgsmål, som bør tages med i overvejelserne:

* Bruges disse rapporter på forskellige tidspunkter på dagen af brugerne?
* Hvilke typer forbindelser bruger de (DirectQuery eller Import)?
* Bruger alle brugerne den samme rapport?

Hvis alle brugere har adgang til en given rapport på samme tidspunkt hver dag, skal du sørge for at installere gateway'en på en computer, der er i stand til at håndtere alle disse anmodninger. Se de følgende afsnit for ydelsestællere og minimumkrav, der kan hjælpe dig med at finde ud af, om en maskine er tilstrækkelig.

En begrænsning i Power BI tillader kun *én* gateway pr. *rapport*. Selvom en rapport er baseret på flere datakilder, skal alle disse datakilder gennem en enkelt gateway. Hvis et dashboard er baseret på *flere* rapporter, kan du bruge en dedikeret gateway til hver bidragende rapport. På den måde kan du fordele gateway'ens belastningen blandt de mange rapporter, der bidrager til det enkelte dashboard.

### <a name="connection-type"></a>Forbindelsestype

Power BI giver mulighed for to typer forbindelser: DirectQuery og Import. Ikke alle datakilder understøtter begge forbindelsestyper. Mange faktorer kan bidrage til, at du vælger én frem for en anden, f.eks. sikkerhedskrav, ydeevne, datagrænser og datamodelstørrelser. Hvis du vil vide mere om forbindelsestyper og understøttede datakilder, skal du se [listen over tilgængelige datakildetyper](service-gateway-data-sources.md#list-of-available-data-source-types).

Brugen af gatewayen kan variere, afhængigt af den anvendte forbindelsestype. Du kan f.eks. prøve at adskille DirectQuery-datakilder fra datakilder med planlagt opdatering, når det er muligt. Forudsætningen er, at de findes i forskellige rapporter og kan adskilles. Adskillelse af kilder forhindrer, at gatewayen ophobes med tusindvis af DirectQuery-anmodninger samtidigt med morgenens planlagte opdatering af en stor datamodelstørrelse, der bruges til virksomhedens primære dashboard. 

Følgende overvejelser bør tages i hver situation:

* **Planlagt opdatering**: Afhængigt af din forespørgselstørrelse og antallet af foretagne opdateringer pr. dag kan du vælge at forblive mellem de anbefalede mindstekrav til hardware eller opgradere til en computer med større ydeevne. Hvis en given forespørgsel ikke er mislykkedes, sker transformationerne på gatewaycomputeren. Derfor har gateway-maskinen fordel af mere disponibel RAM.

* **DirectQuery**: En forespørgsel sendes hver gang, en given bruger åbner rapporten eller gransker data. Hvis du forventer, at flere end 1000 brugere tilgår data samtidigt, så skal du sørge for, at din computer har robuste og kapacitetstunge hardwarekomponenter. Flere CPU-kerner resulterer i et forbedret gennemløb for en DirectQuery-forbindelse.

Du kan se kravene til installation af computeren i [installationskravene](/data-integration/gateway/service-gateway-install#requirements) til datagateways i det lokale miljø.

### <a name="location"></a>Placering

Placeringen af gatewayinstallationen kan have stor indflydelse på ydeevnen i forbindelse med din forespørgsel. Sørg for, at din gateway, datakildernes placeringer og Power BI-lejeren er så tæt som muligt på hinanden for at minimere netværksventetiden. For at fastsætte din Power BI-lejerplacering i Power BI-tjenesten, skal du vælge **?** - -ikonet i øverste højre hjørne. Vælg derefter **Om Power BI**.

![Bestem placering af Power BI-lejer](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Hvis du planlægger at bruge Power BI-gatewayen med Azure Analysis Services, skal du sørge for, at dataområderne i begge matcher. Se [denne video](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/) for at få flere oplysninger om, hvordan du angiver dataområder for flere tjenester.

## <a name="next-steps"></a>Næste trin

* [Konfiguration af proxyindstillinger](/data-integration/gateway/service-gateway-proxy)  
* [Foretag fejlfinding af gateways – Power BI](service-gateway-onprem-tshoot.md)  
* [Ofte stillede spørgsmål om datagatewayen i det lokale miljø – Power BI](service-gateway-power-bi-faq.md)  

Har du flere spørgsmål? Prøv at spørge [Power BI-community'et](https://community.powerbi.com/).
