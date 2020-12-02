---
title: Føj Power BI URL-adresser til listen over tilladte
description: I denne artikel vises URL-slutpunkter og porte, der skal angives på en liste over tilladte ved oprettelse af forbindelse til Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: 433b3d53ccb653e1a945a83176ab9ebc19ccac5d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96409234"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>Føj Power BI URL-adresser til listen over tilladte
[//]: # "suparnap, miwehnia og natham er kontakter til vedligeholdelse af listen"

Der skal bruges internetforbindelse til Power BI-tjenesten. De slutpunkter, der er angivet i tabellerne i denne artikel, skal være tilgængelige for kunder, der bruger Power BI-tjenesten.

Hvis du vil bruge Power BI-tjenesten, skal du kunne oprette forbindelse til de slutpunkter, der er markeret med **Påkrævet** i tabellen nedenfor, og de slutpunkter, som er markeret med **Påkrævet** på de websteder, der linkes til. Hvis linket til et eksternt websted refererer til en bestemt sektion, skal du kun se slutpunkterne i den sektion.

De slutpunker, der er markeret med **Valgfri**, kan også føjes til lister over tilladte til bestemte funktioner.

Power BI-tjenesten kræver kun, at TCP-port 443 er åben for de viste slutpunkter.

Stjernen (*) repræsenterer alle niveauer under roddomænet, og vi bruger I/T, når oplysningerne ikke er tilgængelige. I kolonnen **Destination(er)** vises en liste med domænenavne og links til eksterne websteder, som indeholder yderligere oplysninger om slutpunkter.

>[!Important]
>Oplysningerne i nedenstående tabeller gælder ikke for Power BI Tyskland, Power BI Kina, der drives af 21Vianet eller Power BI til US Government. Læs [Opret forbindelse mellem Government-tjenester og globale Azure Cloud-tjenester](service-govus-overview.md#connect-government-and-global-azure-cloud-services) for at få mere at vide om kommunikation mellem cloudtjenester.

## <a name="authentication"></a>Godkendelse

Power BI er afhængig af de krævede slutpunkter i sektionerne til godkendelse og identitet i Microsoft 365. Hvis du vil bruge Power BI, skal du kunne oprette forbindelse til slutpunkterne på det websted, der linkes til nedenfor.

| Række | Formål | Destination(er) | Port(e) |
| --- | --- | --- | --- |
| 1 | **Påkrævet:** Godkendelse og identitet | Se dokumentationen til [Almindelige URL-adresser til Microsoft 365 og Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | I/T |

## <a name="general-site-usage"></a>Websted til generel brug

Hvis du vil bruge Power BI, skal du kunne oprette forbindelse til slutpunkterne fra tabellen og de websteder, der linkes til nedenfor.

| Række | Formål | Destination(er) | Port(e) |
| --- | --- | --- | --- |
| 1 | **Påkrævet:** Back-end-API'er | api.powerbi.com | TCP 443 |
| 2 | **Påkrævet:** Back-end-API'er | *.analysis.windows.net | TCP 443 |
| 3 | **Påkrævet:** Back-end-API'er | *.pbidedicated.windows.net | TCP 443 |
| 4 | **Påkrævet:** CDN (Content Delivery Network) | content.powerapps.com | TCP 443 |
| 5 | **Påkrævet:** Microsoft 365-integration | Se dokumentationen til [Almindelige URL-adresser til Microsoft 365 og Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | I/T |
| 6 | **Påkrævet:** Portal | *.powerbi.com | TCP 443 |
| 7 | **Påkrævet:** Tjenestetelemetri | dc.services.visualstudio.com | TCP 443 |
| 8 | **Valgfrit:** Meddelelser til orientering | dynmsg.modpim.com | TCP 443 |
| 9 | **Valgfrit:** NPS-undersøgelser | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administration

Hvis du vil udføre administrative funktioner i Power BI, skal du kunne oprette forbindelse til slutpunkterne på de websteder, der linkes til nedenfor.

| Række | Formål | Destination(er) | Port(e) |
| --- | --- | --- | --- |
| 1 | **Påkrævet:** Til administration af brugere og visning af overvågningslogge | Se dokumentationen til [Almindelige URL-adresser til Microsoft 365 og Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | I/T |
| | | |

## <a name="getting-data"></a>Hent data

Hvis du vil hente data fra specifikke datakilder, f.eks. OneDrive, skal du kunne oprette forbindelse til slutpunkterne i tabellen nedenfor. Adgang til yderligere internetdomæner og URL-adresser er muligvis påkrævet for specifikke datakilder i din organisation.

| Række | Formål | Destination(er) | Port(e) |
| --- | --- | --- | --- |
| 1 | **Påkrævet:** AppSource (interne eller eksterne apps i Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Valgfrit:** Log på, og hent data til indholdspakker | Afhænger af anvendte indholdspakker | Afhænger af anvendte indholdspakker |
| 3 | **Valgfrit:** Importér filer fra et personligt OneDrive | S [Krævede URL-adresser og porte til OneDrive-webstedet](/onedrive/required-urls-and-ports) | I/T |
| 4 | **Valgfrit:** 60 sekunders video med selvstudie om Power BI | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Valgfrit:** PubNub-streamingdatakilder | Se [dokumentationen til PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | I/T |
| | | |

## <a name="dashboard-and-report-integration"></a>Dashboard- og rapportintegration

Power BI er afhængig af, at bestemte slutpunkter understøtter dine dashboards og rapporter. Du skal kunne oprette forbindelse til slutpunkterne i tabellen og de websteder, der linkes til, nedenfor.

| Række | Formål | Destination(er) | Port(e) |
| --- | --- | --- | --- |
| 1 | **Påkrævet:** Excel-integration | Se dokumentationen til [Almindelige URL-adresser til Microsoft 365 og Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | I/T |
| | | |

## <a name="power-bi-visuals"></a>Power BI-visualiseringer

Power BI er afhængig af, at bestemte slutpunkter kan se og få adgang til Power BI-visualiseringer. Du skal kunne oprette forbindelse til slutpunkterne i tabellen og de websteder, der linkes til, nedenfor.

| Række | Formål | Destination(er) | Port(e) |
| --- | --- | --- | --- |
| 1 | **Påkrævet:** Importér en brugerdefineret visualisering fra Marketplace-brugergrænsefladen eller fra en fil | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Valgfrit:** Bing Maps | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Valgfrit:** PowerApps | Se [sektionen Krævede tjenester](/powerapps/maker/canvas-apps/limits-and-config#required-services) fra webstedet med systemkrav til PowerApps | I/T |
| 4 | **Valgfrit:** Visio | Se dokumentationen til [Almindelige URL-adresser til Microsoft 365 og Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) samt [SharePoint Online og OneDrive for Business](/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | I/T |
| | | |

## <a name="related-external-sites"></a>Relaterede eksterne websteder

Power BI-links til andre relaterede websteder. Disse websteder hoster dokumentation, support, forslag til nye funktioner og meget mere. Adgangen til disse websteder påvirker ikke Power BI's funktionalitet, så det er valgfrit, om du vil føje dem til lister over tilladte.

| Række | Formål | Destination(er) | Port(e) |
| --- | --- | --- | --- |
| 1 | **Valgfrit:** Communitywebsted | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Valgfrit:** Dokumentationswebsted | docs.Microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Valgfrit:** Downloadwebsted (til Power BI Desktop osv.) | download.microsoft.com | TCP 443 |
| 4 | **Valgfrit:** Eksterne omdirigeringer | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Valgfrit:** Websted med idéer og feedback| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Valgfrit:** Power BI-webstedet – landingsside, links til yderligere oplysninger, supportwebsted, downloadlinks, partnerpræsentation osv. | powerbi.Microsoft.com | TCP 443 |
| 7 | **Valgfrit:** Power BI Developer Center | dev.powerbi.com | TCP 443 |
| 8 | **Valgfrit:** Supportwebsted | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |