---
title: Overvejelser i forbindelse med generering af et integreringstoken
description: Få mere at vide om overvejelser, begrænsninger og tilladelser, der kræves for at generere et integreringstoken
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: cea97f16cf06e80b7b16ef7740fcf3103b2f1eb4
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2020
ms.locfileid: "95513774"
---
# <a name="considerations-when-generating-an-embed-token"></a>Overvejelser i forbindelse med generering af et integreringstoken

[Generér token](/rest/api/power-bi/embedtoken) er en REST API, der gør det muligt at oprette et token til integration af et Power BI-element i en webapp eller en portal. Tokenet bruges til at godkende din anmodning i forhold til Power BI-tjenesten.

API'en til oprettelse af token bruger en enkelt identitet (en masterbruger eller en tjenesteprincipal) til at oprette et token til en individuel bruger, afhængigt af brugerens legitimationsoplysninger i appen (effektiv identitet).

Når anmodningen er godkendt, gives der adgang til de relevante data.

>[!NOTE]
>Generér token er kun tilgængelig, når du [*integrerer for dine kunder*](embed-sample-for-customers.md) (også kaldet et scenarie, hvor *appen ejer data*).

Du kan bruge følgende API'er til at generere et token:

* [Dashboards](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [Datasæt](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [Generér token for flere rapporter](/rest/api/power-bi/embedtoken/generatetoken)


* [Rapportoprettelse](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [Rapporter](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [Felter](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>Versioner af arbejdsområde

Power BI har to versioner af arbejdsområdet, et *klassisk* arbejdsområde og et *nyt* arbejdsområde. Du kan få mere at vide om forskellen mellem disse arbejdsområder i [Forskelle på det nye og det klassiske arbejdsområde](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences).

Når du opretter et integreringstoken, skal du gøre dig forskellige overvejelser for de forskellige arbejdsområder, og de kræver forskellige tilladelser.

|                  |*Klassisk* arbejdsområde |*Nyt* arbejdsområde|
|------------------|---------|--------|
|**Overvejelser**|<li>Datasættet og elementet skal være i det samme arbejdsområde</li><li>Tjenesteprincipalen kan ikke bruges</li>  |Datasættet og elementet kan være i to forskellige *nye* arbejdsområder |
|**Tilladelser til arbejdsområde**|Masterbrugeren skal være administrator af arbejdsområdet  |Tjenesteprincipalen eller masterbrugeren skal som minimum være medlem af begge arbejdsområder |

>[!NOTE]
>* Du kan ikke oprette et integreringstoken til [Mit arbejdsområde](../../consumer/end-user-workspaces.md#types-of-workspaces).
>* Ordet *element* refererer til et Power BI-element, f.eks. et dashboard, et felt, spørgsmål og svar eller en rapport.

## <a name="securing-your-data"></a>Sikring af dine data

Når du opretter din løsning, skal du overveje disse to måder at sikre dine data på:

* [Arbejdsområdebaseret isolation](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [Sikkerhedsbaseret isolation på rækkeniveau](embed-multi-tenancy.md#row-level-security-based-isolation)

Hvis du vil bruge RLS-metoden, skal du gennemse [RLS-overvejelser og begrænsninger](generate-embed-token.md#row-level-security) i slutningen af denne artikel.

## <a name="token-permissions"></a>Tilladelser til token

I API'er til oprettelse af token beskrives tokentilladelserne i afsnittet *GenerateTokenRequest*.

>[!NOTE]
>De tokentilladelser, der er angivet i dette afsnit, er ikke tilgængelige for API'en [Generér token for flere rapporter](/rest/api/power-bi/embedtoken/generatetoken).

### <a name="access-level"></a>Adgangsniveau

Brug parameteren *accessLevel* til at bestemme brugerens adgangsniveau.

* **Vis** – Tildel visningstilladelser til brugeren.

* **Rediger** – Tildel visnings- og redigeringstilladelser til brugeren (gælder kun, når der genereres et integreringstoken til en rapport).

    Hvis du bruger API'en [Generér token for flere rapporter](/rest/api/power-bi/embedtoken/generatetoken), skal du bruge parameteren *allowEdit* til at give brugeren visnings- og redigeringstilladelser.

* **Opret** – Giv brugeren tilladelse til at oprette en rapport (gælder kun, når der oprettes et integreringstoken til oprettelse af en rapport).

    Hvis du vil oprette en rapport, skal du også angive parameteren *datasetId*.

### <a name="saving-a-copy-of-the-report"></a>Gem en kopi af rapporten

Brug det booleske udtryk *allowSaveAs* for at give brugere mulighed for at gemme rapporten som en ny rapport. Denne indstilling er som standard angivet til *false*.

Denne parameter er kun tilgængelig, når du opretter et integreringstoken for en rapport.

### <a name="row-level-security"></a>Sikkerhed på rækkeniveau

Med [Sikkerhed på rækkeniveau (RLS)](embedded-row-level-security.md) kan du vælge at bruge en anden identitet end identiteten for den tjenesteprincipal eller masterbruger, du opretter tokenet med. Ved hjælp af denne indstilling kan du få vist integrerede oplysninger, afhængigt af den bruger du er målrettet mod. I dit program kan du f.eks. bede brugere om at logge på og derefter få vist en rapport, der kun indeholder salgsoplysninger, hvis den bruger, der er logget på, er en salgsmedarbejder.

Hvis du bruger RLS, kan du i nogle tilfælde udelade brugerens identitet (parameteren *EffectiveIdentity*). Derved får tokenet adgang til hele databasen. Denne metode kan bruges til at give adgang til brugere, f.eks. administratorer og ledere, der har tilladelse til at få vist hele datasættet. Du kan dog ikke bruge denne metode i alle scenarier. I tabellen nedenfor kan du se en liste over de forskellige RLS-typer, og den viser, hvilken godkendelsesmetode der kan bruges uden angivelse af en brugers identitet.

Tabellen viser også de overvejelser og den begrænsning, der gælder for de enkelte RLS-typer.

|RLS-type  |Kan jeg generere et integreringstoken uden at angive den effektive brugers id?  |Overvejelser og begrænsninger  |
|---------|---------|---------|
|Sikkerhed på rækkeniveau for Cloud (Cloud RLS)      |✔ Masterbruger<br/>✖ Tjenesteprincipal          |         |
|RDL (sideinddelte rapporter)     |✖ Masterbruger<br/>✔ Tjenesteprincipal        |Du kan ikke bruge en masterbruger til at oprette et integreringstoken til RDL.         |
|Direkte AS-forbindelse (Analysis Services) i det lokale miljø    |✔ Masterbruger<br/>✖ Tjenesteprincipal         |Den bruger, der opretter integreringstokenet, skal også have en af følgende tilladelser:<li>Tilladelser til gatewayadministration</li><li>Datakilde repræsenter tilladelse (*ReadOverrideEffectiveIdentity*)</li>         |
|Direkte AS-forbindelse (Analysis Services)    |✔ Masterbruger<br/>✖ Tjenesteprincipal         |Identiteten for den bruger, der opretter integreringstokenet, kan ikke tilsidesættes. Brugerdefinerede data kan bruges til at implementere dynamisk RLS eller sikker filtrering.<br/><br/>**Bemærk!** Tjenesteprincipalen skal angive sit objekt-id som den effektive identitet (RLS-brugernavn).         |
|SSO (enkeltlogon)     |✔ Masterbruger<br/>✖ Tjenesteprincipal         |Der kan leveres en eksplicit (SSO) identitet ved hjælp af identitetsblobegenskaben i et effektivt identitetsobjekt         |
|SSO og Cloud RLS     |✔ Masterbruger<br/>✖ Tjenesteprincipal         |Du skal angive følgende:<li>Eksplicit (SSO) identitet i identitetsblobegenskaben i et effektivt identitetsobjekt</li><li>Effektiv (RLS) identitet (brugernavn)</li>         |

>[!NOTE]
>Tjenesteprincipalen skal altid angive følgende:
>* En identitet for et element med et RLS-datasæt.
>* En effektiv RLS-identitet med egenskaben username defineret for et SSO-datasæt.

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Registrer et program](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded til dine kunder](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objekter for et program og en tjenesteprincipal i Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Sikkerhed på rækkeniveau ved hjælp af datagateway i det lokale miljø med tjenesteprincipal](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Integrer Power BI-indhold med tjenesteprincipal](embed-service-principal.md)