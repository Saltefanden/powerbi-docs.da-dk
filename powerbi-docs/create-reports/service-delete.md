---
title: Slet et dashboard, en rapport, en projektmappe, et datasæt eller et arbejdsområde
description: Få mere at vide, hvordan du sletter næsten alt fra Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/11/2018
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: b2263a1eddfdbc51f0e345443f7bbb75b11da6e7
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91632726"
---
# <a name="delete-almost-anything-in-power-bi-service"></a>Slet næsten alt i Power BI-tjenesten
I denne artikel kan du lære, hvordan du sletter et dashboard, en rapport, en projektmappe, et datasæt, en app og et arbejdsområde i Power BI-tjenesten.

## <a name="delete-a-dashboard"></a>Slet et dashboard
Dashboards kan fjernes. Når du fjerner et dashboard, sletter du ikke det underliggende datasæt eller de rapporter, der er knyttet til dette dashboard.

* Hvis du er ejeren af dashboardet, kan du fjerne det. Hvis du har delt dashboardet med kolleger, fjernes det fra deres Power BI-arbejdsområder, når du fjerner det fra dit Power BI-arbejdsområde.
* Hvis et dashboard er delt med dig, og du ikke længere vil se det, kan du fjerne det.  Når du fjerner et dashboard, fjernes det ikke fra alle andres Power BI-arbejdsområde.
* Hvis et dashboard er en del af en [organisationsindholdspakke](../collaborate-share/service-organizational-content-pack-disconnect.md), kan du kun fjerne det ved at fjerne det tilknyttede datasæt.

### <a name="to-delete-a-dashboard"></a>Sådan sletter du et dashboard
1. Vælg fanen **Dashboards** i dit arbejdsområde.
2. Find det dashboard, du vil slette, og vælg sletteikonet :::image type="icon" source="media/service-delete/power-bi-delete-icon.png" border="false":::.

    ![video](media/service-delete/power-bi-delete-dash.gif)

## <a name="delete-a-report"></a>Slet en rapport
Bare rolig, når du sletter en rapport, bliver det datasæt, som rapporten er baseret på, ikke slettet.  Eventuelle visualiseringer, som du har fastgjort fra rapporten, er også sikre. De forbliver på dashboardet, indtil du sletter dem enkeltvist.

### <a name="to-delete-a-report"></a>Sådan sletter du en rapport
1. Vælg fanen **Rapporter** i dit arbejdsområde.
2. Find den rapport, du vil slette, og vælg sletteikonet :::image type="icon" source="media/service-delete/power-bi-delete-icon.png" border="false":::.   

    ![fanen Rapporter i et arbejdsområde](media/service-delete/power-bi-delete-reportnew.png)
3. Bekræft sletningen.

   ![Dialogboksen Slet rapport](media/service-delete/power-bi-delete-report.png)

   > [!NOTE]
   > Hvis rapporten er en del af en [indholdspakke](../collaborate-share/service-organizational-content-pack-introduction.md), kan du ikke slette den ved hjælp af denne metode.  Se [Fjern din forbindelse til en organisationsindholdspakke](../collaborate-share/service-organizational-content-pack-disconnect.md).
   >
   >

## <a name="delete-a-workbook"></a>Slet en projektmappe
Projektmapper kan fjernes. Men når du fjerner en projektmappe, fjerner du også alle rapporter og dashboardfelter, der indeholder data fra denne projektmappe.

Hvis projektmappen er gemt på OneDrive for Business, bliver denne ikke slettet fra OneDrive, når du sletter den fra Power BI.

### <a name="to-delete-a-workbook"></a>Sådan sletter du en projektmappe
1. Vælg fanen **Projektmapper** i dit arbejdsområde.
2. Find den projektmappe, du vil slette, og vælg sletteikonet :::image type="icon" source="media/service-delete/power-bi-delete-report2.png" border="false":::.

    ![Fanen Projektmapper](media/service-delete/power-bi-delete-workbooknew.png)
3. Bekræft sletningen.

   ![Dialogboksen Fjern projektmappe](media/service-delete/power-bi-delete-confirm.png)

## <a name="delete-a-dataset"></a>Slet et datasæt
Datasæt kan slettes. Når du sletter et datasæt, sletter du dog også alle rapporter og dashboardfelter, der indeholder data fra det pågældende datasæt.

Hvis et datasæt er en del af en eller flere [organisationsindholdspakker](../collaborate-share/service-organizational-content-pack-disconnect.md), kan du kun slette det ved at fjerne det fra de indholdspakker, hvor det bruges, vente på, at det bliver behandlet og derefter prøve at slette det igen.

