---
title: Slet et dashboard, en rapport, en projektmappe, et datasæt eller et arbejdsområde
description: Få mere at vide om, hvordan du sletter næsten alt fra Power BI-tjenesten.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/29/2020
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 1e1cc55f21f43b7029a68670d9a7af9215f5b62c
ms.sourcegitcommit: 8861dac6724202a5b3be456a6aff8f3584e0cccf
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132442"
---
# <a name="delete-almost-anything-in-the-power-bi-service"></a>Slet næsten alt i Power BI-tjenesten
I denne artikel får du mere at vide om, hvordan du sletter et dashboard, en rapport, en projektmappe, et datasæt, en app eller et arbejdsområde i Power BI-tjenesten. Du kan slette næsten alt i Power BI-tjenesten med nogle få undtagelser. 

## <a name="delete-a-dashboard-report-dataset-or-workbook"></a>Slet et dashboard, en rapport, et datasæt eller en projektmappe

1. Vælg fanen **Alle** i dit arbejdsområde.
1. Vælg **Flere indstillinger (...)** ved siden af det aktiv, du vil slette, og vælg **Slet**.

    ![Skærmbillede af Vælg flere indstillinger og derefter valg af Slet.](media/service-delete/power-bi-delete-dashboard.png)

1. Vælg **Slet** for at bekræfte sletningen.

## <a name="remove-an-app-from-your-app-list-page"></a>Fjern en app fra din side med applisten

Du kan nemt fjerne apps fra din side med applisten. Hvis du fjerner en app, slettes appen ikke for andre medlemmer. Det er kun en administrator eller et medlem af et arbejdsområde, der kan slette appen permanent fra arbejdsområdet.

1. Vælg **Apps** i navigationsruden for at åbne siden med applisten.
2. Hold over den app, du vil slette, og vælg sletteikonet :::image type="icon" source="media/service-delete/power-bi-delete-report2.png" border="false":::.

   ![Skærmbillede af udvalgte apps.](media/service-delete/power-bi-delete-app.png)

   Hvis du kommer til at fjerne en app ved et uheld, har du flere muligheder for at få den tilbage.  Du kan bede personen, der oprettede appen, om at sende den igen. Du kan finde den oprindelige mail med linket til appen. Du kan undersøge, om meddelelsen om appen stadig findes i [meddelelsescentret](../consumer/end-user-notification-center.md), eller du kan kontrollere din organisations [AppSource](../consumer/end-user-apps.md).

## <a name="remove-or-delete-a-workspace"></a>Fjern eller slet et arbejdsområde

Power BI har to forskellige typer arbejdsområder: de originale eller *klassiske* arbejdsområder og de nye arbejdsområder. Processerne til at fjerne eller slette dem er forskellige. Læs mere om [nye og klassiske arbejdsområder](../collaborate-share/service-new-workspaces.md).

### <a name="remove-members-from-a-new-workspace"></a>Fjern medlemmer fra et nyt arbejdsområde

Det er kun arbejdsområdeadministratorer, der kan fjerne personer fra et nyt arbejdsområde. Hvis du er administrator, kan du fjerne dig selv eller enhver anden. Hvis du er den eneste administrator for et arbejdsområde, kan du dog ikke fjerne dig selv i Power BI.

1. Vælg **Få adgang til** i øverste højre hjørne i visningslisten i arbejdsområdet.

    :::image type="content" source="media/service-delete/power-bi-select-access.png" alt-text="Skærmbillede af valg af Adgang.":::

1. I ruden **Adgang** skal du vælge **Flere indstillinger (...)** ud for navnet på den person, du vil fjerne, og vælge **Fjern**.

    :::image type="content" source="media/service-delete/power-bi-access-remove.png" alt-text="Skærmbillede af ruden Adgang og valg af Fjern.":::

### <a name="delete-a-new-workspace"></a>Slet et nyt arbejdsområde

Når du opretter et af de *nye arbejdsområder* , opretter du ikke en tilknyttet Microsoft 365-gruppe. Hvis du er administrator af arbejdsområdet, kan du slette et nyt arbejdsområde uden at påvirke Microsoft 365-grupper. Læs mere om [nye og klassiske arbejdsområder](../collaborate-share/service-new-workspaces.md).

Som administrator for et arbejdsområde kan du slette det eller fjerne andre fra det. Når du sletter det, slettes den tilknyttede app også for alle gruppemedlemmer, og appen fjernes fra AppSource. 

1. Vælg **Arbejdsområder** i navigationsruden

2. Vælg **Flere indstillinger** (...) til højre for det arbejdsområde, der skal slettes, og vælg **Indstillinger for arbejdsområde**.

    ![Skærmbillede af Flere indstillinger og valg af Indstillinger for arbejdsområde.](media/service-delete/power-bi-delete-workspace.png)

