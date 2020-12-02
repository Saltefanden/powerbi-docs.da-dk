---
title: Opret forbindelse til Azure Search med Power BI
description: Azure Search til Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: 5c2c5d3b6382fdb85125a71829d62624dab31e83
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403369"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Opret forbindelse til Azure Search med Power BI
Med Azure Search Traffic Analytics kan du overvåge og forstå trafikken til Azure Search-tjenesten. Azure Search-indholdspakken til Power BI giver detaljeret indsigt i dine Search-data, herunder søgning, indeksering, tjenestestatistik og ventetid fra de seneste 30 dage. Flere oplysninger finder du i [Azure-blogindlæg](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

[!INCLUDE [include-short-name](../includes/service-deprecate-content-packs.md)]

Opret forbindelse til [Azure Search-indholdspakken](https://app.powerbi.com/getdata/services/azure-search) til Power BI.

## <a name="how-to-connect"></a>Sådan opretter du forbindelse
1. Vælg **Hent data** nederst i navigationsruden.
   
   ![Skærmbillede af Hent data i Power BI Desktop, der viser knappen i ruden Navigator.](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Markér **Hent** i feltet **Tjenester**.
   
   ![Skærmbillede af dialogboksen Tjenester, der viser knappen Hent.](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Vælg **Azure Search** \> **Hent**.
   
   ![Skærmbillede af dialogboksen Azure-tjenester, der viser linket Hent.](media/service-connect-to-azure-search/azuresearch.png)
4. Angiv navnet på den tabellagerkonto, hvor din Azure Search-analyse er gemt.
   
   ![Skærmbillede af dialogboksen Opret forbindelse til Azure Search, hvor feltet Navn på Azure Storage-konto vises.](media/service-connect-to-azure-search/params.png)
5. Vælg **Nøgle** som godkendelsesmetode, og angiv din nøgle til lagerkontoen. Klik på **Log på** for at starte indlæsningsprocessen.
   
   ![Skærmbillede af dialogboksen Opret forbindelse til Azure Search, der viser, at Key er angivet i feltet Godkendelsesmetode.](media/service-connect-to-azure-search/creds.png)
6. Når indlæsningen er fuldført, vises der et nyt dashboard samt en ny rapport og model i navigationsruden. Vælg dashboardet for at få vist de importerede data.
   
    ![Skærmbillede af navigationsruden, der viser dashboardet, rapporten og modellen.](media/service-connect-to-azure-search/dashboard2.png)

**Hvad nu?**

* Prøv [at stille et spørgsmål i feltet Spørgsmål og svar](../consumer/end-user-q-and-a.md) øverst i dashboard'et
* [Rediger felterne](../create-reports/service-dashboard-edit-tile.md) i dashboard'et.
* [Vælg et felt](../consumer/end-user-tiles.md) for at åbne den underliggende rapport.
* Selvom dit datasæt opdateres dagligt, kan du ændre tidsplanen for opdatering eller prøve at opdatere det efter behov ved hjælp af **Opdater nu**

## <a name="system-requirements"></a>Systemkrav
Azure Search-indholdspakken kræver, at Azure Search Traffic Analytics er aktiveret på kontoen.

## <a name="troubleshooting"></a>Fejlfinding
Kontrollér, at navnet på lagerkontoen er angivet korrekt sammen med den fulde adgangsnøgle. Navnet på lagerkontoen skal svare til den konto, der er konfigureret med Azure Search Traffic Analytics.

## <a name="next-steps"></a>Næste trin
[Hvad er Power BI?](../fundamentals/power-bi-overview.md)

[Grundlæggende begreber for designere i Power BI-tjenesten](../fundamentals/service-basic-concepts.md)
