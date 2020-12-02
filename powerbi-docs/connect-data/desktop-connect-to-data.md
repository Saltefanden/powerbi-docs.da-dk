---
title: Opret forbindelse til data i Power BI Desktop
description: Opret forbindelse til data i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/21/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: a9fdb4e2ebd71d652c66220ad4a70473ef6dd764
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411281"
---
# <a name="connect-to-data-sources-in-power-bi-desktop"></a>Opret forbindelse til datakilderne i Power BI Desktop

I Power BI Desktop kan du nemt oprette forbindelse til en stadig større verden af data. Hvis du ikke har Power BI Desktop, kan du [downloade](https://go.microsoft.com/fwlink/?LinkID=521662) og installere det.

I Power BI Desktop findes der *alle mulige* forskellige datakilder. På følgende billede kan du se, hvordan du opretter forbindelse til data ved at vælge båndet **Hent data**  > **Andet** > **Web**.

![Hent data fra internettet](media/desktop-connect-to-data/get-data-from-the-web.png)

## <a name="example-of-connecting-to-data"></a>Eksempel på oprettelse af forbindelse til data

I dette eksempel opretter vi forbindelse til en datakilde af typen **Web**.

Forestil dig, at du går på pension. Du vil gerne bo et sted, hvor der er masser af solskin, bedre skatter og et godt sundhedsvæsen. Eller… du er måske dataanalytiker, og du ønsker, at oplysningerne skal hjælpe dine kunder, f.eks. hjælpe en kunde, der producerer regnfrakker, med at målrette salg, hvor det regner *meget*.

Uanset hvad, kan du finde en webressource, der indeholder interessante data om disse og andre emner:

[https://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx](https://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

Vælg **Hent data** > **Andet** > **Web**. I **Fra web** skal du angive adressen.

![Angiv en adresse på en webkilde](media/desktop-connect-to-data/connecttodata_3.png)

Når du vælger **OK**, begynder *forespørgsel* sfunktionen i Power BI Desktop at arbejde. Power BI Desktop kontakter webressourcen, og i **navigatorvinduet** returneres resultaterne af det, der blev fundet på den pågældende webside. I dette tilfælde blev der fundet en tabel og det generelle dokument. Vi er interesseret i tabellen, så vi vælger den på listen. I **navigatorvinduet** vises der et eksempel.

![Eksempelvisning af data i Navigator](media/desktop-connect-to-data/datasources_fromnavigatordialog.png)

På nuværende tidspunkt kan du redigere forespørgslen, før tabellen indlæses, ved at vælge **Transformer data** nederst i vinduet, eller du kan bare indlæse tabellen.

Vælg **Transformer data** for at indlæse tabellen og starte Power-forespørgselseditor. Ruden **Forespørgselsindstillinger** vises. Hvis ikke, skal du vælge **Vis** på båndet og derefter **Forespørgselsindstillinger** for at få vist ruden **Forespørgselsindstillinger**. Sådan ser det ud.

![Power Query-editor med Forespørgselsindstillinger](media/desktop-connect-to-data/designer_gsg_editquery.png)

Alle disse resultater er tekst i stedet for tal, og vi skal bruge tal. Intet problem. Du skal blot højreklikke på kolonneoverskriften og vælge **Skift type**  > **Heltal** for at ændre dem. Hvis du vil markere mere end én kolonne, skal du først markere en kolonne og derefter holde Skift nede, vælge yderligere tilstødende kolonner og derefter højreklikke på en kolonneoverskrift for at ændre alle de valgte kolonner. Brug Ctrl til at vælge de kolonner, der ikke er tilstødende.

![Skift datatypen til Heltal](media/desktop-connect-to-data/designer_gsg_changedatatype.png)

Under **Forespørgselsindstillinger** afspejler **ANVENDTE TRIN** de ændringer, der er foretaget. Når du foretager yderligere ændringer af dataene, registrerer Power-forespørgselseditoren disse ændringer i sektionen **ANVENDTE TRIN**, som du kan tilpasse, vende tilbage til, omarrangere eller slette efter behov.

![Anvendte trin](media/desktop-connect-to-data/designer_gsg_appliedsteps_changedtype.png)

Der kan stadig foretages yderligere ændringer i tabellen, når den er indlæst, men på nuværende tidspunkt er det fint, som det er. Når du er færdig, skal du vælge **Luk og anvend** på båndet **Hjem**, og Power BI Desktop anvender ændringerne og lukker Power-forespørgselseditoren.

![Luk og anvend](media/desktop-connect-to-data/connecttodata_closenload.png)

Mens datamodellen indlæst, kan vi i **rapportvisningen** i Power BI Desktop gå i gang med at oprette visualiseringer ved at trække felter til lærredet.

![Træk en værdi til lærredet](media/desktop-connect-to-data/connecttodata_dragontoreportview.png)

Det er selvfølgelig en simpel model med en enkelt dataforbindelse. De fleste Power BI Desktop-rapporter vil have forbindelser til forskellige datakilder, formet til dine behov, med relationer, der opretter en mere omfattende datamodel.

## <a name="next-steps"></a>De næste trin
Du kan gøre mange forskellige ting med Power BI Desktop. Du kan finde flere oplysninger om funktionerne i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Om brug af Forespørgselseditor i Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Udfør almindelige forespørgselsopgaver i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   

Vil du give os feedback? Fint. Brug menupunktet **Indsend en idé** i Power BI Desktop, eller besøg [Feedback fra community](https://community.powerbi.com/t5/Community-Feedback/bd-p/community-feedback). Vi ser frem til at høre fra dig!

![Send en ide](media/desktop-connect-to-data/sendfeedback.png)
