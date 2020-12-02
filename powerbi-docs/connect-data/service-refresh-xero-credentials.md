---
title: Sådan opdaterer du dine legitimationsoplysninger til Xero-indholdspakken
description: Hvis du bruger Xero Power BI-indholdspakken, kan du have oplevet et problem med indholdspakkens daglige opdatering på grund af en nylig hændelse på Power BI-tjenesten.
author: paulinbar
ms.author: painbar
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/10/2017
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 972340d4c9cca4507308aaac4c07f410ff8fc6fe
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392099"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>Sådan opdaterer du dine legitimationsoplysninger til Xero-indholdspakken, hvis opdatering mislykkedes
Hvis du bruger Xero Power BI-indholdspakken, kan du have oplevet nogle problemer med indholdspakkens daglige opdatering på grund af en nylig hændelse på Power BI-tjenesten.

Du kan se, om din indholdspakke blev korrekt opdateret ved at kontrollere status for seneste opdatering til dit Xero-datasæt, som vist på skærmbilledet nedenfor.

![Skærmbillede af dialogboksen Xero, der viser opdateringsstatus for dit Xero-datasæt.](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

Hvis opdateringen mislykkedes som vist ovenfor, skal du følge disse trin for at forny dine legitimationsoplysninger til indholdspakken.

1. Klik på **Flere indstillinger** (...) ud for dit Xero-datasæt, og klik derefter på **Planlæg opdatering**. Indstillingssiden åbnes for Xero-indholdspakken.
   
    ![Skærmbillede af dialogboksen Xero, der viser indstillingen Planlæg opdatering.](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. Vælg **Legitimationsoplysninger for datakilde** > **Rediger legitimationsoplysninger** på siden **Indstillinger for Xero**.
   
    ![Skærmbillede af dialogboksen Xero-indstillinger, der viser indstillingerne for Xero med Rediger legitimationsoplysninger valgt.](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. Indtast din organisations navn > **Næste**.
   
    ![Skærmbillede af dialogboksen Konfigurer Xero, der viser organisationens navn.](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Log på med din Xero-konto.
   
    ![Skærmbillede af dialogboksen Xero-logon, der viser, hvordan du logger på din Xero-konto.](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. Nu hvor dine legitimationsoplysninger er opdateret, skal vi sikre os, at tidsplanen for opdatering er indstillet til at køre dagligt. Kontrollér det ved at klikke på **Flere indstillinger** (...) ud for dit Xero-datasæt og derefter klikke på **Planlæg opdatering** igen.
   
    ![Skærmbillede af dialogboksen Planlæg opdatering, der viser opdateringsfrekvensen og-tidszonen.](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. Du kan også vælge at opdatere datasættet med det samme. Klik på **Flere indstillinger** (...) ud for dit Xero-datasæt, og klik derefter på **Opdater nu**.
   
    ![Skærmbillede af dialogboksen Xero, der viser Opdater nu, som er markeret.](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

Hvis du stadig har problemer med opdatering, er du velkommen til at kontakte os på [https://support.powerbi.com](https://support.powerbi.com) 

Hvis du vil vide mere om Xero-indholdspakken til Power BI, skal du gå til [Xero-indholdspakkens Hjælp-side](service-connect-to-xero.md).

### <a name="next-steps"></a>Næste trin
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

