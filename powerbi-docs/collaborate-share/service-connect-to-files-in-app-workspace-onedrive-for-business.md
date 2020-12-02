---
title: Opret forbindelse til filer i OneDrive for et Power BI-arbejdsområde
description: Læs om at gemme og oprette forbindelse til dine Excel-, CSV- og Power BI Desktop-filer på OneDrive for dit Power BI-arbejdsområde.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukasz
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 10/15/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 6c3c43d8aad26249ac1b8afab09bdcbf1414f0cf
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411971"
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-workspace"></a>Opret forbindelse til filer, der gemmes i OneDrive for dit Power BI-arbejdsområde
Når du [opretter et arbejdsområde i Power BI](service-create-workspaces.md), opretter du også en Microsoft 365-gruppe med en tilknyttet OneDrive for Business. I denne artikel forklares det, hvordan du gemmer og opdaterer dine Excel-, CSV- og Power BI Desktop-filer på den pågældende OneDrive for Business. Disse opdateringer afspejles automatisk i dine Power BI-rapporter og på dine Power BI-dashboards, som er baseret på filerne.

> [!NOTE]
> Den nye arbejdsområdeoplevelse ændrer relationen mellem Power BI-arbejdsområder og Microsoft 365-grupper. Du opretter ikke automatisk en Microsoft 365-gruppe, hver gang du opretter et af de nye arbejdsområder. Læs om [oprettelse af nye arbejdsområder](service-create-the-new-workspaces.md)

Tilføjelse af filer til dit arbejdsområde er en proces med to trin: 

1. Først skal du [uploade filer til OneDrive for Business](#1-upload-files-to-the-onedrive-for-business-for-your-workspace) for dit arbejdsområde.
2. Derefter skal du [oprette forbindelse til disse filer fra Power BI](#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> Arbejdsområder er kun tilgængelige med en [Power BI Pro-licens](../fundamentals/service-features-license-type.md).
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 Upload filer til OneDrive for Business for dit arbejdsområde
1. I Power BI-tjenesten skal du vælge pilen ud for Arbejdsområder > vælge ellipsen ( **…** ) ud for navnet på dit arbejdsområde. 
   
   ![Skærmbillede af Power BI-arbejdsområdet, der viser det valgte arbejdsområdenavn.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Vælg **Filer** for at åbne OneDrive for Business for dit arbejdsområde i Microsoft 365.
   
   > [!NOTE]
   > Hvis du ikke ser **Filer** i menuen til arbejdsområdet, skal du vælge **Medlemmer** for at åbne OneDrive for Business for dit arbejdsområde. Her skal du vælge **Filer**. Microsoft 365 konfigurerer en OneDrive-lagerplacering til din apps filer i gruppearbejdsområdet. Denne proces kan tage noget tid.
   > 
   > 
3. Her kan du uploade dine filer til OneDrive for Business for dit apparbejdsområde. Vælg **Upload**, og gå til dine filer.
   
   ![Skærmbillede af OneDrive for Business, der viser, hvordan du kan navigere for at uploade en fil.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Importér Excel-filer som datasæt eller Excel Online-projektmapper
Nu, hvor dine filer er i OneDrive for Business for dit arbejdsområde, står du over for et valg. Du kan: 

* [Importér dataene fra Excel-projektmappen som et datasæt](../connect-data/service-get-data-from-files.md). Brug derefter dataene til at oprette rapporter og dashboards, som du kan få vist i en webbrowser og på mobilenheder.
* Eller [oprette forbindelse til en hel Excel-projektmappe i Power BI](../connect-data/service-excel-workbook-files.md) og vise den præcis, som den vises i Excel Online.

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>Importér eller opret forbindelse til filer i dit arbejdsområde
1. Skift til arbejdsområdet i Power BI, så navnet på arbejdsområdet er i øverste venstre hjørne. 
2. Vælg **Hent data** nederst i navigationsruden. 
   
   ![Skærmbillede af knappen Hent data i navigationsruden.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. Vælg **Hent** i feltet **Filer**.
   
   ![Skærmbillede af dialogboksen Filer, der viser knappen Hent.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Vælg **OneDrive** - *navnet på dit arbejdsområde*.
   
    ![Skærmbillede af tre felter, hvor du kan vælge dit arbejdsområde, der viser Lokal fil, OneDrive og SharePoint.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Markér den ønskede fil > **Opret forbindelse**.
   
    Det er her, du skal beslutte, om du vil [importere dataene fra Excel-projektmappen](../connect-data/service-get-data-from-files.md) eller [oprette forbindelse til hele Excel-projektmapper](../connect-data/service-excel-workbook-files.md).
6. Vælg **Importér** eller **Opret forbindelse**.
   
    ![Skærmbillede af dialogboksen OneDrive for Business, der viser Importér fra Excel eller Opret forbindelse til Excel.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Hvis du vælger **Importér**, så vises projektmappen på fanen **Datasæt**. 
   
    ![Skærmbillede af arbejdsområderne i Power BI, hvor fanen Datasæt vises.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Hvis du vælger **Opret forbindelse**, så er projektmappen på fanen **Projektmapper**.
   
    ![Skærmbillede af arbejdsområderne i Power BI, hvor fanen Projektmapper vises.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>Næste trin
* [Opret apps og arbejdsområder i Power BI](../collaborate-share/service-create-distribute-apps.md)
* [Importér data fra Excel-projektmapper](../connect-data/service-get-data-from-files.md)
* [Opret forbindelse til hele Excel-projektmapper](../connect-data/service-excel-workbook-files.md
* Har du flere spørgsmål? [Prøv Power BI-community'et](https://community.powerbi.com/)
* Har du feedback? Besøg [Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi)
