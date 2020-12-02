---
title: Brug dashboardtemaer i Power BI-tjenesten
description: Få mere at vide om, hvordan du bruger en brugerdefineret farvepalet og anvender den for et helt dashboard i Power BI-tjenesten
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 08/22/2018
LocalizationGroup: Create reports
ms.openlocfilehash: 9167a5931976cdcec710ee79b347fcd0f33ba378
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395296"
---
# <a name="use-dashboard-themes-in-power-bi-service"></a>Brug Dashboard-temaer i Power BI-tjenesten
Med **dashboardtemaer** kan du anvende et farvetema på hele dit dashboard, f.eks virksomhedens farver, sæsonmæssige farver eller andre farvetemaer, som du gerne vil anvende. Når du anvender et **dashboardtema**, bruges farver fra det valgte tema for alle visualiseringer på dashboardet (med nogle få undtagelser, der er beskrevet senere i denne artikel).

![eksempeldashboard med tema](media/service-dashboard-themes/power-bi-full-dashboard-theme.png)

Hvis du ændrer farverne i rapportvisualiseringerne på dashboardet, påvirker det ikke visualiseringerne i rapporten. Når du fastgør felter fra en rapport, hvor der allerede er [anvendt et rapporttema](desktop-report-themes.md), kan du vælge at beholde det aktuelle tema eller at bruge dashboardtemaet.


## <a name="prerequisites"></a>Forudsætninger
* [Åbn eksempeldashboardet Sales and Marketing](sample-datasets.md) for at følge med.


## <a name="how-dashboard-themes-work"></a>Sådan bruges dashboardtemaer
Åbn et dashboard, du har oprettet (eller har tilladelse til at redigere), og som du vil tilpasse. Vælg **Flere indstillinger** (...), og vælg **Dashboardtema**. 

![indstillingen dashboardtema](media/service-dashboard-themes/power-bi-dashboard-theme.png)

Vælg et af de medfølgende temaer i dashboardruden.  I eksemplet herunder har vi valgt **Dark**.

![Indstillingen Light valgt](media/service-dashboard-themes/power-bi-theme-menu.png)

![Indstillingen Dark anvendt](media/service-dashboard-themes/power-bi-theme-dark.png)

## <a name="create-a-custom-theme"></a>Opret et brugerdefineret tema

Standardtemaet til Power BI-dashboards er **Light**. Hvis du vil tilpasse farverne eller oprette dit eget tema, skal du vælge **Brugerdefineret** på rullelisten. 

![Vælg Brugerdefineret på rullelisten](media/service-dashboard-themes/power-bi-theme-custom.png)

Brug de brugerdefinerede indstillinger for at oprette dit eget dashboardtema. Hvis du tilføjer et baggrundsbillede, anbefaler vi, at billedet har en opløsning på mindst 1920 x 1080. Hvis du vil bruge et billede som baggrund, skal du uploade billedet til et offentligt websted, kopiere URL-adressen og indsætte den i feltet **URL-adresse til billede**. 

### <a name="using-json-themes"></a>Brug af JSON-temaer
En anden metode til at oprette et brugerdefineret tema er at uploade en JSON-fil, som indeholder indstillinger for alle de farver, du vil bruge i dit dashboard. I Power BI Desktop kan rapportoprettere bruge JSON-filer til [oprette temaer til rapporter](desktop-report-themes.md). De samme JSON-filer kan uploades til dashboards, eller du kan finde og uploade JSON-filer fra siden [Theme gallery](https://community.powerbi.com/t5/Themes-Gallery/bd-p/ThemesGallery) i Power BI-communityet 

![Webstedet Themes gallery](media/service-dashboard-themes/power-bi-theme-gallery.png)

Du kan også gemme dit brugerdefinerede tema som en JSON-fil og derefter dele den med andre dashboardoprettere. 

### <a name="use-a-theme-from-the-theme-gallery"></a>Brug et tema fra temagalleriet

Når temaet er uploadet, anvendes farverne automatisk på alle felterne i dashboardet. 

1. Peg på et tema, og vælg **Vis rapport**.

    ![Vis rapport](media/service-dashboard-themes/power-bi-choose-theme.png)

2. Rul ned, og find linket til JSON-filen.  Vælg downloadikonet, og gem filen.

    ![JSON-filen Spring Day](media/service-dashboard-themes/power-bi-theme-json.png)

3. Gå tilbage til vinduet Brugerdefineret dashboardtema i Power BI-tjenesten, og vælg **Upload JSON-tema**.

    ![Upload JSON](media/service-dashboard-themes/power-bi-upload-theme.png)

4. Gå til den placering, hvor du har gemt JSON-filen, og vælg **Åbn**.

5. Vælg **Gem** på dashboardtemasiden. Det nye tema anvendes på dit dashboard.

    ![nyt tema anvendt](media/service-dashboard-themes/power-bi-json.png)

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

* Hvis din rapport anvender et andet tema end dashboardtemaet, kan du styre, om det visuelle element skal bevare det aktuelle tema, eller om det skal anvende temaet for dashboardet for at give et ensartet udtryk på tværs af visuelle elementer fra forskellige kilder. Når du fastgør et felt på et dashboard, kan du vælge **Behold det aktuelle tema** for at bevare rapporttemaet. På dashboardet vil visualiseringen beholde rapporttemaet inklusive indstillingerne for gennemsigtighed. 

    Det eneste tidspunkt, hvor du får vist indstillingerne for **Felttemaer** er, når du opretter rapporten i Power BI Desktop, [tilføjer et rapporttema](desktop-report-themes.md) og derefter publicerer rapporten til Power BI-tjenesten. 

    ![Behold det aktuelle tema](media/service-dashboard-themes/power-bi-keep-current.png)

    Prøv at fastgøre feltet igen, og vælg **Brug dashboardtema**.

    ![Brug destinationstema](media/service-dashboard-themes/power-bi-use-destination.png)

* Dashboardtemaer kan ikke anvendes på fastgjorte dynamiske rapportsider, iframe-felter, SSRS-felter, projektmappefelter eller billeder.
* Dashboardtemaer kan ses på mobilenheder, men du kan kun oprette et dashboardtema i Power BI-tjenesten. 
* Brugerdefinerede dashboardtemaer virker kun med felter, der er fastgjort fra rapporter. 

