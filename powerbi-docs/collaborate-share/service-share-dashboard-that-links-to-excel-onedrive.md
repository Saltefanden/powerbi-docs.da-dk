---
title: Del dashboards, der er knyttet til en Excel-fil på OneDrive – Power BI
description: Læs om deling af dashboards, der er tilknyttet en Excel-projektmappe på OneDrive for Business, med felter, der er fastgjort fra den projektmappe.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 08/02/2018
LocalizationGroup: Share your work
ms.openlocfilehash: ee70a90ee104f1144595bd346b85d858f0aed49f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411580"
---
# <a name="share-a-power-bi-dashboard-that-links-to-an-excel-file-in-onedrive"></a>Del et Power BI-dashboard, der linker til en Excel-fil i OneDrive
I Power BI kan du [oprette forbindelse til Excel-projektmapper på OneDrive for Business](../connect-data/service-excel-workbook-files.md) og fastgøre felter til et dashboard fra den projektmappe. Når du deler det dashboard eller opretter en indholdspakke, der indeholder dette dashboard:

* Dine kollegaer kan få vist felterne uden at have tilladelser til selve projektmappen. Så du kan oprette en indholdspakke og vide, at dine kollegaer kan se de felter, der er oprettet ud fra Excel-projektmappen på OneDrive.
* Når du klikker på feltet, åbnes projektmappen i Power BI. Projektmappen åbnes kun, hvis dine kollegaer som minimum har [læserettigheder](https://support.office.com/article/Share-documents-or-folders-in-Office-365-1fe37332-0f9a-4719-970e-d2578da4941c) til projektmappen i OneDrive for Business.

## <a name="share-a-dashboard-that-contains-workbook-tiles"></a>Del et dashboard, der indeholder projektmappefelter
Hvis du vil dele et dashboard, der har en linker tilbage til en Excel-projektmappe på OneDrive for Business, kan du se [Del et dashboard](service-share-dashboards.md). Forskellen er, at du har mulighed for at ændre tilladelserne for den sammenkædede Excel-projektmappe, før du deler.

  ![Dialogboksen Del dashboard](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_share_workbk.png)

1. Angiv mailadressen til dine kollegaer.
2. Hvis du vil gøre det muligt for dine kollegaer at få vist Excel-projektmappen fra Power BI, skal du vælge **Gå til OneDrive for Business for at angive tilladelser til projektmappen**.
3. På OneDrive kan du [ændre tilladelserne](https://support.office.com/article/Share-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) efter behov.
4. Vælg **Del**.

>[!NOTE]
>Dine kollegaer vil ikke kunne fastgøre yderligere felter fra denne projektmappe eller foretage ændringer til Excel-projektmappen fra Power BI.
> 
> 

## <a name="create-an-organizational-content-pack-with-a-dashboard-that-contains-workbook-tiles"></a>Opret en organisationsindholdspakke med et dashboard, der indeholder projektmappefelter
Når du [publicerer en indholdspakke](service-organizational-content-pack-create-and-publish.md), giver du adgang til individuelle kollegaer eller grupper. Når du publicerer en indholdspakke, der indeholder projektmappelinks, får du mulighed for at ændre tilladelserne for den sammenkædede Excel-projektmappe før publicering.

1. På skærmbilledet **Opret indholdspakke** kan du angive mailadresser, give indholdspakken en titel og en beskrivelse og uploade et billede.
2. Vælg det dashboard og/eller den rapport, der er sammenkædet med Excel-projektmappen i OneDrive for Business.
   
    ![Excel-projektmappe i en indholdspakke](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_contpack_workbk.png)
3. Vælg **Gå til OneDrive for Business for at angive tilladelser til projektmappen**.
4. På OneDrive kan du [ændre tilladelserne](https://support.office.com/article/Share-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) efter behov.
5. Vælg **Publicer**.

## <a name="share-a-dashboard-from-a-power-bi-workspace"></a>Del et dashboard fra et arbejdsområde i Power BI
Deling af et dashboard fra et Power BI-arbejdsområde ligner deling af et dashboard fra dit eget arbejdsområde, bortset fra at filerne er placeret i et Microsoft 365-arbejdsområde i stedet for din private OneDrive for Business. Rediger tilladelserne til Excel-projektmappen, før du deler dashboardet med personer uden for arbejdsområdet.

![Del fra OneDrive](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_onedriveshare.png)

## <a name="next-steps"></a>Næste trin
* [Fastgør et felt til et Power BI-dashboard fra Excel](../create-reports/service-dashboard-pin-tile-from-excel.md)
* [Grundlæggende begreber for designere i Power BI-tjenesten](../fundamentals/service-basic-concepts.md)
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
