---
title: Gem en sideinddelt rapport i OneDrive for Business eller SharePoint Online
description: I denne artikel bruger du Power Automate til at automatisere lagring af en sideinddelt Power BI-rapport til OneDrive for Business eller en SharePoint Online-mappe.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 6aaad48fb3e97aa6c1b4fc51834ee593a49a8192
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097725"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>Gem en sideinddelt rapport i OneDrive for Business eller SharePoint Online

Med [Power Automate](/power-automate/getting-started) kan du automatisere eksport og distribution af sideinddelte Power BI-rapporter til en række understøttede formater og scenarier. I denne artikel bruger du Power Automate til at automatisere lagring af en sideinddelt Power BI-rapport til OneDrive for Business eller en SharePoint Online-mappe.


:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="Skærmbillede af Power Automate-flowet til lagring af en sideinddelt rapport i OneDrive eller SharePoint Online":::

Leder du efter andre Power Automate-skabeloner til sideinddelte Power BI-rapporter? Se [Eksportér sideinddelte Power BI-rapporter med Power Automate](service-automate-paginated-integration.md). 

## <a name="prerequisites"></a>Forudsætninger  

Hvis du vil følge med, skal du sørge for, at du har:

- Mindst ét arbejdsområde i din Power BI-lejer skal understøttes af en reserveret kapacitet. Denne kapacitet kan være en hvilken som helst af SKU'erne A4/P1-A6/P3. Læs mere om [reserverede kapaciteter til sideinddelte rapporter i Power BI Premium](../admin/service-premium-what-is.md#paginated-reports)
- Få adgang til standardforbindelser i Power Automate, som medfølger ethvert Office 365-abonnement.

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>Gem en sideinddelt rapport i OneDrive for Business eller en SharePoint Online-mappe 

Men en hvilken som helst af disse skabeloner konfigurerer du tilbagevendende eksporter af en sideinddelt rapport i et ønsket format til OneDrive for Business eller en SharePoint Online-mappe. Se forudsætningerne, hvis det er første gang, du bruger handlingen Eksportér til fil for sideinddelte rapporter i et Power Automate-flow. 

> [!NOTE]
> Følgende trin og billeder viser konfigurationen af et flow ved hjælp af skabelonen **Gem en sideinddelt Power BI-rapport i OneDrive for Business**. Følg de samme trin for at oprette et flow ved hjælp af skabelonen **Gem en sideinddelt Power BI-rapport i en SharePoint Online-mappe**. Når du vælger, hvor du vil eksportere din sideinddelte rapport til, skal du vælge en SharePoint Online-mappe i stedet for en OneDrive for Business-mappe. 

1. Log på Power Automate på [flow.microsoft.com](https://flow.microsoft.com/). 
1. Vælg **Skabeloner**, og søg efter  **sideinddelte rapporter**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Skærmbillede af Power Automate-skabeloner til sideinddelte Power BI-rapporter.":::

1. Vælg **Gem en sideinddelt Power BI-rapport i OneDrive for Business** eller **Gem en sideinddelt Power BI-rapport i en SharePoint Online-mappe**. Sørg for, at du er logget på Power BI og OneDrive for Business eller SharePoint Online.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="Skærmbillede af valg af skabelonen til Power BI og OneDrive for Business.":::
1. Vælg **Fortsæt**.  


1. Hvis du vil angive **Gentagelse** for dit flow, skal du vælge en indstilling under **Hyppighed** og angive den ønskede værdi for **Interval**.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="valg af gentagelse for flowet.":::

1. (Valgfri) Vælg **Vis avancerede indstillinger** for at angive yderligere parametre for **Gentagelse**, herunder **Tidszone**, **Starttidspunkt**, **På disse dage**, **På dette klokkeslæt** og **På dette minuttal**.  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="visning af avancerede indstillinger for gentagelse.":::

1. I feltet **Arbejdsområde** skal du vælge et arbejdsområde i en reserveret kapacitet. I feltet **Rapport** skal du vælge den sideinddelte rapport i det valgte arbejdsområde, du vil eksportere. I feltet **Eksportformat** skal du vælge det ønskede eksportformat. Alternativt kan du angive parametre for den sideinddelte rapport. Find detaljerede beskrivelser af parametrene i [connectorreferencen til REST-API til Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="valg af den sideinddelte rapport, arbejdsområde og eksportformat.":::

1. Under **Mappesti** skal du vælge den OneDrive for Business- eller SharePoint Online-mappe, som du vil eksportere din sideinddelte rapport til.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="valg af destination og oprettelse af filen.":::

1. I Power Automate genereres et **filnavn** og **filindholdet** automatisk for dig. Du kan ændre filnavnet, men beholde den dynamisk genererede værdi for **filindhold**. 

1. Når du er færdig, skal du vælge  **Næste trin** eller **Gem**. Med Power Automate oprettes og evalueres flowet, og du får besked, hvis der findes fejl. 

1. Hvis der er fejl, skal du vælge **Rediger flow** for at løse dem. Ellers skal du vælge pilen **Tilbage** for at få vist flowoplysningerne og køre det nye flow. 

    Når du kører flowet, eksporterer Power Automate en sideinddelt rapport i den angivne format til OneDrive for Business eller SharePoint Online.  

## <a name="next-steps"></a>Næste trin

- [Eksportér sideinddelte Power BI-rapporter med Power Automate](service-automate-paginated-integration.md)
- [Kom godt i gang med Power Automate](/power-automate/getting-started/)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
