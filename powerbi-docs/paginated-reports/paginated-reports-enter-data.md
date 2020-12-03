---
title: Angiv data direkte i en sideinddelt rapport i Report Builder
description: I denne artikel kan se du, hvordan du kan angive data direkte i en sideinddelt rapport i Report Builder.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 07/10/2020
ms.openlocfilehash: 5719a5d6e8f559f1dba9f87bc9937ed925195072
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418204"
---
# <a name="enter-data-directly-in-a-paginated-report-in-report-builder---power-bi"></a>Angiv data direkte i en sideinddelt rapport i Report Builder – Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

I denne artikel får du mere at vide om en funktion i den nye version af Microsoft Power BI Report Builder, som gør det muligt at angive data direkte i en RDL-rapport som et integreret datasæt.  Denne funktion er magen til Power BI Desktop. Du kan skrive data direkte i et datasæt i din rapport eller indsætte dem vha. et andet program, f.eks. Microsoft Excel. Når du har oprettet et datasæt ved at angive data, kan du bruge det på præcis samme måde, som du ville bruge alle andre integrerede datasæt, du har oprettet. Du kan desuden tilføje mere end én tabel og bruge én som et filter for den anden. Denne funktion er især nyttig til små, statiske datasæt, som du evt. vil bruge i din rapport, f.eks. rapportparametre.
 
## <a name="prerequisites"></a>Forudsætninger

