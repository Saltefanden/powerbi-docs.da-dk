---
title: 'Fejl: Der blev ikke fundet nogen data i din Excel-projektmappe'
description: 'Fejl: Der blev ikke fundet nogen data i din Excel-projektmappe'
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 04/30/2019
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6e78dba3e6a18544f68fae4b737a7840d1fa2724
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403783"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Fejl: Der blev ikke fundet nogen data i din Excel-projektmappe

>[!NOTE]  
>Denne artikel gælder for Excel 2007 og nyere.

Når du importerer en Excel-projektmappe til Power BI, kan du se følgende fejl:

*Fejl: Vi kunne ikke finde nogen data, der er formateret som en tabel. Hvis du vil importere fra Excel til Power BI-tjenesten, skal du formatere dataene som en tabel. Markér alle de data, du vil have i tabellen, og tryk på CTRL + T.*

![Data blev ikke fundet i projektmappen](media/service-admin-troubleshoot-excel-workbook-data/power-bi-we-couldnt-find-any-data.png)

## <a name="quick-solution"></a>Hurtig løsning
1. Rediger din projektmappe i Excel.
2. Markér det celleområde, der indeholder dataene. Den første række skal indeholde kolonneoverskrifterne (kolonnenavnene).
3. Tryk på **Ctrl + T** for at oprette en tabel.
4. Gem projektmappen.
5. Vend tilbage til Power BI, og importér projektmappen igen, eller hvis du arbejder i Excel 2016, og du har gemt projektmappen på OneDrive for Business, skal du i Excel klikke på Filer > Udgiv.

## <a name="details"></a>Detaljer
### <a name="cause"></a>Årsag
I Excel kan du oprette en **tabel** ud af et celleområde, som gør det nemmere at sortere, filtrere og formatere data.

Når du importerer en Excel-projektmappe, leder Power BI efter disse tabeller og importerer dem til et datasæt. Hvis der ikke findes nogen tabeller, vises denne fejlmeddelelse.

### <a name="solution"></a>Løsning
1. Åbn din projektmappe i Excel. 
    >[!NOTE]
    >Billederne her er til Excel 2013. Hvis du bruger en anden version, kan det se lidt anderledes ud, men trinnene er de samme.
    
    ![Åbn projektmappe](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-1.png)
2. Markér det celleområde, der indeholder dataene. Den første række skal indeholde kolonneoverskrifterne (kolonnenavnene):
   
    ![Vælg celleområde](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-2.png)
3. Klik på **Tabel** på båndet under fanen **INDSÆT**. (Eller som en genvej kan du trykke på **Ctrl + T**).
   
    ![Indsæt tabel](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-3.png)
4. Du kan se følgende dialogboks. Sørg for, at **Tabellen indeholder overskrifter** er markeret, og vælg **OK**:
   
    ![Opret tabel](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-create-table.png)
5. Nu er dataene formateret som en tabel:
   
    ![Data, der er formateret som en tabel](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-table.png)
6. Gem projektmappen.
7. Vend tilbage til Power BI. Vælg Hent data nederst i navigationsruden.
   
    ![Hent data](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-data.png)
8. Vælg **Hent** i feltet **Filer**.
   
    ![Hent filer](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-files.png)
9. Importér Excel-projektmappen igen. Denne gang bør importen finde tabellen.
   
    Hvis importen stadig mislykkes, kan du give os besked ved at klikke på **Community ** i menuen Hjælp:
   
    ![Communitylink](media/service-admin-troubleshoot-excel-workbook-data/power-bi-question-menu-community.png)