3. I ruden **Indstillinger for arbejdsområde** skal du vælge **Slet arbejdsområde** > **Slet**.

### <a name="remove-a-classic-workspace-from-your-list"></a>Fjern et klassisk arbejdsområde fra din liste

Hvis du ikke længere vil være medlem af et klassisk arbejdsområde, kan du * *_forlade_* _ det, hvorefter det fjernes fra din liste. Selvom du forlader et arbejdsområde, har alle andre medlemmer af arbejdsområdet det stadig.  

> [!NOTE]
> Hvis du er den eneste administrator af arbejdsområdet, tillader Power BI ikke, at du forlader det.
>

1. Start i det arbejdsområde, du vil fjerne.

2. Vælg _ *Flere indstillinger* * (...) i øverste højre hjørne, og vælg **Forlad arbejdsområde** > **Forlad**.

      :::image type="content" source="media/service-delete/power-bi-leave-workspace.png" alt-text="Skærmbillede af Flere indstillinger, Forlad arbejdsområde.":::

   > [!NOTE]
   > De indstillinger, du kan se på rullelisten, afhænger af, om du er administrator eller medlem af det pågældende arbejdsområde.
   >

### <a name="delete-a-classic-workspace"></a>Slet et klassisk arbejdsområde

> [!WARNING]
> Når du opretter et *klassisk* arbejdsområde, opretter du en Microsoft 365-gruppe. Når du sletter et klassisk arbejdsområde, sletter du den pågældende Microsoft 365-gruppe. Gruppen slettes også fra andre Microsoft 365-produkter, f.eks. SharePoint og Microsoft Teams.
> 

Det er ikke det samme at slette et arbejdsområde som at forlade et arbejdsområde. Du skal være administrator af arbejdsområdet for at slette det. Når du sletter det, slettes den tilknyttede app også for alle gruppemedlemmer og fjernes fra AppSource. Hvis du er den eneste administrator for et arbejdsområde, så kan du dog ikke fjerne dig selv i Power BI.

1. Vælg **Arbejdsområder** i navigationsruden.

2. Vælg **Flere indstillinger (...)**  > **Indstillinger for arbejdsområde** ud for det arbejdsområde, der skal slettes.

    ![Skærmbillede af indstillinger for arbejdsområde.](media/service-delete/power-bi-workspace-settings-classic.png)

3. Vælg **Slet arbejdsområde** i vinduet **Indstillinger** , og bekræft derefter **sletningen**.

    ![Skærmbillede af Slet arbejdsområde.](media/service-delete/power-bi-delete-classic-workspace.png)


## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

- Når du fjerner et *dashboard* , sletter du ikke det underliggende datasæt eller de rapporter, der er knyttet til dette dashboard.
- Hvis du er *ejer af et dashboard eller en rapport* , kan du fjerne det. Hvis du har delt dashboardet med kolleger, fjernes det også fra deres arbejdsområder i Power BI, hvis du fjerner det fra dit eget arbejdsområde i Power BI.
- Hvis et *dashboard eller en rapport er delt med dig* , kan du ikke fjerne dashboardet.
- Når du sletter en rapport, bliver det datasæt, som rapporten er baseret på, ikke slettet.  Alle visualiseringer, som du har fastgjort til et dashboard fra rapporten, er også sikre. De forbliver på dashboardet, indtil du sletter dem individuelt.
- Du kan slette et *datasæt*. Når du sletter et datasæt, sletter du dog også alle rapporter og dashboardfelter, der indeholder data fra det pågældende datasæt.
- Du kan fjerne *projektmapper*. Men når du fjerner en projektmappe, fjerner du også alle rapporter og dashboardfelter, der indeholder data fra denne projektmappe. Hvis en projektmappe er gemt på OneDrive for Business, bliver den ikke slettet fra OneDrive, når du sletter den fra Power BI.
- Hvis et *dashboard eller en rapport* er en del af en [organisations indholdspakke](../collaborate-share/service-organizational-content-pack-disconnect.md), kan du ikke slette den ved hjælp af denne metode.  Se [Fjern din forbindelse til en organisationsindholdspakke](../collaborate-share/service-organizational-content-pack-disconnect.md).
- Hvis et *datasæt* er en del af en eller flere organisationsindholdspakker, kan du kun slette det ved at fjerne det fra de indholdspakker, hvor det bruges, vente på, at det bliver behandlet og derefter prøve at slette det igen.

## <a name="next-steps"></a>Næste trin

Denne artikel indeholdte oplysninger om, hvordan du sletter de større komponenter i Power BI-tjenesten. Her er nogle andre ting, du også kan slette.  

- [Fjern et udvalgt dashboard](../consumer/end-user-featured.md)
- [Fjern et dashboard fra favoritter](../consumer/end-user-favorite.md)
- [Slet et dashboardfelt](service-dashboard-edit-tile.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)