---
title: Azure-sikkerhedsbaseline til Power BI
description: Power BI-sikkerhedsbaselinen leverer procedurebaseret vejledning og ressourcer til implementering af de sikkerhedsanbefalinger, der er angivet i Azure Security Benchmark.
author: mbaldwin
ms.author: margoc
ms.service: powerbi
ms.subservice: pbi-security
ms.topic: conceptual
ms.date: 11/20/2020
ms.custom: subject-security-benchmark
ms.openlocfilehash: 9e7aefba7a2e47fbf5249feaab3ac56057ac867c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386257"
---
# <a name="azure-security-baseline-for-power-bi"></a>Azure-sikkerhedsbaseline til Power BI

I denne sikkerhedsbaseline anvendes vejledning fra [Azure Security Benchmark version 2.0](https://docs.microsoft.com/azure/security/benchmarks/overview) til Power BI. Azure Security Benchmark leverer anbefalinger til, hvordan du kan beskytte dine cloudløsninger i Azure. Indholdet er grupperet efter de **sikkerhedskontroller**, der er defineret af Azure Security Benchmark og den relaterede vejledning, der gælder for Power BI. **Kontroller**, der ikke er relevante for Power BI, er blevet udeladt.

Hvis du vil se, hvordan Power BI helt knyttes til Azure Security Benchmark, skal du se [den fulde fil med tilknytning til Power BI-sikkerhedsbaseline](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="network-security"></a>Netværkssikkerhed

*Du kan finde flere oplysninger i [Azure Security Benchmark: Netværkssikkerhed](/azure/security/benchmarks/security-controls-v2-network-security).*

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3: Etabler privat netværksadgang til Azure-tjenester

**Vejledning**: Power BI understøtter oprettelse af forbindelse mellem din Power BI-lejer og et Private Link-slutpunkt og deaktiverer adgang til det offentlige internet.

- [Private links, der giver adgang til Power BI](https://docs.microsoft.com/power-bi/admin/service-security-private-links)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Delt

## <a name="identity-management"></a>Identitetsstyring

*Du kan finde flere oplysninger i [Azure Security Benchmark: Identitetsstyring](/azure/security/benchmarks/security-controls-v2-identity-management).*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1: Standardiser Azure Active Directory som det centrale identitets- og godkendelsessystem

**Vejledning**: Power BI er integreret i Azure Active Directory (Azure AD), som er Azures standardtjeneste til identitets- og adgangsstyring. Du bør standardisere Azure AD for at kontrollere din organisations identitets- og adgangsstyring.

Beskyttelse af Azure AD bør være en høj prioritet i din organisations cloudsikkerhedspraksis. Azure AD leverer en sikkerhedsscore for identitet for at hjælpe dig med at vurdere sikkerhedsniveauet for identitet i forhold til Microsofts anbefalinger for bedste praksis. Brug scoren til at måle, i hvor grad din konfiguration stemmer overens med anbefalingerne til bedste praksis og foretage forbedringer af dit sikkerhedsniveau.

Bemærk! Azure AD understøtter eksterne identiteter, der giver brugere uden en Microsoft-konto mulighed for at logge på deres programmer og ressourcer med deres eksterne identitet.

- [Lejemål i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

- [Sådan opretter og konfigurerer du en Azure AD-instans](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [Brug eksterne identitetsudbydere til programmet](https://docs.microsoft.com/azure/active-directory/b2b/identity-providers)

- [Hvad er sikkerhedsscoren for identitet i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2: Administrer programidentiteter sikkert og automatisk

**Vejledning**: Power BI og Power BI Embedded understøtter brugen af tjenesteprincipaler. Gem alle legitimationsoplysninger til tjenesteprincipaler, der bruges til at kryptere eller få adgang til Power BI i Key Vault, tildel passende adgangspolitikker til samlingen af legitimationsoplysninger, og gennemse regelmæssigt adgangstilladelser.

Automatiser Premium-opgaver for arbejdsområde og datasæt med tjenesteprincipaler https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3: Brug Azure AD-enkeltlogon (SSO) til programadgang

**Vejledning**: Power BI bruger Azure Active Directory til at levere identitets- og adgangsstyring for Azure-ressourcer, cloudbaserede programmer og programmer i det lokale miljø. Dette omfatter virksomhedsidentiteter såsom medarbejdere samt eksterne identiteter såsom partnere, forhandlere og leverandører. Dette muliggør enkeltlogon (SSO) til administration og beskyttelse af din organisations data og ressourcer i det lokale miljø og i cloudmiljøet. Forbind alle dine brugere, programmer og enheder til Azure AD for at få problemfri, sikker adgang og større synlighed og styring.

- [Forstå enkeltlogon til programmer med Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4: Brug stærke godkendelseskontroller til al Azure Active Directory-baseret adgang

**Vejledning**: Power BI er integreret i Azure AD, som understøtter stærke godkendelseskontroller via multifaktorgodkendelse (MFA) og stærke metoder uden adgangskode.
- Multifaktorgodkendelse – Aktivér MFA til Azure AD, og følg anbefalingerne til Identitets- og adgangsstyring i Azure Security Center for at bruge bedste praksis i din MFA-konfiguration. MFA kan håndhæves for alle brugere, for udvalgte brugere eller for niveauet pr. bruger baseret på logonbetingelser og risikofaktorer.
- Godkendelse uden adgangskode – Der er tre godkendelsesmuligheder uden adgangskode tilgængelige: Windows Hello for Business, Microsoft Authenticator-app og godkendelsesmetoder i det lokale miljø såsom chipkort.

For administratorer og privilegerede brugere skal du sørge for, at det højeste niveau af stærk godkendelse bruges efterfulgt af udrulning af en passende stærk godkendelsespolitik for andre brugere.

Bemærk! MFA kan kun håndhæves for brugerkonti, der er aktiveret i Azure AD. Power BI-tjenesteprincipaler understøtter ikke brugen af MFA.

- [Sådan aktiveres MFA i Azure](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

- [Introduktion til godkendelsesmuligheder uden adgangskode til Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5: Overvåg og giv besked om uregelmæssigheder på konto

**Vejledning**: Definer politikker for registrering af uregelmæssigheder i Microsoft Cloud App Security, der kan tildeles uafhængigt af hinanden, så de kun gælder for de brugere og grupper, som du vil inkludere. Disse politikker for registrering af uregelmæssigheder kan hjælpe med at registrere og overvåge uregelmæssigheder i adfærd relateret til brugere, der har adgang til og bruger Power BI.

- [Brug af Microsoft Cloud App Security-kontroller i Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6: Begræns adgang til Azure-ressourcer på baggrund af betingelser

**Vejledning**: Power BI understøtter betinget adgang til Azure AD for at opnå en mere detaljeret adgangskontrol baseret på brugerdefinerede betingelser, f.eks. at brugerlogon fra bestemte IP-intervaller skal bruge MFA for at logge på. Politik for administration af session med detaljeret godkendelse kan også bruges til forskellige use cases.

- [Oversigt over betinget adgang til Azure](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

- [Almindelige politikker for betinget adgang](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

- [Konfigurer administration af session med godkendelse med betinget adgang](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

- [Brug af Microsoft Cloud App Security-kontroller i Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7: Fjern utilsigtet eksponering af legitimationsoplysninger

**Vejledning**: I forbindelse med integrerede Power BI-programmer anbefales det at implementere Credential Scanner for at identificere legitimationsoplysninger i din kode. Credential Scanner opfordrer også til, at fundne legitimationsoplysninger flyttes til mere sikre placeringer såsom Azure Key Vault.

Gem alle krypteringsnøgler eller legitimationsoplysninger til tjenesteprincipaler, der bruges til at kryptere eller få adgang til Power BI i Key Vault, tildel korrekte adgangspolitikker til samlingen af legitimationsoplysninger, og gennemse regelmæssigt adgangstilladelser.
 
Til GitHub kan du bruge funktionen til scanning efter oprindelig hemmelighed til at identificere legitimationsoplysninger eller andre former for hemmeligheder i koden.

- [Medbring dine egne krypteringsnøgler til Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

 
Sådan konfigurerer du legitimationsoplysninger
- [Scanner](https://secdevtools.azurewebsites.net/helpcredscan.html) 

- [Scanning efter GitHub-hemmelighed](https://docs.github.com/github/administering-a-repository/about-secret-scanning)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Delt

## <a name="privileged-access"></a>Privilegeret adgang

*Du kan finde flere oplysninger i [Azure Security Benchmark: Privilegeret adgang](/azure/security/benchmarks/security-controls-v2-privileged-access).*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1: Beskyt og begræns brugere med mange tilladelser

**Vejledning**: Hvis du vil reducere risikoen og følge princippet om færreste tilladelser, anbefales det, at du kun tildeler medlemskab som Power BI-administrator til nogle få personer. Brugere med disse privilegerede tilladelser kan potentielt få adgang til og redigere alle administrationsfunktioner for organisationen. Globale administratorer via Microsoft 365 eller Azure Active Directory kan implicit også have administratorrettigheder i Power BI-tjenesten.

Power BI indeholder nedenstående konti med mange tilladelser:
- Global administrator
- Faktureringsadministration
- Licensadministrator
- Brugeradministrator
- Power BI Administration
- Administration af Power BI Premium-kapacitet
- Administrator af Power BI Embedded-kapacitet

Power BI understøtter sessionspolitikker i Azure AD for at aktivere politikker for betinget adgang og dirigere sessioner, der bruges i Power BI via Cloud App Security-tjenesten.

Aktivér privilegeret JIT-adgang (just-in-time) til Power BI-administratorkonti ved hjælp af privilegeret adgangsstyring i M365.

- [Administratorroller, der er relateret til Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-administering-power-bi-in-your-organization#administrator-roles-related-to-power-bi)

- [Privilegeret adgangsstyring i M365](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true)

- [Cloud App Security-kontroller i Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: Begræns administrativ adgang til forretningskritiske systemer

**Vejledning**: Begræns antallet af yderst privilegerede konti eller roller med øget adgang til Power BI.

Du kan aktivere privilegeret JIT-adgang (just-in-time) ved hjælp af vejledningen til privilegeret adgangsstyring i M365 [her](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true).

Du kan finde yderligere oplysninger på side 183 i dokumentet om udrulning af Power BI i store virksomheder [her](https://aka.ms/PBIEnterpriseDeploymentWP).

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3: Gennemse og afstem brugeradgangen regelmæssigt

**Vejledning**: Som administrator af Power BI-tjenesten kan du analysere forbruget for alle Power BI-ressourcer på lejerniveau ved hjælp af brugerdefinerede rapporter, der er baseret på Power BI-aktivitetsloggen. Du kan downloade aktiviteterne ved hjælp af en REST API eller PowerShell-cmdlet. Du kan også filtrere aktivitetsdataene efter datoområde, bruger og aktivitetstype.

Du skal opfylde disse krav for at få adgang til Power BI-aktivitetsloggen:
- Du skal enten være global administrator eller administrator af Power BI-tjenesten.
- Du har installeret [administrations-cmdlet'er i Power BI](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) lokalt eller bruger administrations-cmdlet'er i Power BI i Azure Cloud Shell.

Når disse krav er opfyldt, kan du følge vejledningen nedenfor for at spore brugeraktivitet i Power BI:

- [Spor brugernes aktivitet i Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4: Konfigurer akutadgang i Azure AD

**Vejledning**: Power BI er integreret i Azure Active Directory og M365, så ressourcerne kan administreres. Hvis du vil forhindre utilsigtet spærring af din M365-lejer eller Azure AD-organisation, skal du konfigurere en akutadgangskonto til adgang, når der ikke kan bruges normale administrative konti. Akutadgangskonti har som regel mange tilladelser, og de bør ikke tildeles til specifikke enkeltpersoner. Akutadgangskonti er begrænset til nødstilfælde eller scenarier af typen "knust glas", hvor normale administrative konti ikke kan bruges.

Du skal sørge for, at legitimationsoplysningerne (f.eks. adgangskode, certifikat eller chipkort) for akutadgangskonti holdes sikre og kun kendes af personer, der kun er autoriseret til at bruge dem i nødstilfælde.

- [Administrer akutadgangskonti i Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access)

- [Beskyt dine M365-konti](https://docs.microsoft.com/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6: Brug arbejdsstationer med privilegeret adgang

**Vejledning**: Sikre, isolerede arbejdsstationer er meget vigtige i forbindelse med sikkerheden af følsomme roller såsom administratorer, udviklere og kritiske tjenesteoperatører. Brug yderst sikre brugerarbejdsstationer og/eller Azure Bastion til administrative opgaver, der er relateret til administration af Power BI. Brug Azure Active Directory, Microsoft Defender Advanced Threat Protection (ATP) og/eller Microsoft Intune til at udrulle en sikker og administreret brugerarbejdsstation til administrative opgaver. De sikre arbejdsstationer kan administreres centralt for at håndhæve sikker konfiguration, herunder stærk godkendelse, software- og hardwarebaselines, begrænset logisk adgang og netværksadgang.

Forstå privilegeret adgang
- [arbejdsstationer](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-managed-workstation)

- [Udrul en privilegeret arbejdsstation til adgang](https://docs.microsoft.com/azure/active-directory/devices/howto-azure-managed-workstation)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

## <a name="data-protection"></a>Databeskyttelse

*Du kan finde flere oplysninger i [Azure Security Benchmark: Databeskyttelse](/azure/security/benchmarks/security-controls-v2-data-protection).*

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1: Find, klassificer og forsyn følsomme data med mærkat

**Vejledning**: Brug følsomhedsmærkater fra Microsoft Information Protection på dine rapporter, dashboards, datasæt og dataflow for at beskytte dit følsomme indhold mod uautoriseret adgang og lækage af data.

Brug følsomhedsmærkater fra Microsoft Information Protection til at klassificere dine rapporter, dashboards, datasæt og dataflow samt forsyne dem med mærkat i Power BI-tjenesten. Beskyt desuden dit følsomme indhold mod uautoriseret adgang og lækage af data, når indhold eksporteres fra Power BI-tjenesten til Excel-, PowerPoint- og PDF-filer.

- [Sådan anvendes følsomhedsmærkater i Power BI](https://docs.microsoft.com/power-bi/admin/service-security-apply-data-sensitivity-labels)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="dp-2-protect-sensitive-data"></a>DP-2: Beskyt følsomme data

**Vejledning**: Power BI kan integreres med følsomhedsmærkater fra Microsoft Information Protection med henblik på beskyttelse af følsomme data. Du kan finde flere oplysninger i [Følsomhedsmærkater fra Microsoft Information Protection i Power BI](https://docs.microsoft.com/power-bi/admin/service-security-sensitivity-label-overview)

Power BI gør det muligt for brugerne af tjenesten at medbringe deres egen nøgle for at beskytte inaktive data. Du kan finde flere oplysninger i [Medbring dine egne krypteringsnøgler til Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

Kunderne har mulighed for at bevare datakilder i det lokale miljø og gøre brug af Direct Query eller Live Connect med en datagateway i det lokale miljø for at minimere dataeksponering til cloudtjenesten. Du kan finde flere oplysninger i [Hvad er en datagateway i det lokale miljø?](https://docs.microsoft.com/data-integration/gateway/service-gateway-onprem)

Power BI understøtter sikkerhed på rækkeniveau. Du kan finde flere oplysninger i [Sikkerhed på rækkeniveau med Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-rls). Bemærk, at sikkerhed på rækkeniveau tilmed kan anvendes på Direct Query-datakilder, og i det tilfælde fungerer PBIX-filer som en proxy, der muliggør sikkerhed.

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3: Overvågning af uautoriseret overførsel af følsomme data

**Vejledning**: Denne kontrol kan delvist opnås ved hjælp af Microsoft Cloud App Security-understøttelse af Power BI.

Når du bruger Cloud App Security med Power BI, kan du hjælpe med at beskytte dine Power BI-rapporter, -data og -tjenester mod utilsigtede lækager eller brud. Med Cloud App Security kan du oprette politikker for betinget adgang for din organisations data ved hjælp af kontrolelementerne for sessioner i realtid i Azure Active Directory (Azure AD), der hjælper med at sikre, at din Power BI-analyse er sikker. Når disse politikker er angivet, kan administratorer overvåge brugeradgang og -aktivitet, udføre risikoanalyse i realtid og angive mærkatspecifikke kontrolelementer.

Brug af 
- [Microsoft Cloud App Security-kontroller i Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4: Kryptér følsomme oplysninger under overførsel

**Vejledning**: For HTTP-trafik skal du sørge for, at alle klienter og datakilder, der opretter forbindelse til dine Power BI-ressourcer, kan forhandle TLS v1.2 eller nyere.

- [Gennemtvingelse af brug af TLS-version](https://docs.microsoft.com/power-bi/admin/service-admin-power-bi-security#enforcing-tls-version-usage)

- [Oplysninger om TLS-sikkerhed](https://docs.microsoft.com/security/engineering/solving-tls1-problem)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5: Kryptér følsomme inaktive data

**Vejledning**: Power BI krypterer inaktive og igangværende data. Power BI bruger som standard Microsoft-administrerede nøgler til kryptering af dine data. Organisationer kan vælge at bruge deres egne nøgler til kryptering af inaktivt brugerindhold i hele Power BI, fra rapportbilleder til importerede datasæt i Premium-kapaciteter.

- [Brug Bring Your Own Key i Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Delt

## <a name="asset-management"></a>Ressourcestyring

*Du kan finde flere oplysninger i [Azure Security Benchmark: Ressourcestyring](/azure/security/benchmarks/security-controls-v2-asset-management).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: Sørg for, at sikkerhedsteamet har indblik i risiciene for ressourcerne

**Vejledning**: Brug Azure Sentinel med dine Power BI Office Audit-logge for at sikre, at dit sikkerhedsteam har indblik i risiciene for dine Power BI-ressourcer.

- [Forbind Office 365-logge til Azure Sentinel](https://docs.microsoft.com/azure/sentinel/connect-office-365)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2: Sørg for, at sikkerhedsteamet har adgang til ressourcelager og metadata

**Vejledning**: Sørg for, at sikkerhedsteams har adgang til et løbende opdateret lager over Power BI Embedded-ressourcer. Sikkerhedsteams har ofte brug for dette lager for at evaluere organisationens potentielle eksponering for nye risici og som et input til løbende sikkerhedsforbedringer. 

Azure Resource Graph kan forespørge efter og finde alle Power BI Embedded-ressourcer i dine abonnementer.  

Organiser ressourcer logisk i henhold til din organisations taksonomi ved hjælp af tags samt andre metadata i Azure (navn, beskrivelse og kategori).  

- [Sådan opretter du forespørgsler med Azure Resource Graph Explorer](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

- [Vejledning til beslutning om navngivning og tagging af ressourcer](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=/azure/azure-resource-manager/management/toc.json)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="am-3-use-only-approved-azure-services"></a>AM-3: Brug kun godkendte Azure-tjenester

**Vejledning**: Power BI understøtter Azure Resource Manager-baserede udrulninger for Power BI Embedded, og du kan begrænse udrulningen af ressourcerne via Azure Policy ved hjælp af en brugerdefineret politikdefinition.

Brug Azure Policy til at overvåge og begrænse, hvilke tjenester brugerne kan klargøre i dit miljø. Brug Azure Resource Graph til at forespørge efter og finde ressourcer i deres abonnementer. Du kan også bruge Azure Monitor til at oprette regler, der udløser vigtige beskeder, når der registreres en ikke-godkendt tjeneste.

- [Sådan konfigureres og administreres Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage)

Sådan afvises en bestemt ressourcetype med
- [Azure Policy](https://docs.microsoft.com/azure/governance/policy/samples/built-in-policies#general)

Sådan oprettes forespørgsler med Azure
- [Resource Graph Explorer](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

## <a name="logging-and-threat-detection"></a>Logføring og trusselsregistrering

*Du kan finde flere oplysninger i [Azure Security Benchmark: Logføring og trusselsregistrering](/azure/security/benchmarks/security-controls-v2-logging-threat-protection).*

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2: Aktivér trusselsregistrering for identitets- og adgangsstyring i Azure

**Vejledning**: Videresend logge fra Power BI til din SIEM, som kan bruges til at konfigurere brugerdefinerede trusselsregistreringer. Derudover kan du bruge Microsoft Cloud App Security-kontroller (MCAS) i Power BI til at aktivere registrering af uregelmæssigheder ved hjælp af vejledningen [her](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls).

- [Spor brugeraktiviteter i Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3: Aktivér logføring for Azure-netværksaktiviteter

**Vejledning**: Power BI er et fuldt administreret SaaS-tilbud, og den underliggende netværkskonfiguration og logføring er Microsofts ansvar. For kunder, der anvender Private Links, er en del logføring og overvågning tilgængelig, hvilket kan konfigureres.

- [Logføring og overvågning af Private Link](https://docs.microsoft.com/azure/private-link/private-link-overview#logging-and-monitoring)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Delt

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4: Aktivér logføring for Azure-ressourcer

**Vejledning**: Med Power BI har du to muligheder for at spore brugeraktivitet: Power BI-aktivitetsloggen og den samlede overvågningslog. Disse logge indeholder begge en komplet kopi af Power BI-overvågningsdataene, men der er flere vigtige forskelle, som er opsummeret nedenfor.
 
Samlet overvågningslog:

 
- Omfatter hændelser fra SharePoint Online, Exchange Online, Dynamics 365 og andre tjenester foruden Power BI-overvågningshændelserne.

 
- Det er kun brugere, der har tilladelserne Skrivebeskyttede overvågningslogge eller Overvågningslogge, som har adgang, f.eks. globale administratorer og auditører.

 
- Globale administratorer og auditører kan søge i den samlede overvågningslog ved hjælp af Microsoft 365 Sikkerhedscenter og Microsoft 365 Overholdelsescenter.

 
- Globale administratorer og auditører kan downloade poster i overvågningsloggen ved hjælp af API'er og cmdlet'er til administration i Microsoft 365.

 
- Bevarer overvågningsdata i 90 dage.

 
- Bevarer overvågningsdata, selvom lejeren flyttes til et andet Azure-område.
 
Power BI-aktivitetslog:

 
- Omfatter kun Power BI-overvågningshændelser.

 
 
- Globale administratorer og administratorer af Power BI-tjenesten har adgang.

 
- Der er endnu ingen brugergrænseflade til at søge efter aktivitetsloggen.

 
- Globale administratorer og administratorer af Power BI-tjenesten kan downloade poster i aktivitetsloggen ved hjælp af en REST API i Power BI og cmdlet til administration.

 
- Bevarer aktivitetsdata i 30 dage.

 
- Bevarer ikke aktivitetsdata, når lejeren flyttes til et andet Azure-område.

- [Power BI-overvågningsdata](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Power BI-aktivitetslog](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Power BI-overvågningslog](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Delt

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5: Centraliser administration og analyse af sikkerhedslog

**Vejledning**: Power BI centraliserer logge to steder: Power BI-aktivitetslog og den samlede overvågningslog. Disse logge indeholder begge en komplet kopi af Power BI-overvågningsdataene, men der er flere vigtige forskelle, som er opsummeret nedenfor.
 

Samlet overvågningslog:

- Omfatter hændelser fra SharePoint Online, Exchange Online, Dynamics 365 og andre tjenester foruden Power BI-overvågningshændelser.

- Det er kun brugere, der har tilladelserne Skrivebeskyttede overvågningslogge eller Overvågningslogge, som har adgang, f.eks. globale administratorer og auditører.

- Globale administratorer og auditører kan søge i den samlede overvågningslog ved hjælp af Microsoft 365 Sikkerhedscenter og Microsoft 365 Overholdelsescenter.

- Globale administratorer og auditører kan downloade poster i overvågningsloggen ved hjælp af API'er og cmdlet'er til administration i Microsoft 365.

- Bevarer overvågningsdata i 90 dage.

- Bevarer overvågningsdata, selvom lejeren flyttes til et andet Azure-område.

 

Power BI-aktivitetslog:

- Omfatter kun Power BI-overvågningshændelser.

- Globale administratorer og administratorer af Power BI-tjenesten har adgang.

- Der er endnu ingen brugergrænseflade til at søge efter aktivitetsloggen.

- Globale administratorer og administratorer af Power BI-tjenesten kan downloade poster i aktivitetsloggen ved hjælp af en REST API i Power BI og cmdlet til administration.

- Bevarer aktivitetsdata i 30 dage.

- Bevarer ikke aktivitetsdata, når lejeren flyttes til et andet Azure-område.

- [Power BI-overvågningsdata](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Power BI-aktivitetslog](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Power BI-overvågningslog](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="lt-6-configure-log-storage-retention"></a>LT-6: Konfigurer lageropbevaring af log

**Vejledning**: Konfigurer politikker for lageropbevaring for dine Office-overvågningslogge i henhold til dine krav om overholdelse af angivne standarder, regler og virksomheder.

- [Politikker for opbevaring af Office-overvågningslog](https://docs.microsoft.com/microsoft-365/compliance/audit-log-retention-policies)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

## <a name="incident-response"></a>Svar på hændelse

*Du kan finde flere oplysninger i [Azure Security Benchmark: Svar på hændelse](/azure/security/benchmarks/security-controls-v2-incident-response).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: Forberedelse – opdater processen for svar på hændelse for Azure

**Vejledning**: Sørg for, at din organisation har processer til at svare på sikkerhedshændelser, har opdateret disse processer for Azure og udøver dem regelmæssigt for at sikre, at de er klar.

- [Implementer sikkerhed på tværs af virksomhedsmiljøet](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Vejledning til reference for svar på hændelse](https://docs.microsoft.com/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: Forberedelse – konfigurer meddelelse om hændelse

**Vejledning**: Konfigurer kontaktoplysninger for sikkerhedshændelser i Azure Security Center. Disse kontaktoplysninger bruges af Microsoft til at kontakte dig, hvis Microsoft Security Response Center (MSRC) registrerer, at en ulovlig og uautoriseret part har fået adgang til dine data. Du har også mulighed for at tilpasse vigtige beskeder om hændelser og meddelelser i forskellige Azure-tjenester baseret på behov for svar på hændelser. 

- [Sådan konfigureres Azure Security Center-sikkerhedskontakt](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: Registrering og analyse – opret hændelser baseret på vigtige beskeder af høj kvalitet

**Vejledning**: Sørg for, at du har en proces til at oprette vigtige beskeder af høj kvalitet og måle kvaliteten af beskederne. Dette giver dig mulighed for at få mere at vide om lektioner fra tidligere hændelser og prioritere vigtige beskeder til analytikere, så de ikke spilder tid på falske positiver.

Overvåg vigtige beskeder, der er relateret til Power BI i Microsoft Cloud App Security. Beskeder af høj kvalitet kan oprettes på baggrund af erfaringer fra tidligere hændelser, validerede communitykilder og værktøjer, der er designet til at generere og rydde op i vigtige beskeder ved at fusionere og korrelere forskelligartede signalkilder.

- [Overvåg vigtige beskeder i Cloud App Security](https://docs.microsoft.com/cloud-app-security/monitor-alerts)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: Registrering og analyse – undersøg en hændelse

**Vejledning**: Opret en vejledning til svar på hændelser for din organisation. Udfør regelmæssigt øvelser for at teste dine systemers funktionalitet til svar på hændelser. Identificer svage punkter og huller, og revider planen efter behov.

Sørg for, at der er nedskrevne planer for svar på hændelser, der definerer alle personalets roller samt faser i håndteringen/administrationen af hændelser fra registrering til gennemsyn efter hændelsen.

- [Oversigt over hændelser i Microsoft Threat Protection](https://docs.microsoft.com/microsoft-365/security/mtp/incidents-overview)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: Registrering og analyse – prioriter hændelser

**Vejledning**: Angiv kontekst til analytikere om, hvilke hændelser de skal fokusere på først, baseret på alvorsgraden af den vigtige besked og følsomheden af ressourcen. 

 
Microsoft Threat Protection anvender korrelationsanalyser og samler alle relaterede vigtige beskeder og undersøgelser fra forskellige produkter i én hændelse. Microsoft Threat Protection udløser også entydige vigtige beskeder om aktiviteter, der kun kan identificeres som skadelige pga. det omfattende indblik, som Microsoft Threat Protection har på tværs af hele ejendommen og pakken af produkter. Ved at gøre det fortæller Microsoft Threat Protection om den bredere angrebshistorie, hvilket giver en analytiker af sikkerhedshandlinger mulighed for at forstå og håndtere komplekse trusler på tværs af organisationen.

- [Prioriter hændelser i Microsoft Threat Protection](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue?view=o365-worldwide&amp;preserve-view=true)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: Opbevaring, udslettelse og genoprettelse – automatiser håndteringen af hændelser

**Vejledning**: Automatiser manuelle gentagne opgaver for at øge svartiden og reducere analytikernes byrde. Det tager længere tid at udføre manuelle opgaver, hvilket sinker hver hændelse og reducerer antallet af, hvor mange hændelser en analytiker kan håndtere. Manuelle opgaver øger også analytikernes træthed, hvilket øger risikoen for menneskelige fejl, der forårsager forsinkelser, og nedsætter analytikerens evne til at fokusere effektivt på komplekse opgaver.  
 
Brug funktioner til automatisering af arbejdsprocesser i Microsoft Threat Protection for at udløse undersøgelser og afhjælpning automatisk som svar på indgående sikkerhedsbeskeder. 
 
- [Automatiseret undersøgelse og svar i Microsoft Threat Protection](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

## <a name="posture-and-vulnerability-management"></a>Administration af niveau og sårbarhed

*Du kan finde flere oplysninger i [Azure Security Benchmark: Administration af niveau og sårbarhed](/azure/security/benchmarks/security-controls-v2-vulnerability-management).*

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1: Etabler sikre konfigurationer til Azure-tjenester 

**Vejledning**: Konfigurer din Power BI-tjeneste med de indstillinger, der passer til din organisation og din sikkerhedsholdning. Indstillinger for adgang til tjenesten og indhold samt sikkerhed af arbejdsområdet og programmer skal overvejes nøje. Se Power BI Security og Data Protection i whitepaper om udrulning af Power BI i store virksomheder.

- [Whitepaper om udrulning i store virksomheder](https://aka.ms/PBIEnterpriseDeploymentWP)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2: Bevar sikre konfigurationer for Azure-tjenester

**Vejledning**: Overvåg din Power BI-forekomst ved hjælp af REST API'er til administration af Power BI.

- [REST API'er til administration af Power BI](https://docs.microsoft.com/rest/api/power-bi/admin)

- [White om udrulning af Power BI i store virksomheder](https://aka.ms/PBIEnterpriseDeploymentWP)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: Udfør regelmæssig simulering af angreb

**Vejledning**: Udfør indtrængningstest eller red team-aktiviteter af dine Azure-ressourcer efter behov, og sørg for afhjælpning af alle kritiske sikkerhedsfund.

Følg operationsreglerne for Microsoft Cloud-indtrængningstest for at sikre, at dine indtrængningstest ikke overtræder Microsofts politikker. Brug Microsofts strategi for og udførelse af Red Teaming- og indtrængningstest af livewebsteder i forhold til Microsoft-administrerede cloudinfrastruktur, -tjenester og -programmer.

- [Indtrængningstest i Azure](https://docs.microsoft.com/azure/security/fundamentals/pen-testing)

- [Operationsregler for indtrængningstest](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Microsoft Cloud Red Teaming](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Delt

## <a name="backup-and-recovery"></a>Sikkerhedskopiering og genoprettelse

*Du kan finde flere oplysninger i [Azure Security Benchmark: Sikkerhedskopiering og genoprettelse](/azure/security/benchmarks/security-controls-v2-backup-recovery).*

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3: Valider alle sikkerhedskopier, herunder kundeadministrerede nøgler

**Vejledning**: Hvis du bruger funktionen Bring Your Own Key (BYOK) i Power BI skal du regelmæssigt kontrollere, at du har adgang til og kan gendanne dine kundeadministrerede nøgler.

- [BYOK i Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4: Afhjælp risikoen for mistede nøgler

**Vejledning**: Hvis du bruger funktionen Bring Your Own Key (BYOK) i Power BI skal du sikre, at Key Vault, der styrer dine kundeadministrerede nøgler, er konfigureret i henhold til vejledningen i dokumentationen til BYOK i Power BI nedenfor. Aktivér blød sletning og beskyttelse mod tømning i Azure Key Vault for at beskytte nøgler mod utilsigtet eller ondsindet sletning.

- [BYOK i Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

- [Sådan aktiveres blød sletning og beskyttelse mod tømning i Key Vault](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

For ressourcer om gatewaynøgle skal du sikre, at du følger vejledningen i dokumentationen til genoprettelsesnøgle til gateway nedenfor.

- [Genoprettelsesnøgle til datagateway i det lokale miljø](https://docs.microsoft.com/data-integration/gateway/service-gateway-recovery-key)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

## <a name="governance-and-strategy"></a>Styring og strategi

*Du kan finde flere oplysninger i [Azure Security Benchmark: Styring og strategi](/azure/security/benchmarks/security-controls-v2-governance-strategy).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: Definer strategi for ressourcestyring og databeskyttelse 

**Vejledning**: Sørg for at dokumentere og kommunikere en tydelig strategi for løbende overvågning og beskyttelse af systemer og data. Prioriter søgning, vurdering, beskyttelse og overvågning af forretningskritiske data og systemer. 

Denne strategi bør omfatte dokumenteret vejledning, politik og standarder for følgende elementer: 

-   Klassifikationsstandard for data i henhold til forretningsrisiciene

-   Indblik i risici og ressourcelager i organiseringen af sikkerhed 

-   Godkendelse af organiseringen af sikkerhed for Azure-tjenester til brug 

-   Sikkerhed af ressourcer i hele deres livscyklus

-   Påkrævet strategi for adgangskontrol i henhold til klassificering af data i organisationen

-   Brug af oprindelig funktionalitet til databeskyttelse i Azure og funktionalitet fra tredjepart

-   Krav til kryptering af data i forbindelse med data under overførsel og inaktive data

-   Passende kryptografiske standarder

Du kan finde flere oplysninger i følgende referencer:
- [Anbefaling af Azure-sikkerhedsarkitektur – lager, data og kryptering](https://docs.microsoft.com/azure/architecture/framework/security/storage-data-encryption?toc=/security/compass/toc.json&amp;bc=/security/compass/breadcrumb/toc.json)

- [Grundlæggende oplysninger om Azure-sikkerhed – sikkerhed, kryptering og lagring af data i Azure](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)

- [Cloud Adoption Framework – bedste praksis for kryptering og sikkerhed af data i Azure](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices?toc=/azure/cloud-adoption-framework/toc.json&amp;bc=/azure/cloud-adoption-framework/_bread/toc.json)

- [Azure Security Benchmark – ressourcestyring](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-asset-management)

- [Azure Security Benchmark – databeskyttelse](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-data-protection)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: Definer strategi for virksomhedssegmentering 

**Vejledning**: Etabler en strategi for hele virksomheden for at segmentere adgang til ressourcer ved hjælp af en kombination af kontroller til identitet, netværk, programmer, abonnementer, administrationsgrupper og andre kontroller.

Balancer nøje behovet for adskillelse af sikkerhed i forhold til behovet for daglig drift af systemer, der skal kommunikere med hinanden og have adgang til data.

Sørg for, at segmenteringsstrategien er implementeret på tværs af kontroltyper på en ensartet måde, herunder netværkssikkerhed, identitets- og adgangsmodeller samt programtilladelse/adgangsmodeller og kontroller af menneskelige processer.

- [Vejledning til segmenteringsstrategi i Azure (video)](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Vejledning til segmenteringsstrategi i Azure (dokument)](https://docs.microsoft.com/security/compass/governance#enterprise-segmentation-strategy)

- [Afstem netværkssegmentering i forhold til virksomhedens segmenteringsstrategi](https://docs.microsoft.com/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: Definer en strategi for administration af sikkerhedsniveau

**Vejledning**: Mål og afhjælp løbende risici for dine individuelle ressourcer og de miljø, de hostes i. Prioriter ressourcer med høj værdi og angrebsoverflader, der er meget eksponeret, f.eks. publicerede programmer, punkter for indgående data og udgående data på netværk, slutpunkter for bruger og administrator osv.

- [Azure Security Benchmark – administration af niveau og sårbarhed](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-posture-vulnerability-management)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: Afstem roller og ansvar i organisationen

**Vejledning**: Sørg for at dokumentere og kommunikere en tydelig strategi for roller og ansvar i organiseringen af sikkerhed. Prioriter at angive tydeligt ansvar for sikkerhedsbeslutninger, at uddanne alle i modellen for delt ansvar samt at uddanne tekniske teams i teknologien til at beskytte cloudmiljøet.

- [Bedste praksis for sikkerhed i Azure 1 – mennesker: Uddan teams i cloudsikkerhedsrejsen](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Bedste praksis for sikkerhed i Azure 2 – mennesker: Uddan teams i teknologi til cloudsikkerhed](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Bedste praksis for sikkerhed i Azure 3 – processer: Tildel ansvar for sikkerhedsbeslutninger i cloudmiljøet](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="gs-5-define-network-security-strategy"></a>GS-5: Definer en strategi for netværkssikkerhed

**Vejledning**: Etabler en tilgang til netværkssikkerhed i Azure som en del af din organisations overordnede sikkerhedsstrategi for adgangskontrol.  

Denne strategi bør omfatte dokumenteret vejledning, politik og standarder for følgende elementer: 

-   Centraliseret netværksadministration og sikkerhedsansvar

-   Model til segmentering af virtuelt netværk afstemt i forhold til virksomhedens segmenteringsstrategi

-   Afhjælpningsstrategi i forskellige trussels- og angrebsscenarier

-   Strategi for Internet Edge samt indgående data og udgående data

-   Strategi for indbyrdes forbindelse mellem hybridcloudmiljøet og det lokale miljø

-   Opdaterede artefakter for netværkssikkerhed (f.eks. netværksdiagrammer, netværksarkitektur til reference)

Du kan finde flere oplysninger i følgende referencer:
- [Bedste praksis for sikkerhed i Azure 11 – arkitektur. Enkelt samlet sikkerhedsstrategi](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure Security Benchmark – netværkssikkerhed](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-network-security)

- [Oversigt over netværkssikkerhed i Azure](https://docs.microsoft.com/azure/security/fundamentals/network-overview)

- [Strategi for netværksarkitektur i virksomheden](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: Definer en strategi for identitet og privilegeret adgang

**Vejledning**: Etabler tilgange til identitet og privilegeret adgang i Azure som en del af din organisations overordnede sikkerhedsstrategi for adgangskontrol.  

Denne strategi bør omfatte dokumenteret vejledning, politik og standarder for følgende elementer: 

-   Et centraliseret identitets- og godkendelsessystem og dets indbyrdes forbundne forbindelse med andre interne og eksterne identitetssystemer

-   Stærke godkendelsesmetoder i forskellige use cases og forhold

-   Beskyttelse af brugere med mange tilladelser

-   Overvågning og håndtering af uregelmæssige brugeraktiviteter  

-   Proces for afstemning og gennemsyn af adgang og brugeridentitet

Du kan finde flere oplysninger i følgende referencer:

- [Azure Security Benchmark – identitetsstyring](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-identity-management)

- [Azure Security Benchmark – privilegeret adgang](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-privileged-access)

- [Bedste praksis for sikkerhed i Azure 11 – arkitektur. Enkelt samlet sikkerhedsstrategi](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Oversigt over sikkerhed og identitetsstyring i Azure](https://docs.microsoft.com/azure/security/fundamentals/identity-management-overview)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: Definer en strategi for logføring og svar på trusler

**Vejledning**: Etabler en strategi for logføring og svar på trusler, så du hurtigt kan registrere og afhjælpe trusler, mens du opfylder kravene til overholdelse af angivne standarder. Prioriter at give analytikere vigtige beskeder af høj kvalitet og problemfrie oplevelser, så de kan fokusere på trusler i stedet for integration og manuelle trin. 

Denne strategi bør omfatte dokumenteret vejledning, politik og standarder for følgende elementer: 

-   Organisationens rolle og ansvar i sikkerhedshandlingerne 

-   En veldefineret proces for svar på hændelser afstemt i forhold til NIST eller en anden branchestruktur 

-   Registrer og opbevar logge for at understøtte trusselsregistrering, svar på hændelser og behov for overholdelse af angivne standarder

-   Centraliseret indblik i og korrelation af oplysninger om trusler ved hjælp af SIEM, oprindelig funktionalitet i Azure og andre kilder 

-   Planlæg kommunikation og meddelelser med dine kunder, leverandører og offentlige interessenter

-   Brug af en oprindelig platform i Azure og tredjepartsplatforme til håndtering af hændelser, f.eks. logføring og trusselsregistrering, tekniske data samt afhjælpning udryddelse af angreb

-   Processer til håndtering af hændelser og aktiviteter efter hændelser, f.eks. erfaringer og opbevaring af beviser

Du kan finde flere oplysninger i følgende referencer:

- [Azure Security Benchmark – logføring og trusselsregistrering](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-logging-threat-detection)

- [Azure Security Benchmark – svar på hændelser](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-incident-response)

- [Bedste praksis for sikkerhed i Azure 4 – processer. Opdater processer for svar på hændelser i cloudmiljøet](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Vejledning til Azure Adoption Framework, logføring og rapportering af beslutninger](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Virksomhedsskala, administration og overvågning i Azure](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Overvågning af Azure Security Center**: Ikke tilgængelig

**Ansvar**: Kunde

## <a name="next-steps"></a>Næste trin

- Se [Oversigt over Azure Security Benchmark V2](/azure/security/benchmarks/overview)
- Få mere at vide om [Azure-sikkerhedsbaselines](/azure/security/benchmarks/security-baselines-overview)
