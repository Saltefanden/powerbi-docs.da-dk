---
title: Brug Kerberos til enkeltlogon (SSO) til SAP HANA
description: Konfigurer din SAP HANA-server for at aktivere SSO fra Power BI-tjenesten
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 12/16/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 3f50b174e8293d75a0077e1799cb64ff4fdcd696
ms.sourcegitcommit: 5c09d121d3205e65fb33a2eca0e60bc30e777773
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/18/2020
ms.locfileid: "97675114"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Brug Kerberos til enkeltlogon (SSO) til SAP HANA

> [!IMPORTANT]
> Da [SAP ikke længere understøtter OpenSSL](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.05/en-US/de15ffb1bb5710148386ffdfd857482a.html), er Microsoft også ophørt med at understøtte det. Eksisterende forbindelser vil fortsat fungere, men du kan ikke oprette nye forbindelser fra og med februar 2021. Fremadrettet skal du bruge CommonCryptoLib i stedet.

I denne artikel beskrives, hvordan du konfigurerer din SAP HANA-datakilde for at aktivere SSO fra Power BI-tjenesten.

> [!NOTE]
> Før du forsøger at opdatere en SAP HANA-baseret rapport, der bruger Kerberos SSO, skal du fuldføre begge trin i denne artikel og trinnene under [Konfigurer Kerberos SSO](service-gateway-sso-kerberos.md).

## <a name="enable-sso-for-sap-hana"></a>Aktivér SSO til SAP HANA

Hvis du vil aktivere SSO til SAP HANA, skal du følge disse trin:

1. Kontrollér, at SAP HANA-serveren kører den påkrævede minimumversion, hvilket afhænger af niveauet af din SAP HANA-serverplatform:
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. På gatewaymaskinen skal du installere den nyeste ODBC-driver til SAP HANA. Minimumversionen er HANA ODBC version 2.00.020.00 fra august 2017.

3. Kontrollér, at SAP HANA-serveren er konfigureret til Kerberos-baseret SSO. Du kan finde flere oplysninger om konfiguration af SSO til SAP HANA ved hjælp af Kerberos under [Enkeltlogon ved hjælp af Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) i Sikkerhedsvejledning til SAP HANA. Se også linket på den side – især SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

Det anbefales også, at du følger disse ekstra trin, som kan give en mindre forbedring af ydeevnen:

1. Find og åbn denne konfigurationsfil i installationsmappen for gatewayen: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. Find egenskaben `FullDomainResolutionEnabled`, og ret værdien til `True`.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Nu kan du [køre en Power BI-rapport](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om datagatewayen i det lokale miljø og DirectQuery i følgende ressourcer:

* [Hvad er en datagateway i det lokale miljø?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakilder, der understøttes af DirectQuery](power-bi-data-sources.md)
* [DirectQuery og SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery og SAP HANA](desktop-directquery-sap-hana.md)
