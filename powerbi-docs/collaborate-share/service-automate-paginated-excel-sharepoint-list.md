---
title: Eksportér en sideinddelt rapport for hver række i en Excel Online-tabel eller på en SharePoint-liste
description: I denne artikel skal du bruge Power Automate til at automatisere eksport af en sideinddelt rapport for hver række i en Excel Online-tabel eller på en SharePoint Online-liste.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: 7a48a9a594364de4261aa66de48c1a4262392364
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097840"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>Eksportér en sideinddelt rapport for hver række i en Excel Online-tabel eller på en SharePoint-liste

Med [Power Automate](/power-automate/getting-started) kan du automatisere eksport og distribution af sideinddelte Power BI-rapporter til en række understøttede formater og scenarier. I denne artikel bruger du en Power Automate-skabelon til at automatisere konfiguration af tilbagevendende eksporter eller flere sideinddelte rapporter. Du eksporterer dem i et ønsket format for hver række i en Excel Online-tabel eller på en SharePoint Online-liste. Du kan distribuere den eksporterede sideinddelte rapport til OneDrive for Business eller et SharePoint Online-websted, eller du kan sende den via mail i Office 365 Outlook.

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="Eksportér en sideinddelt rapport ved hjælp af en Excel Online-tabel.":::

Hver række i din Excel Online-tabel eller på din SharePoint Online-liste kan repræsentere en enkelt bruger, som skal modtage en sideinddelt rapport på abonnementsbasis. Eller hver række kan i stedet repræsentere en unik sideinddelt rapport, som du gerne vil distribuere. Din tabel eller liste kræver en kolonne, der angiver, hvordan du distribuerer en rapport, uanset om det er OneDrive, SharePoint Online eller Outlook. I Power Automate-flowet bruges denne kolonne i sin Skift-sætning.

