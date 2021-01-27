---
title: 'Selvstudium: Kom i gang med at oprette i Power BI-tjenesten'
description: Kom i gang med Power BI-onlinetjenesten (app.powerbi.com)
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: tutorial
ms.date: 01/13/2021
LocalizationGroup: Get started
ms.openlocfilehash: 04777ba93b6a4639b55406b3952a80de963cb540
ms.sourcegitcommit: 5c5a27aa7ba21612df4c4096e635dfe4b9aaebcf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2021
ms.locfileid: "98861209"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>Selvstudium: Kom i gang med at oprette i Power BI-tjenesten
Dette selvstudium er en introduktion til nogle af funktionerne i *Power BI-tjenesten.* I selvstudiet lærer du, hvordan du opretter forbindelse til data, opretter en rapport og et dashboard samt stiller spørgsmål til dine data. Du kan udføre mange flere opgaver i Power BI-tjenesten, og dette selvstudium er kun ment som en appetitvækker. Hvis du vil have en forståelse af, hvordan Power BI-tjenesten passer sammen med de andre Power BI-tilbud, anbefaler vi, at du læser artiklen [Hvad er Power BI](power-bi-overview.md).

Er du en *rapportlæser* frem for en forfatter? [Navigation i Power BI-tjenesten](../consumer/end-user-experience.md) er et godt sted at starte for dig.

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Skærmbillede af dashboard med økonomieksempel.":::

I dette selvstudium kan du udføre følgende trin:

> [!div class="checklist"]
> * Log på din Power BI-onlinekonto, eller opret en konto, hvis du endnu ikke har en.
> * Åbn Power BI-tjenesten.
> * Hent nogle data, og åbn dem i rapportvisning.
> * Brug disse data til at oprette visualiseringer, og gem dem som en rapport.
> * Opret et dashboard ved at fastgøre felter fra rapporten.
> * Føj andre visualiseringer til dit dashboard ved hjælp af værktøjet Spørgsmål og svar i naturligt sprog.
> * Tilpas størrelsen på, flyt rundt på og rediger detaljerne for felterne på dashboardet.
> * Fjern ressourcer ved at slette datasættet, rapporten og dashboardet.

## <a name="sign-up-for-the-power-bi-service"></a>Tilmeld dig Power BI-tjenesten
Du skal have en Power BI Pro-licens for at oprette indhold i Power BI. Hvis du ikke har en Power BI-konto, [kan du tilmelde dig en gratis prøveversion af Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web), før du begynder.

## <a name="step-1-get-data"></a>Trin 1: Hent data

Når du vil oprette en Power BI rapport, starter du ofte Power BI Desktop. Med Power BI Desktop bliver du endnu mere effektiv. Du kan transformere, forme og udforme data, før du går i gang med at designe rapporter. Denne gang går vi dog i gang med at oprette en rapport fra bunden i Power BI-tjenesten.

