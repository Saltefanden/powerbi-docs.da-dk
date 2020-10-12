---
title: Kopiér rapporter fra andre apps eller arbejdsområder – Power BI
description: Få mere at vide om, hvordan du kan oprette en kopi af en rapport og gemme den i dit eget arbejdsområde.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 86c663e7b9ba035af6592dc10972d868344df7f7
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91633202"
---
# <a name="copy-reports-from-other-workspaces"></a>Kopiér rapporter fra andre arbejdsområder

Når du finder en rapport, du vil bruge i et arbejdsområde eller en app, kan du lave en kopi af den og gemme den i et andet arbejdsområde. Du kan derefter ændre din kopi af rapporten og tilføje eller slette visualiseringer og andre elementer. Du behøver ikke at oprette datamodellen. Den er allerede oprettet for dig. Og det er meget nemmere at redigere en eksisterende rapport end at starte forfra. Når du opretter en app fra dit arbejdsområde, kan du dog nogle gange ikke publicere din kopi af rapporten i appen. Se yderligere oplysninger under [Overvejelser og begrænsninger i artiklen "Brug datasæt på tværs af arbejdsområder"](service-datasets-across-workspaces.md#considerations-and-limitations).

> [!NOTE]
> Hvis du vil lave en kopi, skal du have en Pro-licens, selvom den oprindelige rapport er i et arbejdsområde med en Premium-kapacitet.

## <a name="save-a-copy-of-a-report-in-a-workspace"></a>Gem en kopi af en rapport i et arbejdsområde

1. Gå til listevisningen Rapporter i et arbejdsområde.

    ![Listevisningen Rapporter](media/service-datasets-copy-reports/power-bi-report-list-view.png)

1. Under **Handlinger** skal du vælge **Gem en kopi**.

    ![Gem en kopi af en rapport](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Du kan kun se ikonet **Gem en kopi**, hvis rapporten er i et arbejdsområde med den nye oplevelse, og du har [tilladelsen Opret](service-datasets-build-permissions.md). Selvom du har adgang til arbejdsområdet, skal du have tilladelsen Opret for datasættet.

3. Navngiv rapporten, og vælg destinationsarbejdsområdet under **Gem en kopi af denne rapport**.

    ![Dialogboksen Gem en kopi](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Du kan gemme rapporten i det aktuelle arbejdsområde eller et andet i Power BI-tjenesten. Du kan kun se arbejdsområder, som er arbejdsområder med den nye oplevelse, hvor du er medlem. 
  
4. Vælg **Gem**.

    Power BI opretter automatisk en kopi af rapporten og en post på listen over datasæt, hvis rapporten er baseret på et datasæt uden for arbejdsområdet. Ikonet for dette datasæt er forskellig fra ikonet for datasæt i arbejdsområdet: ![Ikon for delt datasæt](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)
    
    På denne måde kan medlemmer af arbejdsområdet se, hvilke rapporter og dashboards der bruger datasæt, som er uden for arbejdsområdet. Posten viser oplysninger om datasættet og nogle få udvalgte handlinger.

    ![Handlinger for datasæt](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

    Se [din kopi af rapporten](#your-copy-of-the-report) i denne artikel for at få mere at vide om rapporten og det relaterede datasæt.

## <a name="copy-a-report-in-an-app"></a>Kopiér en rapport i en app

1. Åbn den rapport, du vil kopiere, i en app.
2. Vælg **Flere indstillinger** ( **...** ) > **Gem en kopi** i menulinjen.

    ![Gem en kopi af rapporten](media/service-datasets-copy-reports/power-bi-save-copy.png)

    Du kan kun se indstillingen **Gem en kopi**, hvis rapporten er i et arbejdsområde med den nye oplevelse, og du har [tilladelsen Opret](service-datasets-build-permissions.md).

3. Giv din rapport et navn > **Gem**.

    ![Navngiv din kopi af rapporten](media/service-datasets-copy-reports/power-bi-save-report-from-app.png)

    Din kopi gemmes automatisk i mit arbejdsområde.

4. Vælg **Gå til rapport** for at åbne din kopi.

## <a name="your-copy-of-the-report"></a>Din kopi af rapporten

Når du gemmer en kopi af rapporten, opretter du en direkte forbindelse til datasættet, og du kan åbne oplevelsen for oprettelse af rapporten, hvor hele datasættet er tilgængeligt. 

![Rediger din kopi af rapporten](media/service-datasets-copy-reports/power-bi-edit-report-copy.png)

Du har ikke lavet en kopi af datasættet. Datasættet befinder sig stadig på den oprindelige placering. Du kan bruge alle tabeller og målinger i datasættet i din egen rapport. Begrænsninger for sikkerhed på rækkeniveau på datasættet er i kraft, så du kan kun se data, du har tilladelse til at se, på baggrund af din rolle for sikkerhed på rækkeniveau.

## <a name="view-related-datasets"></a>Få vist relaterede datasæt

Når du har en rapport i et arbejdsområde, der er baseret på et datasæt i et andet arbejdsområde, kan du få mere at vide om det datasæt, det er baseret på.

1. Vælg **Få vist relaterede** i listevisningen Rapporter.

    ![Skærmbillede, der viser ikonet Få vist relaterede under Handlinger.](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. I dialogboksen **Relateret indhold** vises alle relaterede elementer. På denne liste ligner datasættet ethvert andet. Du kan ikke se, at den befinder sig i et andet arbejdsområde. Dette er et kendt problem.
 
    ![Dialogboksen Relateret indhold](media/service-datasets-copy-reports/power-bi-dataset-related.png)

## <a name="delete-a-report-and-its-shared-dataset"></a>Slet en rapport og dens delte datasæt

Du kan beslutte, du ikke længere vil have rapporten og dens tilknyttede delte datasæt i arbejdsområdet.

1. Slet rapporten. På listen over rapporter i arbejdsområdet, skal du vælge ikonet **Slet**.

    ![Ikonet Slet rapport](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. På listen over datasæt kan du se, at de delte datasæt ikke har ikonet **Slet**. Opdater siden, eller gå til en anden side og vend tilbage igen. Datasættet vil nu være væk. Hvis dette ikke er tilfældet, skal du markere **Få vist relaterede**. Det kan være relateret til en anden tabel i dit arbejdsområde.

    ![Skærmbillede, der viser et datasæt med indstillingen Få vist relaterede, så det kan kontrolleres, om der er relaterede tabeller.](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > Hvis du sletter det delte datasæt i dette arbejdsområde, slette datasættet ikke. Der er kun referencen til det, der slettes.


## <a name="next-steps"></a>Næste trin

- [Brug datasæt på tværs af arbejdsområder](service-datasets-across-workspaces.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
