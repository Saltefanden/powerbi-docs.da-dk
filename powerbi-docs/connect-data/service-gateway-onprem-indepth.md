---
title: Datagateway i det lokale miljø – detaljeret
description: Denne artikel ser detaljeret på gatewayen i det lokale miljø. Vi ser på, hvordan tjenesten fungerer sammen med Azure Active Directory og dit lokale Active Directory, når du arbejder med Analysis Services
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 0964ad3e391c8e066c31ea7bb53f67e97f254422
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392348"
---
# <a name="on-premises-data-gateway-in-depth"></a>Datagateway i det lokale miljø – detaljeret

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Vi har flyttet oplysningerne fra denne artikel til flere forskellige artikler på tværs af Power BI og generelle dokumenter. Følg linkene under hver overskrift for at finde det relevante indhold.

## <a name="how-the-gateway-works"></a>Sådan virker gatewayen

Se [Arkitektur for datagatewayen i det lokale miljø](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Liste over tilgængelige datakildetyper

Se [Administrer datakilder](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Godkendelse til datakilder i det lokale miljø

Se [Godkendelse til datakilder i det lokale miljø](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Godkendelse til en live Analysis Services-datakilde

Se [Godkendelse til en live Analysis Services-datakilde](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Rollebaseret sikkerhed

Se [Rollebaseret sikkerhed](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Sikkerhed på rækkeniveau

Se [Sikkerhed på rækkeniveau](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>Hvad med Azure Active Directory?

Se [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Hvordan kan jeg se, hvad mit UPN er?

Se [Hvordan kan jeg se, hvad mit UPN er?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is)

## <a name="map-user-names-for-analysis-services-data-sources"></a>Tilknyt brugernavne for Analysis Services-datakilder

Se [Tilknyt brugernavne for Analysis Services-datakilder](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synkroniser en lokal Active Directory med Azure Active Directory

Se [Synkroniser Active Directory i det lokale miljø med Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>Hvad skal du så gøre?

Se artiklerne om datakilder:

[Administrer dine datakilder](service-gateway-data-sources.md)
[Administrer din datakilde – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Administrer din datakilde – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Administrer din datakilde – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Administrer din datakilde – Oracle](service-gateway-onprem-manage-oracle.md)  
[Administrer din datakilde – Import/Planlagt opdatering](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Hvor ting kan gå galt

Se [Foretag fejlfinding af datagatewayen i det lokale miljø](/data-integration/gateway/service-gateway-tshoot) og [Foretag fejlfinding af gateways – Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Logonkonto

Se [Logonkonto](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Windows-tjenestekonto

Se [Skift tjenestekontoen til datagatewayen i det lokale miljø](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Porte

Se [Porte](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>Gennemtving HTTPS-kommunikation med Azure Service Bus

Se [Gennemtving HTTPS-kommunikation med Azure Service Bus](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Understøttelse af TLS 1.2

Se [TLS 1.2 til gatewaytrafik](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>Sådan genstarter du gatewayen

Se [Genstart en gateway](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Næste trin

[Hvad er datagatewayen i det lokale miljø?](service-gateway-onprem.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)