I dette selvstudium henter vi data fra en enkel Microsoft Excel-fil. Vil du følge med? [Download filen Økonomieksempel](https://go.microsoft.com/fwlink/?LinkID=521962).

1. Du skal først åbne Power BI-tjenesten i din browser (app.powerbi.com). 

    Har du ikke en konto? Helt i orden, du kan [tilmelde dig og få en gratis prøveversion af Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Vælg **Mit arbejdsområde** i navigationsruden.

1. I **Mit arbejdsområde** skal du vælge **Nyt** > **Upload en fil**.

    Siden **Hent data** åbnes.   

3. Sørg for at **Filer** i afsnittet **Opret nyt indhold** er valgt, og vælg derefter den placering, hvor du gemte Excel-filen.
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="Skærmbillede af Opret nyt indhold > Filer.":::

5. Gå til filen på din computer, og vælg **Åbn**.

5. Til dette selvstudium vælger vi **Importér** for at tilføje Excel-filen som et datasæt. Derefter kan vi bruge datasættet til at oprette rapporter og dashboards. Hvis du vælger **Upload**, uploades hele Excel-projektmappen til Power BI, hvor du kan åbne og redigere den i Excel Online.
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="Skærmbillede af valg af import.":::
6. Når dit datasæt er klar, skal du vælge **Flere indstillinger (...)** ud for datasættet Økonomieksempel og derefter vælge **Opret rapport**.
1. åbn rapporteditoren. 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="Skærmbillede af Alt indhold > Opret en rapport.":::

    Rapportlærredet er tomt. Til højre kan du se ruderne **Visualiseringer**, **Filtre** og **Felter**.

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="Skærmbillede af tomt rapportlærred.":::

    > [!TIP]
    > Vælg knappen til global navigation i øverste venstre hjørne for at skjule navigationsruden. På den måde får du mere plads på dit lærred.
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="Knappen til global navigation.":::
    >

7. Du er i øjeblikket i visningen Redigering. Bemærk indstillingen **Læsevisning** på menulinjen. 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="Skærmbillede af indstillingen Læsevisning.":::

    Når du er Redigeringsvisning, kan du redigere rapporter, fordi du er *ejer* og *forfatter* af rapporten. Når du deler din rapport med kolleger, kan de ofte kun interagere med rapporten i Læsevisning. De er *forbrugere* af rapporter i dit **Mit arbejdsområde**. 

## <a name="step-2-create-a-chart-in-a-report"></a>Trin 2: Opret et diagram i en rapport
Nu hvor du har forbindelse til data, kan du begynde at udforske. Når du har fundet noget interessant, kan du gemme det på rapportlærredet. Du kan derefter fastgøre det til et dashboard, så du kan overvåge det, og se, hvordan det ændrer sig over tid. Lad os starte med det vigtigste først.
    
1. Vi begynder med at oprette en visualisering i ruden **Felter** i højre side i rapporteditoren. Vælg feltet **Samlet salg** og derefter feltet **Dato**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="Skærmbillede af listen Felter.":::

    Power BI analyserer dataene og opretter en søjlediagramsvisualisering. 

    > [!NOTE]
    > Hvis du valgte feltet **Dato** først i stedet for **Samlet salg**, får du vist en tabel. Bare rolig. Vi ændrer visualiseringen i næste trin.

    Der vises Sigma-symboler ud for nogle felter, da Power BI registrerede, at de indeholder numeriske værdier.

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="Felter med Sigma-symboler.":::

2. Lad os skifte til en anden måde at vise disse data på. Kurvediagrammer er gode visualiseringer til visning af værdier over tid. Vælg ikonet for **kurvediagrammet** i ruden **Visualiseringer**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="Skærmbillede af Rapporteditor med kurvediagram valgt.":::

3. Dette diagram ser interessant ud, så lad os *fastgøre* det til et dashboard. Hold over visualiseringen, og vælg ikonet med tegnestiften.
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="Skærmbillede af fastgørelsesikonet.":::

4. Da denne rapport er ny, bliver du bedt om at gemme den, før du kan fastgøre en visualisering på et dashboard. Giv din rapport et navn (f.eks. *Rapport med økonomieksempel*), og klik derefter på **Gem**. 

    Nu ser du rapporten i Læsevisning. 

6. Vælg **fastgørelsesikonet** igen.
 
5. Vælg **Nyt dashboard**, og navngiv det *Dashboard med økonomieksempel*. 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="Et skærmbillede af navnet på dashboardet.":::
  
    En meddelelse om fuldførelse (i nærheden af øverste højre hjørne) giver dig besked om, at visualiseringen blev føjet til dit dashboard som et felt.
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="Skærmbillede af dialogboksen Fastgjort til dashboard.":::

    Nu, hvor du har fastgjort denne visualisering, gemmes den på dashboardet. Dataene forbliver opdaterede, så du kan spore den seneste værdi på et øjeblik. Hvis du ændrer visualiseringen i rapporten, ændres feltet på dashboardet ikke.

7. Vælg **Gå til dashboard** for at se det nye dashboard med det kurvediagram, du har fastgjort til det som et felt. 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="Skærmbillede af dashboard med fastgjort visualisering.":::
   
8. Vælg det nye felt på dashboardet. Power BI vender tilbage til rapporten i Læsevisning.

1. Hvis du vil skifte tilbage til Redigeringsvisning, skal du vælge **Flere indstillinger** (...) i den øverste menulinje > **Rediger**.

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="Skærmbillede af valg af Rediger for at redigere rapporten.":::

    Når du er tilbage i Redigeringsvisning, kan du fortsætte med at udforske og fastgøre felter.

## <a name="step-3-explore-with-qa"></a>Trin 3: Udforsk med Spørgsmål og svar

Hvis du vil foretage en hurtig udforskning af dine data, kan du prøve at stille et spørgsmål i spørgsmålsfeltet Spørgsmål og svar. Med Spørgsmål og svar kan du oprette forespørgsler på et naturligt sprog om dine data. I et dashboard er feltet Spørgsmål og svar placeret øverst (**Stil et spørgsmål om dine data**) under menulinjen. I en rapport er det placeret i den øverste navigationsrude (**Stil et spørgsmål**).

1. Hvis du vil vende tilbage til dashboardet, skal du vælge **Mit arbejdsområde** på den sorte overskriftslinje i **Power BI**.

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="Skærmbillede af Gå tilbage til Mit arbejdsområde.":::

1. Vælg dit dashboard i **Mit arbejdsområde**.

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="Skærmbillede af valg af dit dashboard.":::

1. Vælg **Stil et spørgsmål om dine data**. Der vises automatisk en række forslag i Spørgsmål og svar. 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="Skærmbillede af lærredet Spørgsmål og svar.":::

    > [!NOTE]
    > Hvis du ikke kan se forslagene, kan du slå den **nye Spørgsmål og svar-oplevelse** til.

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="Skærmbillede af, hvordan du aktiverer ny Spørgsmål og svar-oplevelse.":::

1. Nogle af forslagene returnerer én enkelt værdi. Du kan f.eks. vælge **hvad er det gennemsnitlige vareforbrug**.

    Spørgsmål og svar søger efter svar og præsenterer dem i form af et *kort*.

3. Vælg **Fastgør visualisering**, og fastgør visualiseringen til dashboardet Økonomieksempel.

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="Skærmbillede af visualiseringen, der fastgøres.":::

1. Gå tilbage til Spørgsmål og svar, og vælg **Vis alle forslag**.
1. Vælg **samlet overskud efter land**. 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="Skærmbillede af samlet overskud efter land.":::

1. Fastgør kortet på dashboardet Økonomieksempel.

1. Vælg det kort på dashboardet, du lige har fastgjort. Vil du se, hvordan det åbner Spørgsmål og svar igen? 
1. Placer markøren efter *efter land* i feltet Spørgsmål og svar, og skriv *som søjle*. Power BI opretter straks et liggende søjlediagram med resultaterne.

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="Skærmbillede af en søjlediagramsvisualisering.":::

1. Fastgør også søjlediagrammet til dashboardet Økonomieksempel.

4. Vælg **Afslut spørgsmål og svar** for at vende tilbage til dit dashboard, hvor du kan se det nye felt, du har oprettet. 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="Skærmbillede af dashboard med visualiseringer i Spørgsmål og svar fastgjort.":::

   Du kan se, at selvom du har ændret kortet til et søjlediagram i Spørgsmål og svar, forbliver feltet et kort, da det er det, det var, da du fastgjorde det. 

## <a name="step-4-reposition-tiles"></a>Trin 4: Flyt felter

Vi kan flytte rundt på felterne for at udnytte pladsen i dashboardet bedre.

1. Træk det nederste højre hjørne af kurvediagramfeltet *Bruttosalg* opad, indtil det får den samme højde som feltet Salg, og slip det så.

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="Skærmbillede af tilpasning af feltets størrelse.":::

    Nu har de to felter den samme højde.

1. Vælg **Flere indstillinger (...)** for feltet Gennemsnittet af vareforbrug > **Rediger detaljer**. 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="Skærmbillede af menuen Flere indstillinger for et felt.":::

1. I feltet **Titel** skal du skrive *Gennemsnitlig kostpris for solgte varer* > **Anvend**.

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="Skærmbillede af dialogboksen Rediger detaljer.":::

1. Omarranger de andre visuelle elementer, så de passer sammen.

    Det ser bedre ud.

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Skærmbillede af omarrangeret dashboard.":::


## <a name="clean-up-resources"></a>Fjern ressourcer
Nu, hvor du har gennemført selvstudiet, kan du slette datasættet, rapporten og dashboardet. 

1. Vælg **Mit arbejdsområde** på den sorte overskriftslinje i **Power BI**.
2. Vælg **Flere indstillinger (...)** ud for datasættet Økonomieksempel > **Slet**.

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="Skærmbillede af sletning af datasættet.":::

    Du får vist en advarsel om, at **alle de rapport- og dashboardfelter, der indeholder data fra datasættet, også vil blive slettet**.

4. Vælg **Slet**.

## <a name="next-steps"></a>Næste trin

[Opret hurtigt en rapport ved at indsætte data i Power BI-tjeneste](https://powerbi.microsoft.com/en-us/blog/quickly-create-reports-power-bi-service/)

Udforsk disse samlinger af Microsoft Learn-indhold til Power BI:

- [Få mere at vide om Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
- [Bliv Power BI-dataanalytiker](/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm)