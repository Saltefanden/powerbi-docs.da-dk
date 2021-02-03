---
title: Integrer indhold i dit program til integreret analyse i Power BI for at give din organisation bedre integreret BI-indsigt
description: Få mere at vide om, hvordan du integrerer Power BI i dit program ved hjælp af software til integreret analyse, integrerede analyseværktøjer eller integrerede værktøjer til business intelligence. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 12/17/2020
ms.openlocfilehash: fbae63597ecf4ff36783ad83785f87c242359f90
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494945"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-organization-application"></a>Selvstudium: Integrer Power BI indhold ved hjælp af et eksempel *på et integreret program til din organisation*

Power BI Embedded Analytics gør det muligt for dig at integrere Power BI indhold, f. eks. rapporter, dashboards og felter, i dit program.

I dette selvstudium lærer du, hvordan du:

>[!div class="checklist"]
>* Konfigurer dit integrerede miljø.
>* Konfigurer en *integrering til din organisation* (også kaldet *bruger ejer data*) eksempelprogrammet.

Hvis du vil bruge dit program, skal brugerne logge på Power BI.

Løsningen Integrer indhold for din organisation bruges normalt af virksomheder og store organisationer og er beregnet til interne brugere.

## <a name="code-sample-specifications"></a>Specifikationer for kodeeksempel

Dette selvstudium indeholder instruktioner til, hvordan du konfigurerer en integrering til eksempelprogrammet til *din organisation* i en af følgende strukturer:

* .NET Framework
* .NET Core
* Reagere maskine

>[!NOTE]
>Med *.net Core* og *Microsoft .NET Framework* -eksempler kan slutbrugeren få vist ethvert Power bi Dashboard, en rapport eller et felt, som de har adgang til i Power bi-tjeneste. I eksemplet med *reagere maskine* kan du kun indlejre én rapport, som din slutbruger allerede har adgang til på Power bi-tjeneste.

Kodeeksemplerne understøtter følgende browsere:

* Microsoft Edge
* Google Chrome
* Mozilla Firefox

## <a name="prerequisites"></a>Forudsætninger

Før du starter dette selvstudium, skal du bekræfte, at du har både de Power BI- og kodeafhængigheder, der er angivet nedenfor:

* **Power BI-afhængigheder**

    * Din egen [Azure Active Directory-lejer](create-an-azure-active-directory-tenant.md).

    * En af følgende licenser:

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)

        * [Premium pr. bruger (PPU)](../../admin/service-premium-per-user-faq.md)

    >[!NOTE]
    >Hvis du vil [skifte til produktion](move-to-production.md) , skal du bruge en af følgende konfigurationer:
    >* Alle brugere med Pro-licenser.
    >* Alle brugere med PPU-licenser.
    >* En [kapacitet](embedded-capacity.md). Denne konfiguration gør det muligt for alle brugere at have gratis licenser.

* **Kodeafhængigheder**

    # <a name="net-core"></a>[.NET Core](#tab/net-core)

    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (eller nyere)
    
    * Et integreret udviklingsmiljø (IDE). Vi anbefaler, at du bruger en af følgende:

        * [Visual Studio](https://visualstudio.microsoft.com/)

        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)

    # <a name="react-typescript"></a>[Reagere maskine](#tab/react)

    * En teksteditor

    * Kommandolinje Terminal (eller PowerShell)

---

## <a name="method"></a>Metode

Følg disse trin for at oprette et integreret eksempelprogram *til din organisations* eksempel:

