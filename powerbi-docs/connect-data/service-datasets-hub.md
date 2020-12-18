---
title: Sådan finder du et datasæt ved hjælp af datasæthubben
description: Få mere at vide om, hvordan du kan finde, udforske og bruge datasæt og de relaterede rapporter i din organisation.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/14/2020
LocalizationGroup: Share your work
ms.openlocfilehash: c6b7170df78b6d544f7eb97ec62516577f9267b6
ms.sourcegitcommit: b5365df7fc32b7c49f8a2bf2cf75b5edd6bda9b6
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513798"
---
# <a name="datasets-discovery-using-the-datasets-hub"></a>Sådan finder du et datasæt ved hjælp af datasæthubben

Med en datasæthub er det nemt at finde, udforske og bruge datasæt i din organisation. Hubben indeholder oplysninger om datasæt samt indgangspunkter til oprettelse af rapporter oven på disse datasæt eller til brug af disse datasæt med Analysér i Excel.

Datasæthubben kan være nyttig i mange scenarier:
* Ejere af datasæt kan se statistik for datasæt, opdateringsstatus, relaterede rapporter og afstamning, så de kan få hjælp til at overvåge og administrere deres datasæt.
* Oprettere af rapporter kan bruge hubben til at finde egnede datasæt til at oprette deres rapporter på og bruge links til nemt at oprette rapporter, der er baseret på datasættet, enten fra bunden eller fra skabeloner.
* Rapportforbrugere kan bruge denne side til at finde rapporter, der er baseret på datasæt, der er tillid til.

Ved at gøre det nemt at finde datasæt i god kvalitet og de relaterede rapporter er datasæthubben med til at forhindre, at der oprettes redundante rapporter. Hubben gør det også nemt at finde gode rapporter, der skal bruges til oprettelse af nye rapporter.

