---
title: Opret forbindelse til Office365Mon med Power BI
description: Office365Mon til Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 11/26/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: c7433bcc75da316e2e705a63dbcc2f17745ad573
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403047"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Opret forbindelse til Office365Mon med Power BI
Du kan nemt analysere nedetid i Office 365 og ydeevnedata med Power BI og Office365Mon-skabelonappen. Power BI henter dine data, herunder om nedetid og fra tilstandsundersøgelser, og opretter derefter et færdigt dashboard og rapporter ud fra de pågældende data.

Opret forbindelse til [Office365Mon-skabelonappen](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3) til Power BI.

>[!NOTE]
>Det er nødvendigt med en Office365Mon-administratorkonto for at oprette forbindelse til og indlæse Power BI-skabelonappen.

## <a name="how-to-connect"></a>Sådan opretter du forbindelse
1. Vælg **Hent data** nederst i navigationsruden.
   
   ![Skærmbillede af knappen Hent data i navigationsruden.](media/service-connect-to-office365mon/pbi_getdata.png)
2. Markér **Hent** i feltet **Tjenester**.
   
   ![Skærmbillede af dialogboksen Tjenester, der viser knappen Hent.](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Vælg **Office365Mon** \> **Hent**.
   
   ![Skærmbillede af dialogboksen Office365Mon, der viser linket Hent.](media/service-connect-to-office365mon/o365mon.png)
4. Som godkendelsesmetode skal du vælge **oAuth2** \> **Log på**.
   
   Når du bliver spurgt, skal du angive dine legitimationsoplysninger til din Office365Mon-administratorkonto og følge godkendelsesprocessen.
   
   ![Skærmbillede af dialogboksen Opret forbindelse til Office365Mon, der viser o Auth2 i feltet Godkendelsesmetode.](media/service-connect-to-office365mon/creds.png)
   
   ![Skærmbillede af Office365Mon-logon, hvor du blive bedt om at angive dine legitimationsoplysninger.](media/service-connect-to-office365mon/creds2.png)
5. Når Power BI har importeret dataene, vises der et nyt dashboard, en ny rapport og et nyt datasæt i navigationsruden. Nye elementer er markeret med en gul stjerne \*, vælg posten Office365Mon.
   
   ![Skærmbillede af navigationsruden i Power BI, der viser dashboardet, rapporten og datasættet.](media/service-connect-to-office365mon/dashboard4.png)

**Hvad nu?**

* Prøv [at stille et spørgsmål i feltet Spørgsmål og svar](../consumer/end-user-q-and-a.md) øverst i dashboard'et
* [Rediger felterne](../create-reports/service-dashboard-edit-tile.md) i dashboard'et.
* [Vælg et felt](../consumer/end-user-tiles.md) for at åbne den underliggende rapport.
* Selvom dit datasæt opdateres dagligt, kan du ændre tidsplanen for opdatering eller prøve at opdatere det efter behov ved hjælp af **Opdater nu**

## <a name="troubleshooting"></a>Fejlfinding
Hvis du får fejlmeddelelsen **"Kunne ikke logge på"** , når du har brugt dine legitimationsoplysninger til Office365Mon-abonnementet for at logge på, skyldes det, at den konto, du bruger, ikke har tilladelse til at hente Office365Mon-data fra din konto. Kontrollér, at det er en administratorkonto, og prøv igen.

## <a name="next-steps"></a>Næste trin
[Hvad er Power BI?](../fundamentals/power-bi-overview.md)

[Hent data til Power BI](service-get-data.md)