1. [Registrer et Azure AD-program](#step-1---register-an-azure-ad-application).

2. [Opret et Power BI-arbejdsområde](#step-2---create-a-power-bi-workspace).

3. [Opret og publicer en Power BI-rapport](#step-3---create-and-publish-a-power-bi-report).

4. [Hent de integrerede parameterværdier](#step-4---get-the-embedding-parameter-values).

5. [Integrer dit indhold](#step-5---embed-your-content).

## <a name="step-1---register-an-azure-ad-application"></a>Trin 1 – Registrer et Azure AD-program

Når du registrerer dit program med Azure AD, kan du oprette en identitet til din app.

[!INCLUDE[Register Azure AD app](../../includes/embed-tutorial-register-app.md)]

## <a name="step-2---create-a-power-bi-workspace"></a>Trin 2 – Opret et Power BI arbejdsområde

[!INCLUDE[Create a Power BI workspace](../../includes/embed-tutorial-create-workspace.md)]

## <a name="step-3---create-and-publish-a-power-bi-report"></a>Trin 3 – Opret og Publicer en Power BI rapport

[!INCLUDE[Create a Power BI report](../../includes/embed-tutorial-create-report.md)]

## <a name="step-4---get-the-embedding-parameter-values"></a>Trin 4-Hent de integrerede parameterværdier

Hvis du vil integrere dit indhold, skal du have nogle få parameterværdier. De parameterværdier, du skal bruge, afhænger af det sprog i eksempelprogrammet, du vil bruge. I nedenstående tabel vises de parameterværdier, der skal bruges til hvert eksempel.

|Parameter  |.NET Core  |.NET Framework  |Reagere maskine |
|---------|---------|---------|---------|
|[Klient-id](#client-id) |![Gælder for.](../../media/yes.png) |![Gælder for.](../../media/yes.png)         |![Gælder for.](../../media/yes.png) |
|[Klienthemmelighed](#workspace-id) |![Gælder for.](../../media/yes.png) |![Gælder for.](../../media/yes.png) |![Gælder ikke for.](../../media/no.png) |
|[Arbejdsområde-id]() |![Gælder ikke for.](../../media/no.png) |![Gælder ikke for.](../../media/no.png) |![Gælder for.](../../media/yes.png) |
|[Rapport-id]() |![Gælder ikke for.](../../media/no.png) |![Gælder ikke for.](../../media/no.png) |![Gælder for.](../../media/yes.png) |

### <a name="client-id"></a>Klient-id

>[!TIP]
>**Gælder for:** ![ Gælder for. ](../../media/yes.png) . NET-kerne ![ gælder for. ](../../media/yes.png) . NET Framework ![ gælder for. ](../../media/yes.png) Reagere maskine

[!INCLUDE[Get the client ID](../../includes/embed-tutorial-client-id.md)]

### <a name="client-secret"></a>Klienthemmelighed

>[!TIP]
>**Gælder for:** ![ Gælder for. ](../../media/yes.png) . NET-kerne ![ gælder for. ](../../media/yes.png) . NET Framework ![ gælder ikke for. ](../../media/no.png) Reagere maskine

[!INCLUDE[Get the client secret](../../includes/embed-tutorial-client-secret.md)]

### <a name="workspace-id"></a>Id for arbejdsområde

>[!TIP]
>**Gælder for:** ![ Gælder ikke for. ](../../media/no.png) . NET Core ![ gælder ikke for. ](../../media/no.png) .. NET Framework ![ gælder for. ](../../media/yes.png) Reagere maskine

[!INCLUDE[Get the workspace ID](../../includes/embed-tutorial-workspace-id.md)]

### <a name="report-id"></a>Rapport-id

>[!TIP]
>**Gælder for:** ![ Gælder ikke for. ](../../media/no.png) . NET Core ![ gælder ikke for. ](../../media/no.png) .. NET Framework ![ gælder for. ](../../media/yes.png) ReactTypeScript

[!INCLUDE[Get the report ID](../../includes/embed-tutorial-report-id.md)]

## <a name="step-5---embed-your-content"></a>Trin 5 – Integrer dit indhold

Det Power BI integrerede eksempelprogram giver dig mulighed for at oprette en *integrering til din organisation* Power bi app.

Følg disse trin for at ændre eksempelprogrammet *Integrer for dit organisations* eksempel, så du kan integrere din Power BI rapport.

[!INCLUDE[Embedding steps](../../includes/embed-tutorial-embedding-steps.md)]

4. Afhængigt af det sprog du vil have, at dit program skal bruge, skal du åbne en af disse mapper:

    * .NET Core
    * .NET Framework
    * Reager-TS

    >[!NOTE]
    >*Integreringen til* eksempelprogrammerne i din organisation understøtter kun de ovenfor viste strukturer. Eksempelprogrammerne *Java*, *node js* og *Python* kan kun understøtte *[integreringen til din kunde](embed-sample-for-customers.md)* løsning.

# <a name="net-core"></a>[.NET Core](#tab/net-core)

### <a name="configure-your-azure-ad-app"></a>Konfigurer din Azure AD-app

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. Åbn *din* webplatform i *platform konfigurationer*, og Tilføj i afsnittet **Omdiriger URI'er** `https://localhost:5000/signin-oidc` .

    > [!NOTE]
    >Hvis du ikke har en **Web-** platform, skal du vælge **Tilføj en platform** og vælge **Web** i vinduet *Konfigurer platforme* .

6. Gem dine ændringer.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-net-configurations.png" alt-text="Skærmbillede, der viser konfigurationen af Azure AD app-godkendelse, herunder webomdirigering U R I for eksempel på en .NET-kerne app.":::

### <a name="configure-the-sample-embedding-app"></a>Konfigurer den eksempel integrerede app

1. Åbn mappen **Integrer for din organisation** .

2. Åbn *appen Integrer for din organisations eksempel* ved hjælp af en af følgende metoder:

    * Hvis du bruger [Visual Studio](https://visualstudio.microsoft.com/), skal du åbne filen **UserOwnsData. SLN** .

    * Hvis du bruger [Visual Studio kode](https://code.visualstudio.com/), skal du åbne mappen **UserOwnsData** .

3. Åbn **appsettings.js,** og Udfyld følgende parameterværdier:

    * `ClientId` -Brug [klient-ID-](#client-id) GUID'et

    * `ClientSecret` -Brug [klientens hemmelighed](#client-secret)

### <a name="run-the-sample-app"></a>Kør eksempel appen

1. Kør projektet ved at vælge den relevante indstilling:

    * Hvis du bruger **Visual Studio**, skal du vælge **IIS Express** (afspil).

    * Hvis du bruger **Visual Studio Code**, skal du vælge **Kør > Start fejlfinding**.

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

### <a name="configure-your-azure-ad-app"></a>Konfigurer din Azure AD-app

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. I *platforms konfigurationer* skal du konfigurere følgende:

    1. På din *Web-* platform skal du i afsnittet om **omdirigering af URI'er** tilføje `https://localhost:44300/` .

        > [!NOTE]
        >Hvis du ikke har en **Web-** platform, skal du vælge **Tilføj en platform** og vælge **Web** i vinduet *Konfigurer platforme* .
    
    2. I *implicit bonus og hybrid flows* skal du aktivere indstillingen **id-tokens** .
    
6. Gem dine ændringer.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-framework-configurations.png" alt-text="Skærmbillede, der viser konfigurationen af Azure AD app-godkendelse, herunder webomdiriger U R I og den valgte adgangstoken til .NET Framework-app-eksempel.":::

### <a name="configure-the-sample-embedding-app"></a>Konfigurer den eksempel integrerede app

1. Åbn mappen **Integrer for din organisation** .

2. Brug [Visual Studio](https://visualstudio.microsoft.com/)ved at åbne filen **UserOwnsData. SLN** .

3. Åbn **Web.config** , og Udfyld følgende parameterværdier:

    * `clientId` -Brug [klient-ID-](#client-id) GUID'et

    * `clientSecret` -Brug [klientens hemmelighed](#client-secret)

### <a name="run-the-sample-app"></a>Kør eksempel appen

1. Kør projektet ved at vælge **IIS Express** (afspil).

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="react-typescript"></a>[Reagere maskine](#tab/react)

### <a name="configure-your-azure-ad-app"></a>Konfigurer din Azure AD-app

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. Konfigurer din webplatform i *platforms konfigurationer* **på følgende** måde:

    1. I **Omdiriger URI'er** skal du tilføje `https://localhost:3000` og vælge **Konfigurer**.

        > [!NOTE]
        >Hvis du ikke har en **Web-** platform, skal du vælge **Tilføj en platform** og vælge **Web** i vinduet *Konfigurer platforme* .

    2. I *implicit bonus og hybrid flows* skal du aktivere begge indstillinger:
        * **Adgangstokens**
        * **ID-tokens**
    
6. Gem dine ændringer.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-react-configurations.png" alt-text="Skærmbillede, der viser konfigurationen af Azure AD app-godkendelse, herunder webomdirigering U R, som er angivet for localhost 3000.":::

### <a name="configure-the-sample-embedding-app"></a>Konfigurer den eksempel integrerede app

1. Åbn mappen **Integrer for din organisation**  >  **UserOwnsData**  >  **src** .

2. Brug en teksteditor til at åbne filen **config. ts** og angive følgende parameterværdier:

    * `clientId` -Brug [klient-ID-](#client-id) GUID'et

    * `workspaceId` -Brug [arbejdsområde-id'et](#client-secret)

    * `reportId` -Brug [rapport-id'et](#report-id)

3. Gem filen.

### <a name="run-the-sample-app"></a>Kør eksempel appen

1. Åbn en terminal i, og Naviger til **Integrer for din organisation**  >  **UserOwnsData**.

2. Installér de påkrævede afhængigheder ved at udføre følgende kommando:

   `npm install`

3. Kør programmet ved at udføre følgende kommando:

   `npm run start`

    >[!NOTE]
    >Når du logger på første gang, bliver du bedt om at tillade Azure AD-tilladelser til appen.

---

## <a name="developing-your-application"></a>Udvikling af dit program

Når du har konfigureret og kørt eksempelprogrammet til *integrering for dine kunder*, kan du begynde at udvikle dit program.

[!INCLUDE[Move to production](../../includes/embed-tutorial-production.md)]

## <a name="next-steps"></a>Næste trin

> [!div class="nextstepaction"]
>[Flyt til produktion](move-to-production.md)

>[!div class="nextstepaction"]
>[Integrer indhold for dine kunder](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Integrer sideinddelte rapporter for dine kunder](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Integrer sideinddelte rapporter for din organisation](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Spørg Power BI-community'et](https://community.powerbi.com/)