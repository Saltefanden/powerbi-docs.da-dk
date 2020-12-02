---
title: Cachelagring af forespørgsler i Power BI Premium
description: Cachelagring af forespørgsler i Power BI Premium
author: KesemSharabi
ms.author: kesharab
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 10/04/2019
LocalizationGroup: ''
ms.openlocfilehash: 8495ccd75fec49079e87312bbf5a7693b78b3e6b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404128"
---
# <a name="query-caching-in-power-bi-premiumembedded"></a>Cachelagring af forespørgsler i Power BI Premium/Embedded

Organisationer med Power BI Premium eller Power BI Embedded kan drage fordel af *cachelagring af forespørgsler* for at fremskynde rapporter, der er knyttet til et datasæt. Ved cachelagring af forespørgsler instrueres Premium-/Embedded-kapaciteten til at bruge dens lokale cachelagringstjeneste til at bevare forespørgselsresultaterne, derved undgår man, at den underliggende datakilde skal beregne disse resultater.

> [!IMPORTANT]
> Cachelagring af forespørgsler er kun tilgængelig til Power BI Premium og Power BI Embedded. Det gælder ikke for LiveConnect-datasæt, der gør brug af Azure Analysis Services eller SQL Server Analysis Services.

Cachelagrede forespørgselsresultater er specifikke for brugeren og datasættets kontekst, og sikkerhedsreglerne overholdes altid. På nuværende tidspunkt udfører tjenesten kun cachelagring af forespørgsler for den første side, du lander på. Med andre ord, så cachelagres forespørgsler ikke, når du interagerer med rapporten. Forespørgselscachen respekterer [personlige bogmærker](../consumer/end-user-bookmarks.md#personal-bookmarks) og [faste filtre](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/), så forespørgsler, der genereres af en personligt tilpasset rapport, cachelagres. [Dashboardfelter](../create-reports/service-dashboard-tiles.md), der leveres af de samme forespørgsler, får samme fordel, når forespørgslen cachelagres. Det er særligt en fordel for ydeevnen, når et datasæt tilgås ofte og ikke skal opdateres så ofte. Cachelagring af forespørgsler kan også reducere belastningen på Premium-/Embedded-kapaciteten ved at reducere det samlede antal forespørgsler.

Du styrer funktionsmåden af cachelagring af forespørgsler på siden **Indstillinger** for datasættet i Power BI-tjenesten. Der er tre mulige indstillinger:

- **Standardkapacitet**: Cachelagring af forespørgsel er slået Fra
- **Fra**: Cachelagring af forespørgsler bruges ikke for dette datasæt.
- **Til**: Cachelagring af forespørgsler bruges for dette datasæt.

    ![Dialogboks for cachelagring af forespørgsler](media/power-bi-query-caching/power-bi-query-3-options.png)

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

- Når du ændrer indstillingerne for cachelagring fra **Til** til **Fra**, fjernes alle tidligere gemte forespørgselsresultater for datasættet fra kapacitetscachen. Du kan enten slå cachelagring fra eksplicit eller ved at gå tilbage til indstillingen Standardkapacitet, som en administrator har angivet til **Fra**. Når indstillingen slås fra, kan det medføre en lille forsinkelse, næste gang en rapport kører forespørgsler i forhold til dette datasæt. Forsinkelsen skyldes, at disse rapportforespørgsler kører efter behov, og at der ikke gøres brug af gemte resultater. Det krævede datasæt skal muligvis også indlæses i hukommelsen, før det kan håndtere forespørgsler.
- Når forespørgselscachen opdateres, skal Power BI køre forespørgsler mod de underliggende datamodeller for at få de nyeste resultater. Hvis et stort antal datasæt har aktiveret cachelagring af forespørgsler, og der er kraftig belastning på Premium-/Embedded-kapaciteten, kan der opstå en forringelse af ydeevnen under opdatering af cachen. Forringelsen skyldes den øgede mængde forespørgsler, der udføres.

## <a name="next-steps"></a>Næste trin

* [Hvad er Power BI Premium?](../admin/service-premium-what-is.md)
* [Hvad er Power BI Embedded i Azure?](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)
