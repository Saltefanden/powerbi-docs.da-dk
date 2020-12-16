---
title: Brug DirectQuery i Power BI Desktop
description: Brug DirectQuery, der også kaldes en dynamisk forbindelse, i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/14/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: a3ab606733e47dec06837cfc1840da09732f7019
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491224"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Brug DirectQuery i Power BI Desktop
Når du opretter forbindelse til din datakilde i *Power BI Desktop*, er det altid muligt at importere en kopi af dataene til Power BI Desktop. For nogle datakilder findes der en anden mulighed: Du kan oprette direkte forbindelse til datakilden med DirectQuery.

## <a name="supported-data-sources"></a>Understøttede datakilder
Hvis du vil se en komplet liste over de datakilder, der understøtter DirectQuery, skal du se [Datakilder, der understøttes af DirectQuery](power-bi-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Sådan opretter du forbindelse ved hjælp af DirectQuery
Når du bruger **Hent data** til at oprette forbindelse til en datakilde, der understøttes af DirectQuery, kan du i dialogboksen forbindelse vælge, hvordan du vil oprette forbindelse. I Power BI Desktop kan du f.eks. under båndet **Hjem** vælge **Hent data** > **SQL Server**. I dialogboksen **SQL Server Database** viser **tilstanden Dataforbindelse** indstillinger for **Import** og **DirectQuery**:

![Indstillinger for Import og DirectQuery, dialogboksen SQL Server Database, Power BI Desktop](media/desktop-use-directquery/directquery_sqlserverdb.png)

Her er forskellene mellem at vælge **Import** og **DirectQuery**:

- **Import**: De valgte tabeller og kolonner importeres i Power BI Desktop. Når du opretter eller interagerer med en visualisering, bruger Power BI Desktop de importerede data. For at se de underliggende dataændringer siden den oprindelige import eller den seneste opdatering skal du opdatere dataene, hvilket vil importere hele datasættet igen.

- **DirectQuery**: Der bliver ikke importeret eller kopieret data til Power BI Desktop. For relationelle datakilder vises de valgte tabeller og kolonner på listen **Felter**. For flerdimensionelle datakilder som SAP Business Warehouse vises dimensioner og målinger for den valgte kube på listen **Felter**. Når du opretter eller interagerer med en visualisering, sender Power BI Desktop en forespørgsel til den underliggende datakilde, så du altid får vist aktuelle data.

Du kan vælge mange dataudformninger og datatransformationer, når du bruger DirectQuery – dog med nogle begrænsninger. Når du opretter eller interagerer med en visualisering, skal du sende en forespørgsel til den underliggende kilde. Den tid, der er nødvendig for at opdatere visualiseringen, afhænger af den underliggende datakildes ydeevne. Hvis der for nylig er sendt en anmodning, vil Power BI Desktop bruge de seneste data til at reducere den tid, der kræves for at vise visualiseringen. Hvis du vælger **Opdater** under båndet **Hjem**, bliver alle visualiseringerne opdateret med de aktuelle data.

I artiklen [Power BI og DirectQuery](desktop-directquery-about.md) kan du læse mere om DirectQuery. Se følgende afsnit for at få flere oplysninger om de fordele, begrænsninger og vigtige overvejelser, du skal være opmærksom på, når du bruger DirectQuery.

## <a name="benefits-of-using-directquery"></a>Fordele ved at bruge DirectQuery
Der er nogle få fordele ved at bruge DirectQuery:

- Med DirectQuery kan du bygge visualiseringer over meget store datasæt, hvor det ellers ikke vil være muligt først at importere alle dataene.
- Underliggende dataændringer kan kræve en opdatering af data. For nogle rapporter kan det kræve store dataoverførsler at vise aktuelle data, hvilket vil gøre det uhensigtsmæssigt at importere dataene igen. I modsætning til det vil de rapporter, der bruger DirectQuery, altid vise aktuelle data.
- Grænsen for datasæt på 1 GB gælder *ikke* for DirectQuery.

## <a name="limitations-of-directquery"></a>Begrænsninger i DirectQuery
Der er i øjeblikket nogle få begrænsninger ved at bruge DirectQuery:

- Hvis forespørgslen i **Forespørgselseditor** er for kompliceret, vil der opstå en fejl. Når du skal løse fejlen, skal du enten slette det fejlbehæftede trin i **Forespørgselseditor**, eller du skal i stedet *importere* dataene i stedet for at bruge DirectQuery. For flerdimensionelle datakilder som SAP Business Warehouse er der ingen **Forespørgselseditor**.

- Funktionerne for tidsintelligens findes ikke i DirectQuery. Eksempelvis understøttes særlig behandling af datokolonner (som f.eks. år, kvartal, måned eller dag) ikke i DirectQuery-tilstand.

- Power BI-tjenesten understøtter ikke beregnede tabeller eller beregnede kolonner, som refererer til en DirectQuery-tabel fra en datakilde med SSO-godkendelse (enkeltlogon).

- Der er pålagt begrænsninger på de DAX-udtryk, der er tilladt i målinger, for at sikre, at de forespørgsler, der sendes til den underliggende datakilde, har en acceptabel ydeevne.

- Der er en begrænsning på 1.000.000 rækker for cloudkilder, hvor datakilder i det lokale miljø er begrænset til en defineret nyttelast på ca. 4 MB pr. række (afhængigt af en privat komprimeringsalgoritme) eller en datastørrelse på 16 MB for hele visualiseringen. Nogle af grænserne kan blive hævet, når der anvendes en Premium-kapacitet. Denne grænse påvirker ikke de sammenlægninger eller beregninger, der bruges til at oprette det datasæt, der returneres ved hjælp af DirectQuery. Det påvirker kun de returnerede rækker. Premium-kapaciteter kan angive maksimale grænser for rækker, som beskrevet i [dette indlæg](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/). 

    Du kan f.eks. samle 10 mio. rækker med din forespørgsel, der kører på datakilden. Forespørgslen returnerer præcist resultaterne af denne sammenlægning til Power BI ved hjælp af DirectQuery, hvis de returnerede Power BI-data er mindre end 1 mio. rækker. Hvis der returneres mere end 1 millioner rækker fra DirectQuery, returnerer Power BI en fejl (medmindre det er en Premium-kapacitet, og rækkeantallet er under den grænse, som administratoren har angivet).


## <a name="important-considerations-when-using-directquery"></a>Vigtige overvejelser i forbindelse med brugen af DirectQuery
Der skal tages højde for følgende tre punkter, når der bruges DirectQuery:

- **Ydeevne og belastning**: Alle DirectQuery-anmodninger sendes til kildedatabasen, så den tid, der kræves for at opdatere en visualisering, er afhængig af, hvor lang tid der går, inden back end-kilden svarer med resultater fra forespørgslen (eller forespørgslerne). Fem sekunder eller mindre er den anbefalede svartid (inklusive returnering af de data, der er anmodet om) ved brug af DirectQuery til visualiseringer. Den maksimalt anbefalede tid er 30 sekunder. Hvis svartiden bliver længere, bliver brugeroplevelsen i rapporten uacceptabel. Efter en rapport er publiceret til Power BI-tjenesten, vil de forespørgsler, der tager mere end nogle få minutter, få timeout, og brugeren får vist en fejl.
  
    Der skal også tages højde for belastningen af kildedatabasen baseret på, hvor mange Power BI-brugere der skal bruge den publicerede rapport. Hvis du bruger **Sikkerhed på rækkeniveau** (RLS), kan det også have stor betydning. Et dashboardfelt, som ikke er RLS, og som deles af flere brugere, resulterer i en enkelt forespørgsel til databasen. Brug af RLS på et dashboardfelt betyder dog som regel, at opdateringen af et felt kræver én forespørgsel *pr. bruger*, hvilket kan øge belastningen på kildedatabasen betydeligt og evt. påvirke ydeevnen.
  
    Power BI opretter forespørgsler, der er så effektive som muligt. I visse situationer vil den genererede forespørgsel muligvis ikke være tilstrækkeligt effektiv til at undgå, at en opdatering medfører fejl. Et eksempel på denne situation er, når den genererede forespørgsel henter et stort antal rækker fra back end-datakilden. I dette tilfælde opstår følgende fejl:

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    Denne situation kan opstå med et simpelt diagram, der indeholder en kolonne med høj kardinalitet, hvor indstillingen for aggregering er angivet til **Opsummer ikke**. Visualiseringen skal kun have kolonner med en kardinalitet under 1 million, eller den skal anvende de relevante filtre.

- **Sikkerhed**: Alle de brugere, der anvender en publiceret rapport, opretter som standard forbindelse til back end-datakilden ved hjælp af de legitimationsoplysninger, der angives efter publiceringen til Power BI-tjenesten. Denne procedure er den samme for de data, der er importeret: Alle brugere ser de samme data, uanset hvilke sikkerhedsregler der er defineret i back end-kilden.

    Kunder, der ønsker sikkerhed pr. bruger, som implementeres med DirectQuery-kilder, skal enten bruge RLS eller konfigurere Kerberos-begrænset godkendelse i forhold til kilden. Kerberos er ikke tilgængelig for alle kilder. [Få mere at vide om RLS](../admin/service-admin-rls.md). [Få mere at vide om Kerberos i DirectQuery](service-gateway-sso-kerberos.md).

- **Understøttede funktioner**: Nogle funktioner i Power BI Desktop er ikke understøttet i DirectQuery-tilstand, eller de har begrænsninger. Nogle funktioner i Power BI-tjenesten (som f.eks. *Hurtig indsigt*) er ikke tilgængelige til datasæt ved brug af DirectQuery. Når du bestemmer, om du vil bruge DirectQuery, skal du overveje disse funktionsbegrænsninger.

> [!NOTE]
> Når du bruger DirectQuery med en Azure SQL-database og en privat IP-adresse, kræves der en gateway i det lokale miljø. 

## <a name="publish-to-the-power-bi-service"></a>Publicer til Power BI-tjenesten
De rapporter, der oprettes ved hjælp af DirectQuery, kan publiceres til Power BI-tjenesten.

Hvis den anvendte datakilde ikke behøver **datagatewayen i det lokale miljø** (**Azure SQL Database**, **Azure SQL Data Warehouse** eller **Redshift**), skal du angive legitimationsoplysninger, før Power BI-tjenesten viser den publicerede rapport. Følg disse instruktioner for at angive legitimationsoplysningerne:

1. Log på [Power BI](https://www.powerbi.com/).
2. I Power BI-tjenesten skal du vælge tandhjulsikonet for **Indstillinger** og vælge menupunktet **Indstillinger**.

    ![Indstillinger, Power BI-tjeneste](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. På siden **Indstillinger** i Power BI-tjenesten skal du vælge fanen **Datasæt**, vælge det datasæt, der bruger DirectQuery, og vælge **Rediger legitimationsoplysninger**.

4. Tilføj legitimationsoplysningerne. Ellers opstår der en fejl, når du åbner en publiceret rapport eller udforsker et datasæt, der er oprettet via en DirectQuery-forbindelse.

Hvis du vil foretage en dataforbindelse til andre datakilder end **Azure SQL Database**, **Azure SQL Data Warehouse** og **Redshift** eller **Snowflake Data Warehouse**, der bruger DirectQuery, skal du installere en **datagateway i det lokale miljø** og registrere datakilden. Du kan finde flere oplysninger i [Hvad er en datagateway i det lokale miljø?](service-gateway-onprem.md)

## <a name="next-steps"></a>Næste trin
Du kan finde flere oplysninger om DirectQuery i følgende ressourcer:

- [Brug af DirectQuery in Power BI](desktop-directquery-about.md)
- [Datakilder, der understøttes af DirectQuery](power-bi-data-sources.md)
- [DirectQuery og SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery og SAP HANA](desktop-directquery-sap-hana.md)
- [Hvad er en datagateway i det lokale miljø?](service-gateway-onprem.md)
