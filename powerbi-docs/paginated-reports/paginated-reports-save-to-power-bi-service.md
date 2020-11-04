---
title: Publicer en sideinddelt rapport i Power BI-tjenesten
description: I dette selvstudium lærer du at publicere en sideinddelt rapport i Power BI-tjenesten ved at uploade den fra din lokale computer.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 05/04/2020
ms.openlocfilehash: 28058161672de9db0cac5093e652e1d551f6a80a
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297312"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Publicer en sideinddelt rapport i Power BI-tjenesten

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

I denne artikel lærer du om publicering af en sideinddelt rapport i Power BI-tjenesten ved at uploade den fra din lokale computer. Du kan uploade sideinddelte rapporter til Mit arbejdsområde eller andre arbejdsområder, så længe arbejdsområdet er i en Premium-kapacitet. Se efter rombeikonet ![Rombeikon for Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ud for navnet på arbejdsområdet. 

Hvis din datakilde til rapporten er i det lokale miljø, skal du oprette en gateway, når du har uploadet rapporten. Se afsnittet [Opret en gateway](#create-a-gateway) senere i denne artikel.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Føj et arbejdsområde til en Premium-kapacitet

Hvis arbejdsområdet ikke har rombeikonet ![Rombeikon for Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ud for navnet, skal du føje arbejdsområdet til en Premium-kapacitet. 

1. Vælg **Arbejdsområder** , vælg ellipsen ( **...** ) ud for navnet på arbejdsområdet, og vælg derefter **Rediger arbejdsområde**.

    ![Vælg Rediger arbejdsområde](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. I dialogboksen **Rediger arbejdsområde** skal du udvide **Avanceret** og derefter sørge for, at indstillingen **Dedikeret kapacitet** er angivet til **Til**.

    ![Vælg Dedikeret kapacitet](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Du kan muligvis ikke kan ændre den. Hvis ikke, skal du kontakte administratoren af Power BI Premium-kapacitet for at får tildelt rettigheder, så du kan føje dit arbejdsområde til en Premium-kapacitet.

## <a name="from-report-builder-publish-a-paginated-report"></a>Udgiv en sideinddelt rapport fra Power BI Report Builder

1. Opret din sideinddelte rapport i Report Builder, og gem den på din lokale computer.

1. I menuen **Filer** i Power BI Report Builder skal du vælge **Gem som**.

    ![Menuen Filer > Gem > Gem som](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Hvis du ikke er logget på Power BI endnu, skal du logge på eller oprette en konto nu. I øverste højre hjørne af Power BI Report Builder skal du vælge **Log på** og udføre trinnene.

2. På listen over arbejdsområder til venstre skal du vælge et arbejdsområde med diamantikonet ![diamantikon for Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ud for navnet. Skriv et **filnavn** i feltet > **Gem**. 

    ![Vælg et Premium-arbejdsområde](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Åbn Power BI-tjenesten i en browser, og gå til arbejdsområdet Premium, hvor du udgav den sideinddelte rapport. Under fanen **Rapporter** kan du se din rapport.

    ![Sideinddelt rapport på listen Rapporter](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Vælg den sideinddelte rapport for at åbne den i Power BI-tjenesten. Hvis den indeholder parametre, skal du vælge dem, før du kan få vist rapporten.

    ![Vælg parametre](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Hvis din rapportdatakilde er i det lokale miljø, kan du læse om, hvordan du [opretter en gateway](#create-a-gateway) i denne artikel for at få adgang til datakilden.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>Overfør en sideinddelt rapport fra Power BI-tjenesten

Du kan også starte fra Power BI-tjenesten og overføre en sideinddelt rapport.

1. Opret din sideinddelte rapport i Report Builder, og gem den på din lokale computer.

1. Åbn Power BI-tjenesten i en browser, og gå til arbejdsområdet Premium, hvor du vil publicere rapporten. Se efter rombeikonet ![Rombeikon for Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ud for navnet. 

1. Vælg **Hent data**.

    ![Power BI – Hent data](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Vælg **Hent** i feltet **Filer**.

    ![Power BI Hent filer](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Vælg **Lokal fil** > gå til den sideinddelte rapport > **Åbn**.

    ![Vælg Lokal fil](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Vælg **Fortsæt** > **Rediger legitimationsoplysninger**.

    ![Vælg Rediger legitimationsoplysninger](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Konfigurer dine legitimationsoplysninger > **Log på**.

    ![Rediger legitimationsoplysninger](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Under fanen **Rapporter** kan du se din rapport.

    ![Sideinddelt rapport på listen Rapporter](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Vælg den for at åbne den i Power BI-tjenesten. Hvis den indeholder parametre, skal du vælge dem, før du kan få vist rapporten.
 
    ![Vælg parametre](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Hvis din rapportdatakilde er i det lokale miljø, kan du læse om, hvordan du [opretter en gateway](#create-a-gateway) i denne artikel for at få adgang til datakilden.

## <a name="create-a-gateway"></a>Opret en gateway

Ligesom alle andre Power BI-rapporter skal du oprette eller oprette forbindelse til en gateway til at få adgang til dataene, hvis datakilden for rapporten er i det lokale miljø.

1. Ud for navnet på rapporten, skal du vælge **Administrer**.

   ![Administrer den sideinddelte rapport](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Du kan se yderligere oplysninger og næste trin i artiklen [Hvad er en datagateway i det lokale miljø](../connect-data/service-gateway-onprem.md) til Power BI-tjenesten.



## <a name="next-steps"></a>Næste trin

- [Publicer en sideinddelt rapport i Power BI-tjenesten](../consumer/paginated-reports-view-power-bi-service.md)
- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [Selvstudium: Integrer sideinddelte Power BI-rapporter i et program til dine kunder](../developer/embedded/embed-paginated-reports-customers.md)
