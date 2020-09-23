---
title: Integrer en rapport på Power BI-rapportserveren ved hjælp af en iFrame på SharePoint Server
description: Denne artikel viser, hvordan du integrerer en rapport fra Power BI-rapportserver i en iFrame i SharePoint Server
author: maggiesMSFT
ms.author: maggies
ms.date: 07/28/2020
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 9e639c4a22cc4e01c04374289026a7006f33143b
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861860"
---
# <a name="embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Integrer en rapport på Power BI-rapportserveren ved hjælp af en iFrame på SharePoint Server

I denne artikel får du mere at vide om, hvordan du integrerer en rapport fra Power BI-rapportserver ved hjælp af en iFrame på en SharePoint-side. Hvis du arbejder med SharePoint Online, skal Power BI-rapportserveren være offentligt tilgængelig. I SharePoint Online fungerer den Power BI-webdel, der fungerer med Power BI-tjenesten, ikke med Power BI-rapportserveren.  

![iFrame-eksempel](media/quickstart-embed/quickstart_embed_01.png)

## <a name="prerequisites"></a>Forudsætninger
* [Power BI-rapportserveren](https://powerbi.microsoft.com/report-server/) skal være installeret og konfigureret.
* [Power BI Desktop optimeret til Power BI-rapportserveren](install-powerbi-desktop.md) skal være installeret.
* Et [SharePoint 2013-, 2016- eller 2019-miljø](/sharepoint/install/install) installeret og konfigureret.
* Internet Explorer 11 understøttes kun, hvis dokumenttilstanden er angivet til IE11 (Edge), eller når du bruger SharePoint Online. Du kan bruge andre understøttede browsere med SharePoint i det lokale miljø og SharePoint Online.

## <a name="create-the-power-bi-report-url"></a>Opret URL-adressen til Power BI-rapporten

1. Download eksemplet fra GitHub: [Blogdemo](https://github.com/Microsoft/powerbi-desktop-samples). Vælg **Klon eller download**, og vælg derefter **Download ZIP**.

    ![Download PBIX-eksempelfilen](media/quickstart-embed/quickstart_embed_14.png)

2. Pak filen ud, og åbn .pbix-eksempelfilen i Power BI Desktop, der er optimeret til Power BI-rapportserver.

    ![Værktøjet PBI RS Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Gem rapporten på **Power BI-rapportserveren**. 

    ![Gem på PBI RS](media/quickstart-embed/quickstart_embed_03.png)

4. Få vist rapporten på webportalen til Power BI-rapportserveren.

    ![Webportal](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capture-the-url-parameter"></a>Hent parameteren for URL-adressen

Når du har URL-adressen, kan du oprette en iFrame på en SharePoint-side, der er vært for rapporten. For en hvilken som helst URL-adresse til en rapport fra Power BI-rapportserver skal du tilføje følgende parameter for en forespørgselsstreng for at integrere rapporten i en SharePoint iFrame: `?rs:embed=true`.

   Eksempel:
    ``` 
    https://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embed-the-report-in-a-sharepoint-iframe"></a>Integrer rapporten i en SharePoint iFrame

1. Naviger til en SharePoint-side med **webstedsindhold**.

    ![Siden Webstedsindhold](media/quickstart-embed/quickstart_embed_05.png)

2. Vælg den side, hvor du vil tilføje din rapport.

    ![App til siden Webstedsindhold](media/quickstart-embed/quickstart_embed_06.png)

3. Vælg tandhjulsikonet øverst til højre, og vælg derefter **Rediger side**.

    ![Indstillingen Rediger side](media/quickstart-embed/quickstart_embed_07.png)

4. Vælg **Tilføj en webdel**.

5. Under **Kategorier** skal du vælge **Medier og indhold**. Under **Dele** skal du vælge **Indholdseditor** og derefter vælge **Tilføj**.

    ![Vælg webdelen Indholdseditor](media/quickstart-embed/quickstart_embed_09.png)

6. Vælg **Klik her for at tilføje nyt indhold**.

7. Vælg **Formatér tekst** i den øverste menu, og vælg derefter **Rediger kilde**.

     ![Rediger kilde](media/quickstart-embed/quickstart_embed_11.png)

8. I vinduet **Rediger kilde** skal du indsætte iFrame-koden i **HTML-kilden** og derefter vælge **OK**.

    ![iFrame-kode](media/quickstart-embed/quickstart_embed_12.png)

     Eksempel:
     ```html
     <iframe width="800" height="600" src="https://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Vælg **Side** i den øverste menu, og vælg derefter **Stop redigering**.

    ![Stop redigering](media/quickstart-embed/quickstart_embed_13.png)

    Rapporten vises på siden.

    ![iFrame-eksempel](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Næste trin

- [Opret en Power BI-rapport til Power BI-rapportserveren](quickstart-create-powerbi-report.md).  
- [Opret en sideinddelt rapport til Power BI-rapportserveren](quickstart-create-paginated-report.md).  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/).