Leder du efter andre Power Automate-skabeloner til sideinddelte Power BI-rapporter? Se [Eksportér sideinddelte Power BI-rapporter med Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Forudsætninger  

Hvis du vil følge med, skal du sørge for, at du har:

- Mindst ét arbejdsområde i din Power BI-lejer skal understøttes af en reserveret kapacitet. Denne kapacitet kan være en hvilken som helst af SKU'erne A4/P1-A6/P3. Læs mere om [reserverede kapaciteter til sideinddelte rapporter i Power BI Premium](../admin/service-premium-what-is.md#paginated-reports).
- Få adgang til standardforbindelser i Power Automate, som medfølger ethvert Office 365-abonnement.
- Hvis du bruger en Excel Online-tabel, skal den være formateret som en tabel i Excel. Se [Opret en tabel](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f) for at få vide, hvordan du gør det.

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>Eksportér en sideinddelt rapport for hver række i en tabel eller på en liste

> [!NOTE]
> Følgende trin og billeder viser konfigurationen af et flow ved hjælp af skabelonen **Eksportér en sideinddelt Power BI-rapport for hver række i en Excel Online-tabel**. Du kan følge de samme trin for at oprette et flow ved hjælp af skabelonen **Eksportér en sideinddelt Power BI-rapport for elementer på en SharePoint Online-liste**. I stedet for en Excel Online-tabel indeholder en SharePoint Online-liste oplysninger om, hvordan du eksporterer den sideinddelte rapport.  

1. Log på Power Automate på [flow.microsoft.com](https://flow.microsoft.com/). 
1. Vælg **Skabeloner**, og søg efter  **sideinddelte rapporter**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Skærmbillede af Power Automate-skabeloner til sideinddelte Power BI-rapporter.":::

1. Vælg skabelonen **Eksportér en sideinddelt Power BI-rapport for hver række i en Excel Online-tabel** eller **Eksportér en sideinddelt Power BI-rapport for elementer på en SharePoint Online-liste**. Sørg for, at du er logget på Excel Online, Power BI, OneDrive for Business, SharePoint Online og Office 365 Outlook. Vælg **Fortsæt**.  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="Eksportér en sideinddelt Power BI-rapport for hver række i en Excel Online-tabel.":::

1. Hvis du vil angive **Gentagelse** for dit flow, skal du vælge en indstilling under **Hyppighed** og angive den ønskede værdi for **Interval**.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="Vælg gentagelse for dit flow.":::

1. (Valgfri) Vælg **Vis avancerede indstillinger** for at angive yderligere parametre for **Gentagelse**, herunder **Tidszone**, **Starttidspunkt**, **På disse dage**, **På dette klokkeslæt** og **På dette minuttal**.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="Valgfrit – vælg avancerede indstillinger for gentagelse.":::

1. I feltet **Placering** skal du vælge OneDrive for Business eller det SharePoint Online-websted, hvor din Excel Online-tabel eller SharePoint Online-liste gemmes. Vælg derefter **Dokumentbiblioteket** på rullelisten.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="Vælg placeringen af Excel Online-tabellen.":::

1. Vælg Excel Online-filen eller SharePoint Online-listen i feltet **Filer**. Vælg navnet på tabellen eller listen på rullelisten i feltet **Tabel**. 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="Vælg Excel Online-filen og navnet på tabellen.":::

    > [!TIP]
    > Se [Opret en tabel](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f) for at få mere at vide om, hvordan du formaterer data som en tabel i Excel. 

1. Initialiser en variabel, der skal bruges til filnavnet. Du kan beholde eller ændre standardværdierne for **Navn** og **Værdi**, men lade **Type** svare til **Streng**.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="Udfyld Navn og Værdi, og lad Type svare til Streng.":::

1. Under **Anvend på hver** er feltet **Vælg output fra forrige trin** som standard angivet til **værdi**. Denne indstilling gentager de handlinger, der er indeholdt i **Anvend på hver** for hver række i din Excel Online-tabel eller på din SharePoint Online-liste.  

1. I feltet **Arbejdsområde** skal du vælge et arbejdsområde i en reserveret kapacitet. I feltet **Rapport** skal du vælge den sideinddelte rapport i det valgte arbejdsområde, du vil eksportere. Hvis du konfigurerer **Angiv en brugerdefineret værdi** på rullelisten, kan du konfigurere **Arbejdsområde** og **Rapport** til at svare til en kolonne i din Excel Online-tabel eller på din SharePoint Online-liste. Disse kolonner bør indeholde hhv. id'er for arbejdsområde og id'er for rapport.  

1. Vælg et **Eksportformat** på rullelisten, eller konfigurer det til at svare til en kolonne i din Excel Online-tabel, som indeholder de ønskede eksportformater. F.eks. PDF, DOCX eller PPTX. Alternativt kan du angive parametre for den sideinddelte rapport. Find detaljerede beskrivelser af parametrene i [connectorreferencen til REST-API til Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="Udfyld Eksportér til fil for sideinddelte rapporter.":::

1. I feltet **Værdi** skal du angive et navn på den sideinddelt rapport, når den er eksporteret. Sørg for at angive et filtypenavn. Du kan angive det statisk, f.eks. .pdf, .docx eller .pptx. Eller du kan angive det dynamisk ved at vælge kolonnen i din Excel-tabel, som svarer til dit ønskede eksportformat. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="Vælg navnet på rapporten og et filtypenavn.":::

1. I handlingen **Skift** skal du udfylde feltet **Til** med kolonnen i din Excel Online-tabel, som svarer til den ønskede leveringsmetode: **OneDrive**, **SharePoint** eller **Mail**. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="I Skift skal du udfylde feltet Til med kolonnen i din Excel Online-tabel.":::

1. I **Sag**, **Sag 2** og **Sag 3** skal du angive de værdier, der er i den Excel Online-tabel, som du valgte i forrige trin.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="Angiv værdier for Sag, Sag 2 og Sag 3.":::

1. Hvis du gemmer din sideinddelte rapport i OneDrive, skal du vælge den **Mappesti**, hvor den skal gemmes.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="Hvis du gemmer på OneDrive.":::

1. Hvis du gemmer din sideinddelte rapport i SharePoint Online, skal du angive den **Webstedsadresse** og **Mappesti**, hvor den skal gemmes. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="Hvis du gemmer din sideinddelte rapport i SharePoint Online.":::

1. Hvis du sender din sideinddelte rapport som en mail via Outlook, skal du udfylde felterne **Til**, **Emne** og **Brødtekst**. Disse felter kan indeholde statisk indhold eller dynamisk indhold fra din Excel Online-tabel eller SharePoint Online-liste. Med Power Automate vedhæftes din sideinddelte rapport til denne mail automatisk.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="Hvis du sender dine sideinddelte rapport som en mail via Outlook.":::

1. Når du er færdig, skal du vælge  **Næste trin** eller **Gem**. Med Power Automate oprettes og evalueres flowet, og du får besked, hvis der findes fejl. 

1. Hvis der er fejl, skal du vælge **Rediger flow** for at løse dem. Ellers skal du vælge pilen **Tilbage** for at få vist flowoplysningerne og køre det nye flow. 


## <a name="next-steps"></a>Næste trin

- [Eksportér sideinddelte Power BI-rapporter med Power Automate](service-automate-paginated-integration.md)
- [Kom godt i gang med Power Automate](/power-automate/getting-started/)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

