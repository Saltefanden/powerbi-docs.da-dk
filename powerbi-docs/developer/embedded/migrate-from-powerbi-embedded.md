---
title: Sådan overfører du indhold i en arbejdsområdesamling i Power BI til en løsning til en integreret Power BI-analyse i Power BI Embedded for at få bedre integreret BI-indsigt
description: Se, hvordan du overfører fra Power BI Workspace Collection til Power BI Embedded og udnytter fordelene ved at integrere i apps. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/30/2018
ms.openlocfilehash: a2e73ced427daa8aebf6b5c9836aa060d3591e3e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886367"
---
# <a name="how-to-migrate-power-bi-workspace-collection-content-to-power-bi-embedded"></a>Sådan overfører du indhold fra Power BI Workspace Collection til Power BI Embedded

Se, hvordan du overfører fra Power BI Workspace Collection til Power BI Embedded og udnytter fordelene ved at integrere i apps.

Microsoft [annoncerede for nylig Power BI Embedded](https://powerbi.microsoft.com/blog/power-bi-embedded-capacity-based-skus-coming-to-azure/), som er en ny kapacitetsbaseret licensmodel, der giver øget fleksibilitet i forhold til den måde, brugerne får adgang til, deler og distribuerer indhold på. Den nye model giver også øget skalerbarhed og ydeevne.

Med Power BI Embedded få du én API-grænseflade, en ensartet række funktioner og adgang til de nyeste funktioner i Power BI, f.eks. dashboards, gateways og arbejdsområder, når du integrerer indhold. Fremadrettet kan du starte med Power BI Desktop og overgå til udrulning med Power BI Embedded.

Den nuværende Power BI Workspace Collection er fortsat tilgængelig i en begrænset periode. Kunder, der har en Enterprise Agreement, får adgang i forbindelse med udløbet af deres eksisterende aftaler. Kunder, der har fået Power BI Workspace Collection via direkte kanaler eller or CSP-kanaler, har fortsat adgang i ét år fra det tidspunkt, hvor Power BI Embedded bliver frigivet som generel tilgængelig.  I denne artikel får du hjælp til at blive overført fra Power BI Workspace Collection til det nye Power BI Embedded, og du kan læse om, hvilke ændringer du kan forvente i applikationen.

> [!IMPORTANT]
> Selvom overførslen vil være afhængig af Power BI Embedded, er brugerne af din applikation ikke afhængige af Power BI, når de bruger et **integreringstoken**. De behøver ikke at tilmelde sig Power BI for at få vist det integrerede indhold i din applikation. Du kan bruge denne integreringstilgang i forbindelse med Embedded for brugere uden Power BI.

![Integreringsflow](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

Inden du begynder overførslen til det nye Power BI Embedded, kan du tage en hurtig gennemgang, der hjælper dig med at konfigurere dit nye Power BI Embedded-miljø ved hjælp af [værktøjet til konfiguration af integrering](https://aka.ms/embedsetup).

Vælg den løsning, der er den rette for dig:
* **Embed for your customers** – når du er interesseret i en løsning, hvor *appen ejer dataene*. [Embedding for your customers](embedding.md#embedding-for-your-customers) giver mulighed for at integrere dashboards og rapporter for de brugere, der ikke har en Power BI-konto. 

* **Embed for your organization** – når du er interesseret i en løsning, hvor *brugeren ejer dataene*. Med [Embedding for your organization](embedding.md#embedding-for-your-organization) kan du udvide Power BI-tjenesten.

## <a name="prepare-for-the-migration"></a>Forbered overførslen

Der er et par ting, du skal gøre som forberedelse til at overføre fra Power BI Workspace Collection til Power BI Embedded. Du skal have adgang til en lejer og til en bruger med en Power BI Pro-licens.

1. Du skal også have adgang til en Azure Active Directory-lejer (Azure AD).

    Du skal beslutte, hvilken lejerkonfiguration du vil bruge.

   * Vil du bruge virksomhedens eksisterende Power BI-lejer?
   * Skal du bruge en separat lejer til din app?
   * Skal du bruge en separat lejer for hver kunde?

     Hvis du beslutter at oprette en ny lejer til din app eller for hver kunde, skal du se [Opret en Azure Active Directory-lejer](create-an-azure-active-directory-tenant.md) eller [Sådan får du en Azure Active Directory-lejer](/azure/active-directory/develop/active-directory-howto-tenant).
2. Opret en bruger under den nye lejer. Brugeren skal fungere som masterkonto i din app. Masterkontoen skal tilmeldes Power BI, og den skal også være tildelt en Power BI Pro-licens.

## <a name="accounts-within-azure-ad"></a>Konti i Azure AD

Der skal findes følgende konti i din lejer.

> [!NOTE]
> Disse konti skal have Power BI Pro-licenser for at kunne bruge arbejdsområder.

1. En Power BI-administrator.

    Det anbefales, at brugeren er medlem af alle de arbejdsområder, der oprettes med henblik på integrering.

2. Konti for analytikere, der opretter indhold.

    Disse brugere skal tildeles til arbejdsområder efter behov.

3. En *master* brugerkonto eller en Embedded-konto.

    Appens backend gemmer legitimationsoplysninger for denne konto og bruger den til at få et Azure AD-token til brug med Power BI REST API'erne. Denne konto bruges til at generere integreringstokenet til appen. Kontoen skal også være administrator for de arbejdsområder, der blev oprettet med henblik på integrering.

> [!NOTE]
> Dette er blot en almindelig brugerkonto i organisationen, der bruges til integrering.

## <a name="app-registration-and-permissions"></a>Appregistrering og tilladelser

Du skal registrere en app i Azure AD og tildele den visse tilladelser.

### <a name="register-an-application"></a>Registrer en app

Du skal registrere din app i Azure AD, før du kan foretage REST-API-kald. Dette omfatter at få til Azure-portalen for at anvende yderligere konfiguration ud over Power BI-appregistreringssiden. Du kan finde flere oplysninger i [Registrer en Azure AD-app for at integrere Power BI-indhold](register-app.md).

Du bør registrere appen med appens **master** konto.

## <a name="create-workspaces-required"></a>Opret arbejdsområder (påkrævet)

Du kan drage fordel af arbejdsområder for at sikre en bedre isolation, hvis din app bruges af flere kunder. Dashboards og rapporter bør være isoleret mellem dine kunder. Du kan derefter bruge en Power BI-konto pr. arbejdsområde for at isolere appoplevelserne yderligere mellem kunderne.

> [!IMPORTANT]
> Du kan ikke bruge et personligt arbejdsområde til integrering til de brugere, der ikke har Power BI.

Brugeren skal have en Pro-licens, før der kan oprettes et arbejdsområde i Power BI. Den Power BI-bruger, der opretter arbejdsområdet, bliver som standard administrator af det pågældende arbejdsområde.

> [!NOTE]
> Appens *master* konto skal være administrator for arbejdsområdet.

## <a name="content-migration"></a>Overførsel af indhold

Du kan overføre indhold fra dine arbejdsområdesamlinger til Power BI Embedded samtidig med din aktuelle løsning, og det medfører ikke nogen nedetid.

Der findes et **overførselsværktøj**, som du kan bruge til at kopiere indhold fra Power BI Workspace Collection til Power BI Embedded. Praktisk, hvis du har en meget indhold. Du kan finde flere oplysninger under [Overførselsværktøjet i Power BI Embedded](migrate-tool.md).

Overførsel af indhold er baseret primært på to-API'er.

1. Download PBIX – dette API kan downloade de PBIX-filer, som blev uploadet til Power BI efter oktober 2016.
2. Import PBIX – dette API uploader PBIX til Power BI.

For nogle relaterede kodestykker skal du se [Kodestykker til overførsel af indhold fra Power BI Workspace Collection](migrate-code-snippets.md).

### <a name="report-types"></a>Rapporttyper

Der findes flere typer rapporter, som kræver hver deres overførselsproces.

#### <a name="cached-dataset--report"></a>Cachelagret datasæt og rapport

Cachelagrede datasæt, der refererer til PBIX-filer, og som havde importerede data i modsætning til en dynamisk forbindelse eller en DirectQuery-forbindelse.

**Flow**

1. Udfør et kald til API'et Download PBIX fra PaaS-arbejdsområdet.
2. Gem PBIX.
3. Udfør et kald til Import PBIX til SaaS-arbejdsområdet.

#### <a name="directquery-dataset--report"></a>DirectQuery-datasæt og -rapport

**Flow**

1. Udfør et kald til GET `https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources` og gem forbindelsesstreng er modtaget.
2. Udfør et kald til API'et Download PBIX fra PaaS-arbejdsområdet.
3. Gem PBIX.
4. Udfør et kald til Import PBIX til SaaS-arbejdsområdet.
5. Opdater forbindelsesstreng ved at udføre et kald – POST  `https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.SetAllConnections`
6. Hent identifikatorer for GW og datakilde ved at udføre et kald – GET `https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources`
7. Opdater brugerens legitimationsoplysninger ved at udføre et kald – PATCH `https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id}`

#### <a name="old-dataset--reports"></a>Gamle datasæt og rapporter

Dette er de datasæt/rapporter, der er oprettet før oktober 2016. Download PBIX understøtter ikke de PBIX'er, som blev uploadet før oktober 2016

**Flow**

1. Hent PBIX fra dit udviklingsmiljø (din interne versionsstyring).
2. Udfør et kald til Import PBIX til SaaS-arbejdsområdet.

#### <a name="push-dataset--report"></a>Push datasæt og rapport

Download PBIX understøtter ikke *Push API*-datasæt. Data fra Push API-datasæt kan ikke overføres fra PaaS til SaaS.

**Flow**

1. Udfør et kald til API'et "Create dataset" med datasæt-Json for at oprette datasæt i SaaS-arbejdsområdet.
2. Byg rapporten igen for det oprettede datasæt*.

Du kan prøve følgende for at overføre Push API-rapporten fra PaaS til SaaS.

1. Overførsel af test-PBIX til PaaS-arbejdsområde.
2. Klon Push API-rapporten, og bind den til test-PBIX'en fra trin 1.
3. Download Push API-rapporten med test-PBIX'en.
4. Overfør test-PBIX'en til dit SaaS-arbejdsområde.
5. Opret et push-datasæt i dit SaaS-arbejdsområde.
6. Bind rapporten til Push API-datasættet.

## <a name="create-and-upload-new-reports"></a>Opret og upload nye rapporter

Foruden det indhold, du migrerede fra Power BI-arbejdsområdesamlingen, kan du oprette dine rapporter og datasæt ved hjælp af Power BI Desktop og derefter udgive rapporterne til et arbejdsområde. Den slutbruger, der udgiver rapporterne, skal have en Power BI Pro-licens for at kunne udgive til et arbejdsområde.

## <a name="rebuild-your-application"></a>Byg din app igen

1. Du skal ændre din app til at bruge Power BI REST API'er og rapportplaceringen på powerbi.com.
2. Byg din AuthN/AuthZ-godkendelse igen ved hjælp af *master* kontoen til din app. Du kan med fordel bruge et [integreringstoken](/rest/api/power-bi/embedtoken) for at give brugeren tilladelse til at agere på vegne af andre brugere.
3. Integrer dine rapporter fra powerbi.com i din app.

## <a name="map-your-users-to-a-power-bi-user"></a>Knyt dine brugere til en Power BI-bruger

I din app kan du knytte de brugere, du administrerer i appen, til en *master* bruger med Power BI-legitimationsoplysninger til brug i appen. Legitimationsoplysningerne til denne Power BI-*master* konto gemmes i din app og bruges til at oprette integreringstokens.

## <a name="what-to-do-when-you-are-ready-for-production"></a>Når du er klar til produktionsmiljøet

Når du er klar til at skifte til produktionsmiljøet, skal du bruge følgende.

* Hvis du bruger en separat lejer til udvikling, skal du sikre, at dine arbejdsområder samt dashboards og rapporter er tilgængelige i dit produktionsmiljø. Du skal også sikre, at du har oprettet appen i Azure AD for din produktionslejer, og at du har tildelt de nødvendige apptilladelser som angivet på trin 1.
* Køb den kapacitet, der passer med dit behov. I dette [whitepaper om planlægning af analysekapacitet i Power BI Embedded](./embedded-capacity-planning.md) kan du få oplysninger, så du kan få en bedre forståelse af, hvor meget kapacitet og hvilken type du har brug for. Du kan [købe kapacitet](https://portal.azure.com/#create/Microsoft.PowerBIDedicated) i Azure.
* Rediger arbejdsområdet, og tildel det til en Premium-kapacitet under avanceret.

    ![Premium-kapacitet](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity02.png)

* Udrul din opdaterede applikation i produktionen, og begynd at integrere rapporter fra Power BI Embedded.

## <a name="after-migration"></a>Efter overførslen

Du bør rydde op i Azure.

* Fjern alle arbejdsområder fra den udrullede løsning i Azure Embedded i Power BI Workspace Collection.
* Slet alle de arbejdsområdesamlinger, der findes i Azure.

## <a name="next-steps"></a>De næste trin

[Integrer med Power BI](embedding.md)  
[Overførselsværktøj til Power BI Workspace Collection](migrate-tool.md)  
[Kodestykker til overførsel af indhold fra Power BI Workspace Collection](migrate-code-snippets.md)  
[Sådan integrerer du Power BI-dashboards, -rapporter og -felter](embed-sample-for-your-organization.md)  
[Power BI Premium – hvad er det?](../../admin/service-premium-what-is.md)  
[Git-lager for JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript)  
[Git-lager til Power BI C#](https://github.com/Microsoft/PowerBI-CSharp)  
[Integreringseksempel til JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Whitepaper om planlægning af analysekapacitet i Workspace Collection](./embedded-capacity-planning.md)  
[Hvidbog til Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)