---
title: Integreret indhold i dit program til integreret analyse i Power BI for dine kunder
description: Lær, hvordan du integrerer en rapport, et dashboard eller et felt i et eksempel på integreret analyse i Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/22/2020
ms.openlocfilehash: 5417266658a493bc81da882761431aa3db072dbe
ms.sourcegitcommit: 1691ce556ab5b22e6f9d06086a054d165d482809
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/23/2020
ms.locfileid: "97745110"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>Selvstudium: Integrer Power BI-indhold ved hjælp af et eksempelprogram til *integrering for dine kunder*

Med **integreret analyse** og **Power BI Embedded** (Azure-tilbuddet) kan du integrere Power BI-indhold såsom rapporter, dashboards og felter i dit program.

I dette selvstudium lærer du, hvordan du:
>[!div class="checklist"]
>* Konfigurer dit integrerede miljø.
>* Konfigurer et eksempelprogram til *integrering for dine kunder* (også kendt som *programmet ejer data*).

Brugerne behøver ikke at logge på Power BI eller have en Power BI-licens for at bruge dit program.

Vi anbefaler, at du bruger metoden til *integrering for dine kunder* til at integrere dit Power BI-indhold, hvis du er en uafhængig softwareproducent eller en udvikler, der gerne vil oprette programmer til tredjeparter.

## <a name="code-sample-specifications"></a>Specifikationer for kodeeksempel

Dette selvstudium indeholder instruktioner til, hvordan du konfigurerer et eksempelprogram til *integrering for dine kunder* på et af følgende sprog:

* .NET Framework
* .NET Core
* Java
* Node JS
* Python

Kodeeksemplerne understøtter følgende browsere:

* Google Chrome

* Microsoft Edge

* Mozilla Firefox

## <a name="prerequisites"></a>Forudsætninger

Før du starter dette selvstudium, skal du bekræfte, at du har både de Power BI- og kodeafhængigheder, der er angivet nedenfor:

* **Power BI-afhængigheder**

    * Din egen [Azure Active Directory-lejer](create-an-azure-active-directory-tenant.md).

    * Du skal have en af følgende for at godkende dit program i Power BI:

        * [Tjenesteprincipal](embed-service-principal.md) – Et objekt for en Azure Active Directory-[tjenesteprincipal](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) (Azure AD), der giver Azure AD mulighed for at godkende dit program.

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)-licens – Dette vil være din **masterbruger**, og dit program bruger den til at godkende i Power BI.

        * En [Premium Per User-licens (PPU)](../../admin/service-premium-per-user-faq.md) til Power BI – Dette vil være din **masterbruger**, og dit program bruger den til at godkende i Power BI.

    >[!NOTE]
    >Hvis du vil [flytte til produktion](move-to-production.md), skal du bruge en [kapacitet](embedded-capacity.md).

