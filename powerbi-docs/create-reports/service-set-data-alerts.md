---
title: Indstil databeskeder i Power BI-tjenesten
description: Få mere at vide om, hvordan du angiver beskeder, så du får besked, når dataene på dine dashboards ændres ud over de grænser, du har angivet i Microsoft Power BI-tjenesten.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/02/2020
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 55d196a9b041f52632300f6e10c00d753ca02a14
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635073"
---
# <a name="data-alerts-in-the-power-bi-service"></a>Databeskeder i Power BI-tjenesten

Angiv beskeder, så du får besked, når dataene på dine dashboards ændres ud over de grænser, du har angivet.

Du kan konfigurere beskeder på felter i Mit arbejdsområde. Du kan også konfigurere beskeder, hvis nogen deler et dashboard, der er i en [Premium-kapacitet](../admin/service-premium-what-is.md). Hvis du har en Power BI Pro-licens, kan du også konfigurere beskeder på felter i andre arbejdsområder. Der kan kun angives beskeder på felter, der er fastgjort via rapportvisualiseringer, og kun på målere, KPI'er og kort. Beskeder kan angives på visuelle elementer, der er oprettet ud fra streamingdatasæt, som du fastgør fra en rapport til et dashboard. Der kan ikke angives beskeder for streamingfelter, der er oprettet direkte på dashboardet ved hjælp af **Tilføj felt** > **Brugerdefinerede streamingdata**.

Det er kun dig, der kan se de angivne beskeder, selvom du deler dashboardet. Selv ejeren af dashboardet kan ikke se de vigtige beskeder, du angiver for din visning af deres dashboard. Databeskeder er fuldt synkroniseret på tværs af platforme. Angiv og få vist databeskeder [i Power BI-mobilapps](../consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md) og i Power BI-tjenesten. De er ikke tilgængelige for Power BI Desktop. Du kan endda automatisere og integrere beskeder med Power Automate. Du kan prøve det selv i denne artikel om [Power Automate og Power BI](../collaborate-share/service-flow-integration.md).

