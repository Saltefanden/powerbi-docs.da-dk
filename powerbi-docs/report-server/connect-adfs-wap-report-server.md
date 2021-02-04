---
title: Brug Web Application Proxy og Active Directory Federated Services – Power BI-rapportserver
description: Få mere at vide om, hvordan du bruger WAP (Web Application Proxy) og AD FS (Active Directory Federation Services) til at oprette forbindelse til Power BI-rapportserver og SSRS 2016 (SQL Server Reporting Services) og nyere.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 02/03/2021
ms.openlocfilehash: 73c7e0b2256d4a45fb9f433a887827e772a32257
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2021
ms.locfileid: "99533067"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Brug Web Application Proxy og Active Directory Federated Services – Power BI-rapportserver

I denne artikel gennemgår vi, hvordan du bruger WAP (Web Application Proxy) og AD FS (Active Directory Federation Services) til at oprette forbindelse til Power BI-rapportserver og SSRS 2016 (SQL Server Reporting Services) og nyere. Brugere, der ikke er i nærheden af virksomhedens netværk, kan ved hjælp af denne integration få adgang til deres Power BI-rapportserver og Reporting Services-rapporter fra deres klientbrowsere og være beskyttet af forhåndsgodkendelse via AD FS. For Power BI-mobilapps skal du også [konfigurere OAuth til at oprette forbindelse til Power BI-rapportserver og SSRS](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Forudsætninger

### <a name="domain-name-services-dns-configuration"></a>Konfiguration af DNS (Domain Name Services)

- Fastlæg den offentlige URL-adresse, som brugeren skal oprette forbindelse til. Den kan se ud på følgende måde: `https://reports.contosolab.com`.
- Konfigurer din DNS-post for værtsnavnet, f.eks. `reports.contosolab.com`, for at pege på den offentlige IP-adresse på WAP-serveren (Web Application Proxy).
- Konfigurer en offentlig DNS-post for din AD FS-server. Du kan f.eks. konfigurere AD FS-serveren med følgende URL-adresse: `https://adfs.contosolab.com`.
- Konfigurer DNS-posten, så den peger på den offentlige IP-adresse for WAP-serveren (Web Application Proxy), f.eks. `adfs.contosolab.com`. Den udgives som en del af WAP-programmet.

### <a name="certificates"></a>Certifikater

Du skal konfigurere certifikater for både WAP-programmet og AD FS-serveren. Begge disse certifikater skal være en del af et gyldigt nøglecenter, som kan genkendes af dine maskiner.

## <a name="1-configure-the-report-server"></a>1. Konfigurer rapportserveren

Vi skal sikre os, at vi har et gyldigt SPN (Service Principal Name). Det gyldige SPN muliggør en korrekt Kerberos-godkendelse og aktiverer rapportserveren til Negotiate-godkendelse.

### <a name="service-principal-name-spn"></a>Tjenestens hovednavn

Tjenestens hovednavn er et entydigt id for en tjeneste, der bruger Kerberos-godkendelse. Du skal sikre, at du har et korrekt HTTP SPN for rapportserveren.

Du kan finde oplysninger om, hvordan du konfigurerer det korrekte hovednavn for tjenesten for rapportserveren, under [Registrer et hovednavn for tjenesten for en rapportserver](/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Aktivering af forhandling af godkendelse

Hvis du vil gøre det muligt, at en rapportserver kan bruge Kerberos-godkendelse, skal du konfigurere, at godkendelsestypen for rapportserveren er RSWindowsNegotiate. Du konfigurerer dette i filen rsreportserver.config.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

Du kan finde flere oplysninger under [Rediger en Reporting Services-konfigurationsfil](/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) og [Konfigurer Windows-godkendelse på en rapportserver](/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Konfigurer AD FS (Active Directory Federation Services).

Du skal konfigurere AD FS på en Windows 2016-server i dit miljø. Konfigurationen kan udføres via Server Manager og ved at vælge Tilføj roller og funktioner under Administrer. Du kan finde flere oplysninger under [Active Directory Federation Services](/windows-server/identity/active-directory-federation-services).

Udfør disse trin På AD FS-serveren ved hjælp af AD FS Management-appen.

1. Højreklik på **Tillidsforhold til afhængig part** > **Tilføj tillidsforhold til afhængig part**.

    ![Tilføj tillidsforhold til afhængig part](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Følg trinnene i guiden **Tilføj tillidsforhold til afhængig part**.

    Vælg indstillingen **Ikke kravsbevidst** for at bruge integreret sikkerhed i Windows som godkendelsesmetode.

    ![Velkommen til guiden Tilføj tillidsforhold til afhængig part](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Angiv et navn i **Angiv vist navn**, og vælg **Næste**.
    Tilføj id for tillidsforhold til afhængig part: `<ADFS\_URL>/adfs/services/trust`

    Eksempel: `https://adfs.contosolab.com/adfs/services/trust`

    ![rapportserver](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Vælg den **adgangskontrolpolitik**, der passer til organisationens behov, og vælg **Næste**.

    ![Vælg adgangskontrol](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Vælg **Næste**, og vælg derefter **Afslut** for at fuldføre guiden **Tilføj tillidsforhold til afhængig part**.

    Når det er fuldført, skal egenskaberne for den afhængige parts tillidsforhold se ud på følgende måde.

    ![Tillidsforhold til afhængig part](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Konfigurer WAP (Web Application Proxy)

Du skal aktivere Windows-rollen Web Application Proxy (rolle) på en server i dit miljø. Det skal ske på en Windows 2016-server. Du kan finde flere oplysninger under [Web Application Proxy i Windows Server 2016](/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) og [Publicering af programmer vha. ADFS-forhåndsgodkendelse](/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication#BKMK_1.2).

### <a name="configure-constrained-delegation"></a>Konfigurer begrænset delegering

Hvis du vil skifte fra Forms-godkendelse til Windows-godkendelse, skal du bruge begrænset delegering med protokolovergang. Dette trin er en del af Kerberos-konfigurationen. Vi har allerede defineret rapportserverens SPN i konfigurationen af rapportserveren.

Vi skal konfigurere begrænset delegering på WAP-serverens maskinkonti i Active Directory. Du skal muligvis samarbejde med en domæneadministrator, hvis du ikke har adgang til Active Directory.

Følg disse trin for at konfigurere begrænset delegering.

1. Start **Active Directory-brugere og -computere** på en computer, hvor Active Directory-værktøjerne er installeret.
2. Find maskinkontoen for WAP-serveren. Den findes som standard i **computerens** objektbeholder.
3. Højreklik på WAP-serveren, og gå til **Egenskaber**.
4. Vælg **Hav kun tillid til denne computer i forbindelse med delegering til de angivne tjenester** på fanen **Delegering**, og vælg derefter **Brug en vilkårlig godkendelsesprotokol**.

    ![Hav tillid til denne computer](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Denne indstilling konfigurerer begrænset delegering for computerkontoen for denne WAP-server. Derefter skal vi angive de tjenester, som denne maskine har tilladelse til at delegere til.
2. Vælg **Tilføj** under tjenestefeltet.

    ![AD FS – tilføj tillid](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Vælg **Brugere eller computere**.
2. Angiv den tjenestekonto, du bruger til rapportserveren. Denne konto er den samme, som du brugte til at tilføje HTTP-SPN'et i det tidligere afsnit [Konfiguration af rapportserver](#1-configure-the-report-server). 

3. Vælg HTTP-SPN'et for rapportserveren, og vælg derefter **OK**.

    > [!NOTE]
    > Du får muligvis kun vist NetBIOS SPN. Tjenestens hovednavn for både NetBIOS og FQDN vælges faktisk, hvis de begge findes.

1. Resultatet ser ud som følger, hvis du vælger at markere afkrydsningsfeltet **Udvidet**.

    ![WAP-Egenskaber](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>Tilføj WAP-program

1. På Web Application Proxy-serveren skal du åbne konsollen **Administration af fjernadgang** og vælge **Web Application Proxy** i navigationsruden. 

2. I ruden **Opgaver** skal du vælge **Publicer**.

2. Vælg **Næste** på velkomstsiden.

    ![Velkommen til Publicer](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. På siden **Forhåndsgodkendelse** skal du vælge **Active Directory Federation Services (AD FS)** og derefter vælge **Næste**.

    ![Forhåndsgodkendelse](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Vælg **Web- og MSOFBA-** forhåndsgodkendelse, da vi kun skal konfigurere browseradgangen til rapportserveren og ikke mobilappadgang.

    ![Understøttede klienter](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Tilføj den **afhængige part**, som vi oprettede på AD FS-serveren som vist nedenfor, og vælg derefter **Næste**.

    ![Publicering af afhængig part](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. I afsnittet **Ekstern URL-adresse** skal du anbringe den offentligt tilgængelige URL-adresse, der er konfigureret på WAP-serveren. Tilføj den URL-adresse, der er konfigureret med rapportserveren (Report Server Configuration Manager), som vist nedenfor i afsnittet **URL-adresse til back end-server**. Tilføj rapportserverens SPN i afsnittet **SPN for back end-server**.

    ![Publiceringsindstillinger](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Vælg **Næste** og **Publicer**.
8. Kør følgende PowerShell-kommando for at validere WAP-konfigurationen.

    ```
    Get-WebApplicationProxyApplication -Name "PBIRSWAP" | FL
    ```

    ![PowerShell-kommando](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Opret forbindelse til rapportserveren via browseren

Du kan derefter få adgang til URL-adressen til den offentlige WAP, f.eks. `https://reports.contosolab.com/ReportServer` for webtjenesten og `https://reports.contosolab.com/Reports` for webportalen fra browseren. Når du er blevet godkendt, kan du få vist rapporterne.

![AD FS-logon](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Næste trin

* [Konfigurer OAuth til at oprette forbindelse til Power BI-rapportserver og SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[Hvad er Power BI-rapportserver?](get-started.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