* **Kodeafhængigheder**

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)
    
    
    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (eller nyere)
    
    * Et integreret udviklingsmiljø (IDE). Vi anbefaler, at du bruger en af følgende:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK (eller JRE)](https://www.oracle.com/java/technologies/)
    
    * [Eclipse IDE](https://www.eclipse.org/downloads/packages/) – Bekræft, at du har *Eclipse for Java EE Developers* (Enterprise Edition)
    
    * [Binære Apache Tomcat-distributioner](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node JS](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * Et integreret udviklingsmiljø (IDE). Vi anbefaler, at du bruger en af følgende:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/) (eller nyere)
    
        >[!NOTE]
        >* Hvis det er første gang, du installerer *Python*, skal du vælge indstillingen **Føj Python til PATH** for at føje installationen til variablen `PATH`.
        >* Hvis du allerede har installeret *Python*, skal du bekræfte, at variablen `PATH` indeholder installationsstien. Du kan finde flere oplysninger i [Excursus: Setting environment variables](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables) (Excursus: Angivelse af miljøvariabler) i dokumentationen til Python (dette link refererer til Python 3).
    
    * Et integreret udviklingsmiljø (IDE). Vi anbefaler, at du bruger en af følgende:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>Metode

Følg disse trin for at oprette et eksempelprogram til *integrering for din kunder*:

1. [Vælg en godkendelsesmetode](#step-1---select-your-authentication-method).

2. [Registrer et Azure AD-program](#step-2---register-an-azure-ad-application).

3. [Opret et Power BI-arbejdsområde](#step-3---create-a-power-bi-workspace).

4. [Opret og publicer en Power BI-rapport](#step-4---create-and-publish-a-power-bi-report).

5. [Hent de integrerede parameterværdier](#step-5---get-the-embedding-parameter-values).

6. [API-adgang til tjenesteprincipal](#step-6---service-principal-api-access)
 
7. [Giv adgang til arbejdsområde](#step-7---enable-workspace-access).

8. [Integrer dit indhold](#step-8---embed-your-content).

## <a name="step-1---select-your-authentication-method"></a>Trin 1 – Vælg en godkendelsesmetode

Din integrerede løsning varierer, afhængigt af den valgte godkendelsesmetode. Det er derfor vigtigt at forstå forskellene mellem godkendelsesmetoderne og beslutte, hvilken metode der passer bedst til din løsning.

I nedenstående tabel beskrives nogle få vigtige forskelle mellem godkendelsesmetoderne [tjenesteprincipal](embed-service-principal.md) og **masterbruger**.

|Overvejelse  |Tjenesteprincipal  |Masterbruger  |
|---------|---------|---------|
|Mekanisme     |[Objektet for din tjenesteprincipal](/azure/active-directory/develop/app-objects-and-service-principals.md#service-principal-object) for dit Azure AD-program giver Azure AD mulighed for at godkende dit integrerede løsningsprogram i Power BI.        |Azure AD-programmet bruger legitimationsoplysningerne (brugernavn og adgangskode) for en Power BI-bruger til at godkende i Power BI.         |
|Sikkerhed     |*Tjenesteprincipal* er den anbefalede godkendelsesmetode for Azure AD. Hvis du bruger en tjenesteprincipal*, kan du godkende ved hjælp af enten en *programhemmelighed* eller et *certifikat*.</br></br>Dette selvstudium indeholder kun en beskrivelse af brug af en *tjenesteprincipal* med en *programhemmelighed*. Hvis du vil integrere ved hjælp af en *tjenesteprincipal* og et *certifikat*, skal du se artiklen om [tjenesteprincipal med et certifikat](embed-service-principal-certificate.md).         |Denne godkendelsesmetode anses ikke for at være lige så sikker som brug af en *tjenesteprincipal*. Det skyldes, at du skal være påpasselig med legitimationsoplysningerne for *masterbrugeren* (brugernavn og adgangskode). Du må f.eks. ikke fremvise dem i dit integreringsprogram, og du bør ændre adgangskoden ofte.         |
|Delegerede tilladelser i Azure AD |Ikke påkrævet. |Din *masterbruger* eller en administrator skal give deres samtykke til, at dit program kan få adgang til REST API-[tilladelser](/azure/active-directory/develop/v2-permissions-and-consent) til Power BI (også kendt som områder). For eksempel *Report.ReadWrite.All*. |
|Adgang til Power BI-tjenesten |Du kan ikke få adgang til Power BI-tjenesten med en *tjenesteprincipal*.|Du kan få adgang til Power BI-tjenesten med legitimationsoplysningerne for din *masterbruger*.|
|Licens     |Kræver ikke en Pro-licens. Du kan bruge indhold fra alle arbejdsområder, som du er medlem eller administrator af.         |Kræver en [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)-licens.         |

## <a name="step-2---register-an-azure-ad-application"></a>Trin 2 – Registrer et Azure AD-program

Når du registrerer dit program med Azure AD, kan du:
> [!div class="checklist"]
>* Etablere en identitet for dit program
>* Give dit program adgang til [REST API'erne til Power BI](/rest/api/power-bi/)
>* Angive [REST-tilladelser til Power BI](/azure/active-directory/develop/v2-permissions-and-consent) for programmet – hvis du bruger en *masterbruger*

Hvis du vil registrere dit program i Azure AD, skal du følge vejledningen under [Registrer dit program](register-app.md).

>[!NOTE]
>Før du registrerer dit program, skal du beslutte, hvilken godkendelsesmetode du vil bruge, *tjenesteprincipal* eller *masterbruger*.

## <a name="step-3---create-a-power-bi-workspace"></a>Trin 3 – Opret et Power BI-arbejdsområde

Power BI opbevarer dine rapporter, dashboards og felter i et arbejdsområde. Hvis du vil integrere disse elementer, skal du oprette dem og uploade dem til et arbejdsområde.

>[!TIP]
>Hvis du allerede har et arbejdsområde, kan du springe dette trin over.

Gør følgende for at oprette et arbejdsområde:

1. Log på Power BI.

2. Vælg **Arbejdsområder**.

3. Vælg **Opret et arbejdsområde**.

4. Navngiv dit arbejdsområde, og vælg **Gem**.

## <a name="step-4---create-and-publish-a-power-bi-report"></a>Trin 4 – Opret og publicer en Power BI-rapport

Det næste trin er at oprette en rapport og uploade den til dit arbejdsområde. Du kan [oprette din egen rapport](/powerbi-docs/fundamentals/desktop-getting-started#build-reports) ved hjælp af Power BI Desktop og derefter [publicere](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) den til dit arbejdsområde. Eller du kan uploade en eksempelrapport til dit arbejdsområde.

>[!Tip]
>Hvis du allerede har et arbejdsområde med en rapport, kan du springe dette trin over.

Hvis du vil downloade en eksempelrapport og publicere den i dit arbejdsområde, skal du følge disse trin:

1. Åbn GitHub-mappen [Power BI Desktop-eksempler](https://github.com/Microsoft/PowerBI-Desktop-Samples).

2. Vælg **Kode**, og vælg derefter **Download zip**.

    :::image type="content" source="media/embed-sample-for-customers/download-sample-report.png" alt-text="Et skærmbillede af indstillingen til download af ZIP i GitHub med Power BI Desktop-eksempler":::

3. Udpak den downloadede ZIP, og naviger til mappen **Eksempelrapporter**.

4. Vælg en rapport, der skal integreres, og [publicer](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) den i dit arbejdsområde.

## <a name="step-5---get-the-embedding-parameter-values"></a>Trin 5 – Hent de integrerede parameterværdier

Hvis du vil integrere dit indhold, skal du hente bestemte parameterværdier. Nedenstående tabel viser de påkrævede værdier og angiver, om de gælder for godkendelsesmetoden med *tjenesteprincipal*, godkendelsesmetoden *masterbruger* eller begge.

Før du integrerer dit indhold, skal du sørge for, at du har alle de værdier, der er angivet nedenfor. Nogle af værdierne vil variere, afhængigt af den valgte godkendelsesmetode.

|Parameter   |Tjenesteprincipal   |Masterbruger  |
|-------------------|---|---|
|[Klient-id](#client-id) |![Gælder for.](../../media/yes.png) |![Gælder for.](../../media/yes.png) |
|[Arbejdsområde-id](#workspace-id)     |![Gælder for.](../../media/yes.png) |![Gælder for.](../../media/yes.png) |
|[Rapport-id](#report-id)           |![Gælder for.](../../media/yes.png) |![Gælder for.](../../media/yes.png) |
|[Klienthemmelighed](#client-secret) |![Gælder for.](../../media/yes.png) |![Gælder ikke for.](../../media/no.png) |
|[Lejer-id](#tenant-id)                 |![Gælder for.](../../media/yes.png) |![Gælder ikke for.](../../media/no.png) |
|[Power BI-brugernavn](#power-bi-username-and-password)   |![Gælder ikke for.](../../media/no.png) |![Gælder for.](../../media/yes.png) |
|[Power BI-adgangskode](#power-bi-username-and-password)   |![Gælder ikke for.](../../media/no.png) |![Gælder for.](../../media/yes.png) |

### <a name="client-id"></a>Klient-id

>[!TIP]
>**Gælder for:** ![Gælder for.](../../media/yes.png)Tjenesteprincipal ![Gælder for.](../../media/yes.png)Masterbruger

Følg disse trin for at hente GUID for klient-id'et (også kaldet *program-id*):

1. Log på [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Søg efter **Programregistreringer**, og vælg linket **Programregistreringer**.

3. Vælg det Azure AD-program, du bruger til at integrere dit Power BI-indhold.

4. I afsnittet **Oversigt** skal du kopiere GUID for **program-id'et (klient)** .

### <a name="workspace-id"></a>Id for arbejdsområde

>[!TIP]
>**Gælder for:** ![Gælder for.](../../media/yes.png)Tjenesteprincipal ![Gælder for.](../../media/yes.png)Masterbruger

Følg disse trin for at hente GUID for arbejdsområde-id'et:

1. Log på Power BI-tjenesten.

2. Åbn den rapport, du vil integrere.

3. Kopiér GUID'et fra URL-adressen. GUID'et er tallet mellem **/groups/** og **/reports/** .

    :::image type="content" source="media/embed-sample-for-customers/workspace-id.png" alt-text="Et skærmbillede, der viser GUID for arbejdsområde-id'et i for URL-adressen til Power BI-tjenesten":::

### <a name="report-id"></a>Rapport-id

>[!TIP]
>**Gælder for:** ![Gælder for.](../../media/yes.png)Tjenesteprincipal ![Gælder for.](../../media/yes.png)Masterbruger

1. Log på Power BI-tjenesten.

2. Åbn den rapport, du vil integrere.

3. Kopiér GUID'et fra URL-adressen. GUID'et er tallet mellem **/reports/** og **/ReportSection**.

    :::image type="content" source="media/embed-sample-for-customers/report-id.png" alt-text="Et skærmbillede, der viser GUID for rapport-id'et i for URL-adressen til Power BI-tjenesten":::

### <a name="client-secret"></a>Klienthemmelighed

>[!TIP]
>**Gælder for:** ![Gælder for.](../../media/yes.png)Tjenesteprincipal ![Gælder ikke for.](../../media/no.png)Masterbruger

Følg disse trin for at hente klienthemmeligheden:

1. Log på [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Søg efter **Programregistreringer**, og vælg linket **Programregistreringer**.

3. Vælg det Azure AD-program, du bruger til at integrere dit Power BI-indhold.

4. Under **Administrer** skal du vælge **Certifikater og hemmeligheder**.

5. Under **Klienthemmeligheder** skal du vælge **Ny klienthemmelighed**.

6. I pop op-vinduet **Tilføj en klienthemmelighed** skal du angive en beskrivelse af din programhemmelighed, vælge, hvornår programhemmeligheden udløber, og vælge **Tilføj**.

7. I afsnittet **Klienthemmeligheder** skal du kopiere strengen i kolonnen **Værdi** i den nyoprettede programhemmelighed. Værdien for klienthemmeligheden er dit *klient-id*.

### <a name="tenant-id"></a>Lejer-id

>[!TIP]
>**Gælder for:** ![Gælder for.](../../media/yes.png)Tjenesteprincipal ![Gælder ikke for.](../../media/no.png)Masterbruger

Følg disse trin for at hente GUID for lejer-id'et:

1. Log på [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Søg efter **Programregistreringer**, og vælg linket **Programregistreringer**.

3. Vælg det Azure AD-program, du bruger til at integrere dit Power BI-indhold.

4. I afsnittet **Oversigt** skal du kopiere GUID for **mappe-id'et (lejer)** .

### <a name="power-bi-username-and-password"></a>Brugernavn og adgangskode til Power BI

>[!TIP]
>**Gælder for:** ![Gælder ikke for.](../../media/no.png)Tjenesteprincipal ![Gælder for.](../../media/yes.png)Masterbruger

Hent *brugernavnet* og *adgangskoden* for den Power BI-bruger, du bruger som **masterbruger**. Det er den samme bruger, som du brugte til at oprette et arbejdsområde og uploade en rapport til, i Power BI-tjenesten.

## <a name="step-6---service-principal-api-access"></a>Trin 6 – API-adgang til tjenesteprincipal

>[!TIP]
>**Gælder for:** ![Gælder for.](../../media/yes.png)Tjenesteprincipal ![Gælder ikke for.](../../media/no.png)Masterbruger
>
>Dette trin er kun relevant, hvis du bruger godkendelsesmetoden *tjenesteprincipal*. Hvis du bruger en *masterbruger*, kan du springe dette trin over og fortsætte med [Trin 7 – Giv adgang til arbejdsområdet](#step-7---enable-workspace-access).

Hvis et Microsoft Azure AD-program skal kunne få adgang til Power BI-indholdet og API'erne, skal en Power BI-administrator have mulighed for at aktivere adgangen til tjenesteprincipalen i Power BI-administrationsportalen. Hvis du ikke er administrator af din lejer, kan du få lejerens administrator til at aktivere *Lejerindstillingerne* for dig.
        
1. I *Power BI-tjenesten* skal du vælge **Indstillinger** > **Indstillinger** > **Administrationsportal**.
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="Et skærmbillede, der viser menuen for administratorindstillinger i menuen Indstillinger for Power BI-tjenesten":::
        
2. Vælg **Lejerindstillinger**, og rul derefter ned til afsnittet **Udviklerindstillinger**.
        
3. Udvid **Giv tjenesteprincipaler tilladelse til at bruge API'er til Power BI**, og aktivér denne indstilling.
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="Et skærmbillede, der viser, hvordan du aktiverer udviklerindstillinger i menuen for lejerindstillinger i Power BI-tjenesten":::
        
>[!NOTE]
>Når du bruger en *tjenesteprincipal*, anbefales det at begrænse adgangen til lejerindstillingerne ved hjælp af en *sikkerhedsgruppe*. Du kan få mere at vide om denne funktion ved at se disse afsnit i artiklen [Tjenesteprincipal](embed-service-principal.md):
> * [Opret en Azure AD-sikkerhedsgruppe](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [Aktivér administrationsindstillingerne for Power BI-tjenesten](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>Trin 7 – Giv adgang til arbejdsområde

Hvis du vil aktivere artefakterne for adgang til dit Azure AD-program, f.eks. rapporter, dashboards og datasæt i Power BI-tjenesten, skal du tilføje *tjenesteprincipalen* eller *masterbrugeren* som et *medlem* eller *administrator* til dit arbejdsområde.

1. Log på Power BI-tjenesten.

2. Rul til det arbejdsområde, du vil aktivere adgang til, og vælg **Adgang til arbejdsområde** i menuen **Mere**.

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Skærmbillede, der viser arbejdsområdets adgangsknap i menuen Mere i et Power BI-arbejdsområde.":::

3. Afhængigt af hvilken godkendelsesmetode du bruger, skal du i ruden **Adgang** kopiere *tjenesteprincipalen* eller *masterbrugeren* til tekstfeltet **Angiv mailadresse**.

    >[!NOTE]
    >Hvis du bruger en *tjenesteprincipal*, er dens navn det navn, du gav dit Azure AD-program.

5. Vælg **Tilføj**

## <a name="step-8---embed-your-content"></a>Trin 8 – Integrer dit indhold

Det integrerede Power BI-eksempelprogram giver dig mulighed for at oprette et Power BI-program til *integrering for dine kunder*.

Følg disse trin for at ændre eksempelprogrammet til *integrering for dine kunder*, så du kan integrere din Power BI-rapport.  

1. Åbn mappen [Power BI-udviklereksempler](https://github.com/microsoft/PowerBI-Developer-Samples).

2. Vælg **Kode**, og vælg derefter **Download zip**.

    :::image type="content" source="media/embed-sample-for-customers/developer-samples.png" alt-text="Et skærmbillede af indstillingen til download af ZIP i GitHub med Power BI-udviklereksempler":::

3. Udpak den downloadede ZIP, og naviger til mappen **PowerBI-Developer-Samples-master**.

4. Afhængigt af det sprog du vil have, at dit program skal bruge, skal du åbne en af disse mapper:

* .NET Core
* .NET Framework
* Java
* Node JS
* Python
    >[!NOTE]
    >Eksempelprogrammerne til *integrering for dine kunder* understøtter kun de sprog, der er angivet ovenfor. Eksempelprogrammet *React TS* understøtter kun løsningen til *[integrering for din organisation](embed-sample-for-your-organization.md)* .

5. Åbn mappen **Integrer for dine kunder**.

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. Åbn *eksempelprogrammet til integrering for dine kunder* ved hjælp af en af disse metoder:

    * Hvis du bruger [Visual Studio](https://visualstudio.microsoft.com/), skal du åbne filen **AppOwnsData.sln**.

    * Hvis du bruger [Visual Studio Code](https://code.visualstudio.com/), skal du åbne mappen **Programmet ejer data**.

7. Åbn **appsettings.json**.

8. Afhængigt af din godkendelsesmetode skal du udfylde følgende parameterværdier:

    |Parameter            |Tjenesteprincipal  |Masterbruger  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |ServicePrincipal         |MasterUser         |
    |`ClientId`           |[Klient-id'et](#client-id) for dit Azure AD-program         |[Klient-id'et](#client-id) for dit Azure AD-program         |
    |`TenantId`           |[Lejer-id'et](#tenant-id) for dit Azure AD         |I/T         |
    |`PbiUsername`        |I/T         |Brugernavnet for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`PbiPassword`        |I/T         |Adgangskoden for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`ClientSecret`       |[Klienthemmeligheden](#client-secret) for dit Azure AD         |I/T         |
    |`WorkspaceId`        |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)          |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)         |
    |`ReportId`           |Id'et for den rapport du integrerer – se [rapport-id](#report-id)            |Id'et for den rapport du integrerer – se [rapport-id](#report-id)         |

9. Kør projektet ved at vælge den relevante indstilling:

    * Hvis du bruger **Visual Studio**, skal du vælge **IIS Express** (afspil).

    * Hvis du bruger **Visual Studio Code**, skal du vælge **Kør > Start fejlfinding**.

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. Åbn filen **AppOwnsData.sln** ved hjælp af [Visual Studio](https://visualstudio.microsoft.com/).

7. Åbn **Web.config**.

8. Afhængigt af din godkendelsesmetode skal du udfylde følgende parameterværdier:

    |Parameter            |Tjenesteprincipal  |Masterbruger  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`applicationId`           |[Klient-id'et](#client-id) for dit Azure AD-program         |[Klient-id'et](#client-id) for dit Azure AD-program         |
    |`workspaceId`        |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)          |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)         |
    |`reportId`           |Id'et for den rapport du integrerer – se [rapport-id](#report-id)            |Id'et for den rapport du integrerer – se [rapport-id](#report-id)         |
    |`pbiUsername`        |I/T         |Brugernavnet for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |I/T         |Adgangskoden for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`applicationSecret`       |[Klienthemmeligheden](#client-secret) for dit Azure AD         |I/T         |
    |`tenant`           |[Lejer-id'et](#tenant-id) for dit Azure AD         |I/T         |

9. Kør projektet ved at vælge **IIS Express** (afspil).

>[!NOTE]
>Hvis du ikke kan se den integrerede rapport, når du kører eksempelprogrammet, skal du opdatere Power BI-pakkerne ved at følge disse trin:
>1. Højreklik på projektnavnet (AppOwnesData), og vælg **Administrer NuGet-pakker**.
>2. Søg efter **Power BI JavaScript**, og geninstaller derefter pakken.
>
>Du kan finde flere oplysninger under [Sådan geninstallerer og opdaterer du pakker](/nuget/consume-packages/reinstalling-and-updating-packages).

# <a name="java"></a>[Java](#tab/java)

6. Åbn **Eclipse**, og følg nedenstående vejledning.

    >[!NOTE]
    >Du finder vejledningerne til Java-*eksempelprogrammet til integrering for dine kunder* i [Eclipse IDE til Java EE-udviklere](https://www.eclipse.org/downloads/packages/) (Enterprise Edition). Hvis du bruger et andet program, skal du selv konfigurere det.

7. Føj Tomcat-serveren til Eclipse:

    a. Vælg **Vindue** > **Vis visning** > **Servere**.

    b. Under fanen Servere skal du vælge **Ingen servere er tilgængelige. Klik på dette link for at oprette en ny server**.

    c. I vinduet **Definer en ny server** skal du udvide **Apache** og vælge den Tomcat-server, du kører på maskinen. For eksempel *Tomcat v9.0 Server*.

    d. Vælg **Næste**.

    e. I vinduet **Tomcat Server** skal du vælge **Gennemse** og navigere til den mappe, der indeholder Tomcat-serveren.

    f. I vinduet **Tomcat Server** skal du vælge **Installerede JRE'er**.

    eks. I vinduet **Installerede JRE'er** skal du vælge den tilgængelige *jre* og vælge **Anvend og luk**.

    h. I vinduet **Tomcat Server** skal du vælge **Udfør**. Du kan se Tomcat-serveren under fanen *Servere*.

8. Åbn projektet i Eclipse:

    >[!IMPORTANT]
    >Der kan opstå problemer i Eclipse, hvis navnet på stien er for lang. Hvis du vil undgå dette problem, skal du bekræfte, at mappen til dit eksempelprogram ikke er indlejret for dybt i computerens mappestruktur.

    a. Vælg **Filer**, og vælg derefter **Åbn projekter fra filsystem**.

    b. I vinduet **Importér projekter fra filsystem eller arkiv** skal du vælge **Mappe** og åbne mappen **AppOwnsData**.

    c. Vælg **Udfør**.

9. Føj Tomcat-serveren til projektet:

    a. I ruden **Package Explorer** skal du højreklikke på **AppOwnsData** og vælge **Egenskaber**.

    b. I vinduet **Egenskaber for AppOwnesData** skal du vælge **Målrettede kørsler** og derefter vælge **Apache Tomcat**. Dette valg omfatter den version af *Apache Tomcat*, du bruger, f.eks. *Apache Tomact v9.0*.

    c. Vælg **Anvend og luk**.

10. Udfyld de påkrævede parametre

    a. I **Package Explorer** skal du udvide projektet **AppOwnsData**.

    b. Udvid **Java-ressourcer**.

    c. Udvid **src**.

    d. Udvid **com.embedsample.appoensdata.config**.

    e. Åbn **Config.java**.

    f. Afhængigt af din godkendelsesmetode skal du udfylde følgende parameterværdier:

    |Parameter            |Tjenesteprincipal  |Masterbruger  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`workspaceId`        |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)          |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)         |
    |`reportId`           |Id'et for den rapport du integrerer – se [rapport-id](#report-id)            |Id'et for den rapport du integrerer – se [rapport-id](#report-id)         | 
    |`clientId`           |[Klient-id'et](#client-id) for dit Azure AD-program         |[Klient-id'et](#client-id) for dit Azure AD-program         |
    |`pbiUsername`        |I/T         |Brugernavnet for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |I/T         |Adgangskoden for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`tenantId`           |[Lejer-id'et](#tenant-id) for dit Azure AD         |I/T         |
    |`appSecret`       |[Klienthemmeligheden](#client-secret) for dit Azure AD         |I/T         |

11. Kør projektet

    a. I **Package Explorer** skal du højreklikke på **AppOwnesData**.

    b. Vælg **Kør som**  > **Kør på server**.

    c. I vinduet **Kør på server** skal du vælge **Vælg en eksisterende server** og vælge *Tomcat*-serveren.

    d. Vælg **Udfør**.

# <a name="node-js"></a>[Node JS](#tab/node-js)

6. Åbn mappen **Programmet ejer data** ved hjælp af dine foretrukne IDE. Vi anbefaler, at du bruger en af følgende:

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. Åbn en terminal, og installér de påkrævede afhængigheder ved at udføre: `npm install`.

8. Udvid mappen **Config**, og åbn **config.json**.

9. Afhængigt af din godkendelsesmetode skal du udfylde følgende parameterværdier:

    |Parameter            |Tjenesteprincipal  |Masterbruger  |
    |---------------------|---------|---------|
    |`authenticationMode` |ServicePrincipal         |MasterUser         |
    |`clientId`           |[Klient-id'et](#client-id) for dit Azure AD-program         |[Klient-id'et](#client-id) for dit Azure AD-program         |
    |`workspaceId`        |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)          |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)         |
    |`reportId`           |Id'et for den rapport du integrerer – se [rapport-id](#report-id)            |Id'et for den rapport du integrerer – se [rapport-id](#report-id)         |
    |`pbiUsername`        |I/T         |Brugernavnet for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |I/T         |Adgangskoden for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`clientSecret`       |[Klienthemmeligheden](#client-secret) for dit Azure AD         |I/T         |
    |`tenantId`           |[Lejer-id'et](#tenant-id) for dit Azure AD         |I/T         |

10. Kør projektet ved at gøre følgende:

    a. På IDE-terminalen skal du udføre `npm start`.

    b. Åbn en ny fane i browseren, og naviger til [http://localhost:5300](http://localhost:5300).

# <a name="python"></a>[Python](#tab/python)

6. Åbn **PowerShell** eller **Kommandoprompt**.

7. Bekræft, at du er i **Python** > mappen **Integrer for dine kunder**, at filen **requirements.txt** er i mappen, og kør `pip3 install -r requirements.txt`.

8. Åbn mappen **Programmet ejer data** ved hjælp af dine foretrukne IDE. Vi anbefaler, at du bruger en af følgende:

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. Åbn **config.py**.

10. Afhængigt af din godkendelsesmetode skal du udfylde følgende parameterværdier:

    |Parameter            |Tjenesteprincipal  |Masterbruger  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |ServicePrincipal         |MasterUser         |
    |`WORKSPACE_ID`        |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)          |Id'et for arbejdsområdet med din integrerede rapport – se [arbejdsområde-id](#workspace-id)         |
    |`REPORT_ID`           |Id'et for den rapport du integrerer – se [rapport-id](#report-id)            |Id'et for den rapport du integrerer – se [rapport-id](#report-id)         |
    |`TENANT_ID`           |[Lejer-id'et](#tenant-id) for dit Azure AD         |I/T         |
    |`CLIENT_ID`           |[Klient-id'et](#client-id) for dit Azure AD-program         |[Klient-id'et](#client-id) for dit Azure AD-program         |
    |`CLIENT_SECRET`       |[Klienthemmeligheden](#client-secret) for dit Azure AD         |I/T         |
    |`POWER_BI_USER`        |I/T         |Brugernavnet for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |
    |`POWER_BI_PASS`        |I/T         |Adgangskoden for din *masterbruger* – se [brugernavn og adgangskode til Power BI](#power-bi-username-and-password)         |

11. Gem filen.

12. Kør projektet ved at gøre følgende:

    a. I **PowerShell** eller **Kommandoprompt** skal du navigere til **Python** > **Integrer for dine kunder** > mappen **AppOwnesData** og udføre `flask run`.

    b. Åbn en ny fane i browseren, og naviger til [http://localhost:5300](http://localhost:5300).

---

## <a name="developing-your-application"></a>Udvikling af dit program

Når du har konfigureret og kørt eksempelprogrammet til *integrering for dine kunder*, kan du begynde at udvikle dit program.

Når du er klar, kan du gennemse kravene til [flyt til produktion](move-to-production.md). Du har også brug for en [kapacitet](embedded-capacity.md), og du bør gennemse artiklen [Kapacitetsplanlægning](embedded-capacity-planning.md) for at etablere, hvilken SKU der passer bedst til dine behov.


## <a name="next-steps"></a>Næste trin

> [!div class="nextstepaction"]
>[Flyt til produktion](move-to-production.md)

>[!div class="nextstepaction"]
>[Integrer til din organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Integrer sideinddelte rapporter for dine kunder](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Integrer sideinddelte rapporter for din organisation](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Spørg Power BI-community'et](https://community.powerbi.com/)