![felter](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Datadrevne beskeder indeholder oplysninger om dine data. Hvis du får vist dine data i Power BI på en mobilenhed, og du mister enheden, eller den bliver stjålet, anbefaler vi, at du bruger Power BI-tjenesten til at slå alle datadrevne regler for beskeder fra.

## <a name="set-data-alerts-in-the-power-bi-service"></a>Indstil databeskeder i Power BI-tjenesten

Se, hvordan Amanda føjer nogle beskeder til felterne på dashboardet. Følg derefter en trinvis vejledning under videoen for at prøve det selv.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

I dette eksempel bruges et kortfelt fra eksempeldashboardet Retail Analysis. Hvis du vil følge med, skal du hente [eksemplet med en detailhandelsanalyse](sample-retail-analysis.md#get-the-content-pack-for-this-sample).

1. Start på et dashboard. Vælg ellipsen på feltet **Butikker i alt**.

   ![Feltet Butikker i alt](media/service-set-data-alerts/powerbi-card.png)

1. Vælg klokkeikonet for ![Beskedikon](media/service-set-data-alerts/power-bi-bell-icon.png) for at tilføje en eller flere beskeder om **Butikker i alt**.

1. Når du starter, skal du vælge **+ Tilføj påmindelsesregel**, sikre, at skyderen **Aktiv** er angivet til **Til** og give din besked en titel. Titler hjælper dig med let at genkende dine beskeder.

   ![Skærmbillede, der viser vinduet Administrer beskeder Tilføj en beskedregel, Besked for butikker i alt og Beskedtitel fremhævet.](media/service-set-data-alerts/powerbi-alert-title.png)

1. Rul ned, og angiv oplysninger om beskederne.  I dette eksempel opretter vi en besked, som skal sendes til os én gang om dagen, hvis antallet af samlede butikker går over 100.

   ![Vinduet Administrer beskeder, angiv grænseværdi](media/service-set-data-alerts/power-bi-set-alert-details.png)

    Beskederne vises i dit **meddelelsescenter**. Power BI sender også en mail om beskeden, hvis du markerer afkrydsningsfeltet.

1. Vælg **Gem og luk**.

## <a name="receiving-alerts"></a>Modtagelse af beskeder

Når de sporede data når en af de angivne tærskelværdier, som du har angivet, sker der flere ting. Først tjekker Power BI, om der er gået mere end én time eller mere end et døgn (afhænger af den valgte indstilling) siden den seneste besked. Du får en besked, hvis dataene har overskredet grænsen.

Derefter sendes en besked til dit **meddelelsescenter** og eventuelt en mail via Power BI. Hver enkelt besked indeholder et direkte link til dine data. Vælg linket for at se det relevante felt, hvor du kan udforske, dele og få mere at vide.  

* Hvis du har angivet for beskeden, at du skal have tilsendt en mail, kan du finde noget i stil med dette i din indbakke.

   ![Mail med vigtig besked](media/service-set-data-alerts/powerbi-alerts-email.png)

* Power BI føjer en meddelelse til dit **meddelelsescenter** og føjer et ny beskedikon til det relevante felt.

   ![Meddelelsesikon i Power BI-tjeneste](media/service-set-data-alerts/powerbi-alert-notifications.png)

* Detaljer om beskeden vises i dit **meddelelsescenter**.

    ![læs beskeden](media/service-set-data-alerts/powerbi-alert-notification.png)

   > [!NOTE]
   > Beskeder fungerer kun for opdaterede data. Når data opdateres, kontrolleres det via Power BI, om der er angivet en besked for disse data. Hvis dataene har nået grænsen for en besked, udløser Power BI en besked.

## <a name="managing-alerts"></a>Administration af beskeder

Der er mange måder at administrere dine beskeder på:

* Fra dashboardfeltet.

* Fra menuen Indstillinger for Power BI.

* På et felt i [Power BI-mobilappene](../consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-dashboard-tile"></a>Fra dashboardfeltet

1. Hvis du vil ændre eller fjerne en besked fra et felt, skal du åbne vinduet **Administrer beskeder** igen ved at vælge klokkeikonet for ![Beskedikon](media/service-set-data-alerts/power-bi-bell-icon.png).

    Power BI viser alle de beskeder, du har angivet for dette felt.

    ![Skærmbillede, der viser vinduet Administrer beskeder.](media/service-set-data-alerts/powerbi-see-alerts.png)

1. Hvis du vil redigere en besked, skal du vælge pilen til venstre for beskednavnet.

    ![pil ud for Beskednavn](media/service-set-data-alerts/powerbi-see-alerts-arrow.png)

1. Hvis du vil slette en besked, skal du vælge skraldespanden til højre for beskednavnet.

      ![Skraldespandsikonet er valgt](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>I menuen Indstillinger for Power BI

1. Vælg tandhjulsikonet på menulinjen i Power BI, og vælg **Indstillinger**.

    ![tandhjulsikon](media/service-set-data-alerts/powerbi-gear-icon.png).

1. Under **Indstillinger** skal du vælge **Beskeder**.

    ![Fanen Beskeder i vinduet Indstillinger](media/service-set-data-alerts/powerbi-alert-settings.png)

1. Her kan du slå beskeder til og fra, åbne vinduet **Administrer beskeder** for at ændre eller slette beskeden.

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

* Beskeder understøttes ikke for kortfelter med målinger for dato/klokkeslæt.
* Beskeder fungerer kun i forbindelse med numeriske datatyper.
* Beskeder fungerer kun for opdaterede data. De fungerer ikke med statiske data.
* Beskeder fungerer kun i forbindelse med streamingdatasæt, hvis du opretter en rapportvisualisering for KPI/kort/måler og derefter fastgør visualiseringen til dashboardet.


## <a name="next-steps"></a>De næste trin

* [Opret en Power Automate, der indeholder en databesked](../collaborate-share/service-flow-integration.md).

* [Angiv databeskeder på din mobilenhed](../consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

* [Hvad er Power BI?](../fundamentals/power-bi-overview.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