I denne artikel forklares det, hvad du kan finde i datasæthubben, og hvordan du bruger den. For ejere af datasæt indeholder artiklen også en række tip til, hvordan det [gøres lettere at finde og bruge datasæt](#make-your-dataset-discoverable).

**Hvilke datasæt kan jeg se i datasæthubben?**
* Hvis et datasæt skal vises i datasæthubben, skal det være placeret i en [ny arbejdsområdeoplevelse](../collaborate-share/service-new-workspaces.md).
* De datasæt, du kan se i datasæthubben, er dem, du mindst har [oprettelsestilladelser](service-datasets-build-permissions.md) til.
* Hvis du er en gratis bruger, kan du kun se datasæt i *Mit arbejdsområde* eller datasæt, du har tilladelsen [Opret](service-datasets-build-permissions.md) for, og som er placeret i arbejdsområder i en Premium-kapacitet.

## <a name="find-the-dataset-you-need"></a>Find de datasæt, du har brug for

Funktionen til at finde datasæt starter på siden med datasæthubben. Sådan kommer du til siden med datasæthubben:
* I Power BI-tjenesten: Vælg **Datasæt** i navigationsruden.
* I Power BI-appen i Teams: Vælg enten fanen **Datasæt** eller **Datasæt** i navigationsruden.

På billedet nedenfor vises datasæthubben i Power BI-tjenesten.

![Skærmbillede af siden med datasæthubben](media/service-datasets-hub/datasets-hub-main-page.png)

Datasæthubben giver dig et udvalg af anbefalede datasæt og en liste over alle datasæt i organisationen, som du har tilladelse til at få adgang til.

I afsnittene nedenfor beskrives disse afsnit og de handlinger, du kan udføre.

### <a name="recommended-datasets"></a>Anbefalede datasæt

Anbefalede datasæt er godkendte datasæt (fremhævede eller certificerede), der præsenteres for dig baseret på en beregning, der tager højde for, hvornår de senest er blevet opdateret, og hvornår du sidst har besøgt rapporter og/eller dashboards, der er knyttet til dem.

### <a name="dataset-list"></a>Datasætliste

Datasætlisten viser de datasæt i organisationen, som du mindst har [oprettelsestilladelser](service-datasets-build-permissions.md) til. Listen indeholder tre faner til filtrering af listen over datasæt.
* **Alle datasæt**: Viser alle datasæt i organisationen, som du mindst har [oprettelsestilladelser](service-datasets-build-permissions.md) til.
* **Seneste**: Viser de datasæt, hvis relaterede rapporter, du har haft åbnet for nylig. Når du åbner en rapport, kan der være en forsinkelse på flere minutter, indtil det relaterede datasæt vises i kolonnen Seneste.
* **Mine datasæt**: Viser de datasæt, du ejer. 

Brug søgefeltet til yderligere at filtrere elementerne på den aktuelle fane.

Kolonnerne på listen er beskrevet nedenfor. Klik på en kolonneoverskrift for at sortere efter den pågældende kolonne. 
* **Navn**: Navnet på datasættet. Klik på navnet på datasættet for at se nærmere på de rapporter, der er bygget ved hjælp af dette datasæt.
* **Anbefaling**: Anbefalingsstatus.
* **Ejer**: Ejeren af datasættet.
* **Arbejdsområde**: Det arbejdsområde, datasættet er placeret i.
* **Opdateret**: Tidspunkt for seneste opdatering (afrundet til time, dag, måned og år. Se oplysningerne om datasættet på detaljesiden for datasættet for at finde det nøjagtige tidspunkt for seneste opdatering).
* **Følsomhed**: Følsomheden, hvis den er angivet. Klik på infoikonet for at få vist beskrivelsen af følsomhedsmærkatet.

### <a name="create-new-reports-or-pull-data-into-excel-via-analyze-in-excel"></a>Opret nye rapporter, eller træk data til Excel via Analysér i Excel

Hvis du vil oprette en ny rapport, der er baseret på datasæt, eller hvis du vil hente dataene til Excel med [Analysér i Excel](../collaborate-share/service-analyze-in-excel.md), skal du vælge **Flere indstillinger (...)** enten i nederste højre hjørne af et anbefalet datasæt eller på et datasæts linje på listen over datasæt. Andre handlinger kan blive vist i rullemenuen, afhængigt af de tilladelser du har for datasættet.

Når du opretter en ny rapport, der er baseret på datasættet, åbnes siden til redigering af rapporten. Når du gemmer den nye rapport, gemmes den i det arbejdsområde, der indeholder datasættet, hvis du har skriverettigheder til det pågældende arbejdsområde. Hvis du ikke har skriverettigheder til det pågældende arbejdsområde, eller hvis du er en gratis bruger, og datasættet er placeret i et arbejdsområde i en Premium-kapacitet, gemmes den nye rapport i *Mit arbejdsområde*.

## <a name="view-dataset-details-and-explore-related-reports"></a>Få vist oplysninger om datasæt, og udforsk relaterede rapporter

Hvis du vil have vist flere oplysninger om datasættet, udforske relaterede rapporter eller oprette en ny rapport, der er baseret på datasættet, eller fra bunden, skal du vælge et datasæt blandt de anbefalede datasæt eller på listen over datasæt. Der vises en side med oplysninger om datasættet, de rapporter, der er bygget oven på datasættet, og indgangspunkter til oprettelse af nye rapporter, der er baseret på datasættet, eller hvordan dataene hentes til Excel via [Analysér i Excel](../collaborate-share/service-analyze-in-excel.md).

![Skærmbillede af datasæthub med siden til udforskning af relaterede rapporter](media/service-datasets-hub/datasets-hub-explore-related-reports.png)

Sidehovedet viser navnet på datasættet, en anbefaling, hvis der er en, og ejeren af datasættet. Hvis du vil sende en mail til ejeren af datasættet eller til den, der har certificeret datasættet (hvis der er en), skal du klikke på overskriften og derefter klikke på navnet på ejeren.

### <a name="dataset-details"></a>Oplysninger om datasæt

Afsnittet med oplysninger om datasættet viser navnet på det arbejdsområde, hvor datasættet er placeret, det nøjagtige klokkeslæt for den seneste opdatering, følsomhed (hvis den er angivet), beskrivelsen af datasættet (hvis det er relevant) og navnet på den, der har certificeret datasættet (hvis det er certificeret). Du kan også åbne datasætafstamningen her.

### <a name="related-reports"></a>Relaterede rapporter

I afsnittet Udforsk relaterede rapporter kan du se alle de rapporter, der er bygget på det valgte datasæt. Du kan oprette en kopi af en rapport ved at vælge rapportlinjen på listen og derefter klikke på ikonet Gem en kopi af denne rapport.

Kolonnerne på listen over relaterede rapporter er:
* **Navn**: Rapportnavnet. Hvis navnet ender på (skabelon), betyder det, at denne rapport er særligt oprettet til at blive brugt som skabelon.
* **Anbefaling**: Anbefalingsstatus.
* **Arbejdsområde**: Navnet på det arbejdsområde, hvor rapporten er placeret.

### <a name="create-a-report-built-on-the-dataset"></a>Opret en rapport, der er bygget på datasættet

Klik på knappen **Opret** i afsnittet til oprettelse af en rapport. Hvis der er en rapportskabelon for datasættet, indeholder en rullemenu to muligheder:
* **Fra skabelon**: Opretter en kopi af skabelonen i *Mit arbejdsområde*.
* **Fra bunden**: Åbner lærredet til redigering af rapporter til en ny rapport, der er bygget på datasættet. Når du gemmer den nye rapport, gemmes den i det arbejdsområde, der indeholder datasættet, hvis du har skriverettigheder til det pågældende arbejdsområde. Hvis du ikke har skriverettigheder til det pågældende arbejdsområde, eller hvis du er en gratis bruger, og datasættet er placeret i et arbejdsområde i en Premium-kapacitet, gemmes den nye rapport i *Mit arbejdsområde*.

Hvis der ikke er nogen rapportskabeloner, åbnes lærredet til redigering af rapporten direkte, hvis du klikker på **Opret**.

>[!NOTE]
> Der vises kun én skabelon på rullelisten Opret rapport, selvom der findes mere end én rapportskabelon for dette datasæt. 

### <a name="pull-the-dataset-into-excel-via-analyze-in-excel"></a>Træk datasættet ind i Excel via Analysér i Excel

I afsnittet Analysér i Excel skal du vælge **Analysér** for at hente datasættet ind i Excel via Analysér i Excel.

## <a name="make-your-dataset-discoverable"></a>Gør dit datasæt synligt

Der er flere måder, hvorpå du kan forbedre synligheden af dine datasæt:
* **Anbefal dit datasæt**: Du kan fremhæve eller certificere dit datasæt for at gøre det nemmere for brugerne at finde det og give dem besked om, at det er en troværdig datakilde. Anbefalede datasæt er mærket med badges og er lette at identificere i Power BI. I datasættethubben vises kun anbefalede datasæt i afsnittet med anbefalede datasæt, og listen over datasæt viser som standard de anbefalede datasæt først.

    [Få mere at vide om, hvordan du kan anbefale dine datasæt](../collaborate-share/service-endorse-content.md). 
* **Angiv en relevant beskrivelse af datasættet**: Du kan hjælpe brugerne med at finde det rette datasæt ved at give nyttige beskrivelser af dine datasæt. [Du angiver beskrivelsen som en del af processen til anbefaling af datasættet](../collaborate-share/service-endorse-content.md#promote-content). 
* **Giv dit datasæt et billede, der er let at huske**: Du kan gøre det nemmere for brugerne at finde og huske dit datasæt ved at give det et billede, der er let at huske. Det får dit datasæt til at skille sig ud på datasæthubsiden og andre steder, der understøtter visning af datasætbilleder. Hvis du vil give dit datasæt et billede, skal du åbne indstillingerne for datasættet og udvide datasætbilledafsnittet.
* **Opret en rapportskabelon, der er bygget på datasættet**: Du kan oprette en rapportskabelon, som brugerne kan bruge til at komme i gang med at bygge deres egne rapporter baseret på dit datasæt. Denne skabelon er ganske enkelt en almindelig rapport, som du designer med det for øje, at den skal bruges som en skabelon. Når du gemmer den, skal du føje suffikset "(skabelon)" til navnet på rapporten, f.eks. *Månedligt salg (skabelon)* .

    Når en bruger vælger **Opret > Fra skabelon** i afsnittet til oprettelse af en rapport i detaljevisningen for datasættet i datasæthubben, oprettes en kopi af skabelonen i brugerens *Mit arbejdsområde*, og skabelonen åbnes derefter på lærredet til redigering af rapporten.

    Rapportskabeloner er også lette at identificere på listen over relaterede rapporter i visningen datasætdetaljer i datasæthubben.
  
## <a name="next-steps"></a>Næste trin
* [Brug datasæt på tværs af arbejdsområder](service-datasets-across-workspaces.md)
* [Opret rapporter baseret på datasæt fra forskellige arbejdsområder](service-datasets-discover-across-workspaces.md)
* [Anbefal dit datasæt](../collaborate-share/service-endorse-content.md)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
