---
title: Opret rapporter baseret på datasæt fra forskellige arbejdsområder – Power BI
description: Få mere at vide om, hvordan du deler et datasæt med brugere på tværs af organisationen. De kan derefter oprette rapporter baseret på dit datasæt i deres egne arbejdsområder.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 59fc2d4be1336d9476c86e4204eeb23564ebe64e
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/27/2020
ms.locfileid: "92681108"
---
# <a name="create-reports-based-on-datasets-from-different-workspaces"></a>Opret rapporter baseret på datasæt fra forskellige arbejdsområder

Få mere at vide om, hvordan du opretter rapporter i dine egne arbejdsområder baseret på datasæt i andre arbejdsområder. Hvis du vil oprette en rapport ud fra et eksisterende datasæt, kan du starte fra Power BI Desktop eller fra Power BI-tjenesten, i Mit arbejdsområde eller i en [ny arbejdsområdeoplevelse](../collaborate-share/service-create-the-new-workspaces.md).

- I Power BI-tjenesten: **Hent data** > **Publicerede datasæt** .
- I Power BI Desktop: **Hent data** > **Power BI-datasæt** .

    ![Opret forbindelse til et eksisterende datasæt](media/service-datasets-across-workspaces/power-bi-connect-dataset-pk.png)
   
I begge tilfælde starter søgningsoplevelsen for datasæt i denne dialogboks: **Vælg et datasæt for at oprette en rapport** . Du kan se alle de datasæt, du har adgang til, uanset hvor de er placeret:

![Vælg et datasæt](media/service-datasets-across-workspaces/power-bi-select-dataset.png)

Du vil bemærke, at den første har mærkaten **Fremhævet** . Det kommer vi til senere i denne artikel under [Find et godkendt datasæt](#find-an-endorsed-dataset).

De datasæt, du ser på denne liste, opfylder mindst én af følgende betingelser:

- Datasættet er placeret i et af områderne med den nye arbejdsområdeoplevelse, og du er medlem af dette arbejdsområde. Se [Overvejelser og begrænsninger](service-datasets-across-workspaces.md#considerations-and-limitations).
- Du har tilladelsen Opret for datasættet, som er placeret i et arbejdsområde med den nye arbejdsområdeoplevelse.
- Datasættet er placeret i Mit arbejdsområde.

> [!NOTE]
> Hvis du er gratis bruger, kan du kun se datasæt i Mit arbejdsområde eller datasæt, du har tilladelsen Opret for, som er placeret i arbejdsområder med Premium-kapacitet.

Når du klikker på **Opret** , opretter du en direkte forbindelse til datasættet, og oplevelsen for oprettelse af rapporten åbnes, hvor hele datasættet er tilgængeligt. Du har ikke lavet en kopi af datasættet. Datasættet befinder sig stadig på den oprindelige placering. Du kan bruge alle tabeller og målinger i datasættet til at oprette dine egne rapporter. Begrænsninger for sikkerhed på rækkeniveau på datasættet er i kraft, så du kan kun se data, du har tilladelse til at se, på baggrund af din rolle for sikkerhed på rækkeniveau.

Du kan gemme rapporten i det aktuelle arbejdsområde i Power BI-tjenesten, eller du kan publicere rapporten i et arbejdsområde fra Power BI Desktop. Power BI opretter automatisk en post på listen over datasæt, hvis rapporten er baseret på et datasæt uden for arbejdsområdet. Ikonet for dette datasæt er forskellig fra ikonet for datasæt i arbejdsområdet: ![Ikon for delt datasæt](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)

På denne måde kan medlemmer af arbejdsområdet se, hvilke rapporter og dashboards der bruger datasæt, som er uden for arbejdsområdet. Posten viser oplysninger om datasættet og nogle få udvalgte handlinger.

![Handlinger for datasæt](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="find-an-endorsed-dataset"></a>Find et godkendt datasæt

Der er to forskellige slags anbefalede datasæt. Ejere af datasæt kan *fremhæve* et datasæt, som de har anbefalet til dig. Power BI-administratoren kan også udpege eksperter i organisationen, som kan *certificere* datasæt, som alle kan bruge. Der vises *badges* for fremhævede og certificerede datasæt, som du ser, både når du leder efter et datasæt og på listen over datasæt i et arbejdsområde. Navnet på den person, der har certificeret et datasæt, vises i et værktøjstip i søgningsoplevelsen for datasæt. Peg på etiketten **Certificeret** , så kan du se det.

- I Power BI-tjenesten: **Hent data** > **Publicerede datasæt** .
- I Power BI Desktop: **Hent data** > **Power BI-datasæt** .

    I dialogboksen **Vælg et datasæt** vises godkendte datasæt som standard øverst på listen. 

    ![Fremhævede datasæt](media/service-datasets-discover-across-workspaces/power-bi-dataset-promoted.png)

## <a name="next-steps"></a>Næste trin

- [Brug datasæt på tværs af arbejdsområder](service-datasets-across-workspaces.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