- Du angiver data direkte i en sideinddelt rapport ved at [downloade og installere Power BI Report Builder](https://aka.ms/pbireportbuilder). 
- Hvis du vil gemme din sideinddelte rapport i Power BI-tjenesten, skal du bruge en [Power BI Pro-konto](../fundamentals/service-self-service-signup-for-power-bi.md) og have skriveadgang til et arbejdsområde i en [Power BI Premium-kapacitet](../admin/service-premium-what-is.md).
- Hvis du vil gemme din sideinddelte rapport på en rapportserver, skal du have tilladelse til at [redigere filen RsReportServer.config](#upload-the-paginated-report-to-a-report-server).

## <a name="create-a-data-source-and-dataset"></a>Opret en datakilde og et datasæt

Når du har downloadet og installeret Report Builder, skal du benytte samme arbejdsproces, som du bruger til at føje en integreret datakilde og et datasæt til din rapport. I følgende procedure kan du under **Datakilder** se en ny indstilling: **Angiv data**.  Du behøver kun at konfigurere denne datakilde én gang i en rapport. Derefter kan du oprette flere tabeller med angivne data som separate datasæt, der alle anvender denne enkelte datakilde.

1. I ruden **Rapportdata** skal du vælge **Nyt** > **datasæt**.

    ![Skærmbillede af Nyt datasæt i Report Builder.](media/paginated-reports-enter-data/paginated-new-dataset.png)

1. I dialogboksen **Egenskaber for datasæt** skal du vælge **Brug et datasæt, der er integreret i min rapport**.

1. Ud for **Datakilde** skal du vælge **Ny**.

    ![Skærmbillede af Ny integreret datakilde.](media/paginated-reports-enter-data/paginated-new-data-source.png)

1. I dialogboksen **Egenskaber for datakilde** skal du vælge **Brug en forbindelse, der er integreret i min rapport**.
2. I dialogboksen **Vælg forbindelsestype** skal du vælge **ANGIV DATA** > **OK**.

    ![Skærmbillede af ANGIV DATA i datakilde.](media/paginated-reports-enter-data/paginated-data-source-properties-enter-data.png)

1. Tilbage i dialogboksen **Egenskaber for datasæt** skal du vælge **Forespørgselsdesigner**.
2. I ruden **Forespørgselsdesigner** skal du højreklikke og indsætte dataene i tabellen.

    ![Skærmbillede af Angiv data i Forespørgselsdesigner.](media/paginated-reports-enter-data/paginated-enter-data.png)

1. Hvis du vil angive kolonnenavnene, skal du dobbeltklikke på hver **NewColumn** og angive kolonnenavnet.

    ![Skærmbillede af Angiv kolonnenavne.](media/paginated-reports-enter-data/paginated-column-name.png)

1. Hvis den første række indeholder kolonneoverskrifter fra de oprindelige data, skal du højreklikke og slette dem.
    
9. Datatypen for hver kolonne er som standard Streng. Hvis du vil ændre datatypen, skal du højreklikke på kolonneoverskriften > **Ændringstype** og angive den til en anden datatype, f.eks Dato eller Flydende.

    ![Skærmbillede af Skift datatype.](media/paginated-reports-enter-data/paginated-data-type.png)

1. Når du er færdig med at oprette tabellen, skal du vælge **OK**.  

    Den forespørgsel, der oprettes, er den samme, som du vil se med en XML-datakilde. Under overfladen bruger vi XML som dataprovider.  Vi har ændret den for også at muliggøre dette scenarie.

    ![Skærmbillede af XML-datastruktur.](media/paginated-reports-enter-data/paginated-xml-data.png)

12. I dialogboksen **Egenskaber for datasæt** skal du vælge **OK**.

13. Du kan se din datakilde og dit datasæt i ruden **Rapportdata**.

    ![Skærmbillede af Datasæt i ruden Rapportdata.](media/paginated-reports-enter-data/paginated-report-data-pane.png)

Du kan bruge dit datasæt som grundlag for datavisualiseringer i din rapport. Du kan også tilføje et andet datasæt og bruge den samme datakilde til det.

## <a name="design-the-report"></a>Design rapporten

Nu, hvor du har en datakilde og et datasæt, er du klar til at oprette din rapport. Med følgende procedure oprettes en enkel rapport baseret på dataene i forrige afsnit.

1. I menuen **Indsæt** skal du vælge **Tabel** > **Guiden Tabel**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-table-wizard.png" alt-text="Skærmbillede af valg af indstillingen Guiden Tabel.":::

1. Vælg det datasæt, du lige har oprettet > **Næste**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-choose-dataset.png" alt-text="Skærmbillede af dialogboksen Vælg et datasæt.":::

2.  Træk de felter, du vil gruppere efter, i boksen **Tilgængelige felter** til boksen **Rækkegrupper** på siden Arranger felter. I dette eksempel:

    - CountryRegion
    - SalesYear

3.  Træk de felter, du vil samle, fra boksen **Tilgængelige felter** til boksen **Værdier**. I dette eksempel:

    - Salgsbeløb

    Report Builder opsummerer som standard felterne i boksen **Værdier**, men du kan vælge en anden sammenlægning.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-select-aggregation.png" alt-text="Skærmbillede af forskellige sammenlægninger, du kan vælge imellem.":::
 
1. Vælg **Næste**.
4.  På siden **Vælg layout** skal du beholde alle standardindstillingerne, men rydde **Vis/skjul grupper**. Det er generelt en god idé at udvide og skjule grupper, men denne gang vil vi gerne se alle dataene.

5.  Vælg **Næste** > **Afslut**. Tabellen vises i designområdet.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-design-view-matrix.png" alt-text="Skærmbillede af rapporten i Designvisning.":::

### <a name="run-the-report"></a>Kør rapporten

Hvis du vil se de faktiske værdier og få forhåndsvist rapporten, skal du køre den.

1. Vælg **Kør** på båndet **Hjem**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-run-report.png" alt-text="Skærmbillede af valg af Kør på båndet Hjem.":::

    Nu kan du se værdierne. Matrixen har flere rækker, end du så i Designvisning.  Du kan enten formatere siden eller vælge at bruge standardindstillingerne, før du gemmer på din lokale computer eller publicerer til tjenesten.

1. Vælg **Udskriftslayout** for at se, hvordan rapporten vil se ud, når du udskriver den.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-select-print.png" alt-text="Skærmbillede af valg af Udskriftslayout.":::

    Nu kan du se den, som den vil se ud på en trykt side.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-print-layout.png" alt-text="Skærmbillede af rapporten i visningen Udskriftslayout.":::

## <a name="upload-the-paginated-report-to-the-power-bi-service"></a>Upload den sideinddelte rapport i Power BI-tjenesten

Nu, hvor sideinddelte rapporter understøttes i Power BI-tjenesten, kan du uploade din sideinddelte rapport til en Premium-kapacitet. Se flere detaljer under [Upload en sideinddelt rapport](paginated-reports-save-to-power-bi-service.md).

## <a name="upload-the-paginated-report-to-a-report-server"></a>Upload den sideinddelte rapport til en rapportserver

Du kan også uploade din sideinddelte rapport til en Power BI-rapportserver eller SQL Server Reporting Services 2016- eller 2017-rapportserver. Inden du gør det, skal du føje følgende element til din RsReportServer.config som en ekstra dataudvidelse. Sikkerhedskopiér din RsReportServer.config-fil, inden du foretager ændringen, i tilfælde af, at støder på problemer.

```xml
<Extension Name="ENTERDATA" Type="Microsoft.ReportingServices.DataExtensions.XmlDPConnection,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <ConfigName>ENTERDATA</ConfigName>
    </Configuration>
</Extension>
```

Når du har redigeret den, bør listen over dataudbydere se ud som følger i config-filen:

![Skærmbillede af konfigurationsfilen RsReportServer.](media/paginated-reports-enter-data/paginated-rsreportserver-config-file.png)

Det var det. Du kan nu publicere rapporter, der bruger denne nye funktionalitet til rapportserveren.

## <a name="next-steps"></a>Næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [Hvad er Power BI-rapportserveren?](../report-server/get-started.md)