### <a name="to-delete-a-dataset"></a>Sådan sletter du et datasæt
1. Vælg fanen **Datasæt** i dit arbejdsområde.
2. Find det datasæt, du vil slette, og vælg **Flere indstillinger** (...).  

    ![Fanen Datasæt](media/service-delete/power-bi-delete-datasetnew.png)
3. Vælg **Slet** på rullelisten.

   ![ellipsemenu](media/service-delete/power-bi-delete-datasetnew2.png)
4. Bekræft sletningen.

   ![Dialogboksen Slet dashboard](media/service-delete/power-bi-delete-dataset-confirm.png)

## <a name="delete-a-workspace"></a>Slet et arbejdsområde
> [!WARNING]
> Når du opretter et arbejdsområde, opretter du en Microsoft 365-gruppe. Og når du sletter et arbejdsområde, sletter du denne Microsoft 365-gruppe. Det betyder, at gruppen også slettes fra andre Microsoft 365-produkter, f.eks. SharePoint og Microsoft Teams.
>
>

Som forfatter af arbejdsområdet, kan du slette det. Når du sletter det, slettes den tilknyttede app også for alle gruppemedlemmer, og den fjernes fra din AppSource, hvis du har udgivet appen i hele organisationen. Det er ikke det samme at slette et arbejdsområde som at forlade et arbejdsområde.

### <a name="to-delete-a-workspace---if-you-are-an-admin"></a>Sådan sletter du et arbejdsområde – hvis du er administrator
1. Vælg **Arbejdsområder** i navigationsruden

2. Vælg **Flere indstillinger** (...) til højre for det arbejdsområde, der skal slettes, og vælg **Rediger arbejdsområde**.

    ![arbejdsområder](media/service-delete/power-bi-delete-workspace.png)

3. I vinduet **Rediger arbejdsområde** skal du vælge **Slet arbejdsområde** > **Slet**.

    ![slet arbejdsområde](media/service-delete/power-bi-delete-workspace2.png)

### <a name="to-remove-a-workspace-from-your-list"></a>Sådan fjerner du et arbejdsområde fra din liste
Hvis du ikke længere vil være medlem af et arbejdsområde, kan du ***forlade*** det, så fjernes det fra din liste. Selvom du forlader et arbejdsområde, har alle andre medlemmer af arbejdsområdet det stadig.  

> [!IMPORTANT]
> Hvis du er den eneste administrator af arbejdsområdet, tillader Power BI ikke, at du forlader det.
>
>

1. Start i det arbejdsområde, du vil fjerne.

2. Vælg **Flere indstillinger** (...) i øverste højre hjørne, og vælg **Forlad arbejdsområde** > **Forlad**.

      :::image type="icon" source="media/service-delete/power-bi-leave-workspace.png" border="false":::

   > [!NOTE]
   > De indstillinger, du kan se på rullelisten, afhænger af, om du er administrator eller medlem af det pågældende arbejdsområde.
   >
   >

## <a name="delete-or-remove-an-app"></a>Slet eller fjerne en app
Apps kan nemt fjernes fra din side med applisten. Det er dog kun appadministrator, der kan slette en app.

### <a name="remove-an-app-from-your-app-list-page"></a>Fjern en app fra din side med applisten
Selvom du sletter en app fra din side med applisten, slettes appen ikke for andre medlemmer.

1. Vælg **Apps** i navigationsruden for at åbne siden med applisten.
2. Hold over den app, du vil slette, og vælg sletteikonet :::image type="icon" source="media/service-delete/power-bi-delete-report2.png" border="false":::.

   ![vælg Apps](media/service-delete/power-bi-delete-app.png)

   Hvis du kommer til at fjerne en app ved et uheld, har du flere muligheder for at få den tilbage.  Du kan bede personen, der oprettede appen, om at sende den igen. Du kan finde den oprindelige mail med linket til appen. Du kan undersøge, om meddelelsen om appen stadig findes i [meddelelsescentret](../consumer/end-user-notification-center.md), eller du kan kontrollere din organisations [AppSource](../consumer/end-user-apps.md).

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding
Denne artikel indholdte oplysninger om, hvordan du sletter de større komponenter i Power BI-tjenesten. Men der er flere ting, du kan slette i Power BI.  

* [Fjern et udvalgt dashboard](../consumer/end-user-featured.md)
* [Fjern et dashboard fra favoritter](../consumer/end-user-favorite.md)
* [Slet en rapportside](service-delete.md)
* [Slet et dashboardfelt](service-dashboard-edit-tile.md)
* [Slet en rapportvisualisering](service-delete.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
