---
title: Opret forbindelse til Microsoft Sustainability Calculator
description: Microsoft Sustainability Calculator til Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 01/06/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: 00c8ee0ff77d2253b1240c943261ab053f29765a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410522"
---
# <a name="connect-the-microsoft-sustainability-calculator"></a>Opret forbindelse til Microsoft Sustainability Calculator
Få indsigt i kulstofemissionerne i din it-infrastruktur, så du kan træffe flere bæredygtige beregningsbeslutninger

Microsoft Sustainability Calculator giver ny indsigt i de data om kulstofemissioner, der er knyttet til Azure-tjenester. De personer, der er ansvarlige for at rapportere om og administrere bæredygtighed i deres organisationer, har nu mulighed for at anslå kulstofpåvirkningen af hvert Azure-abonnement samt se de anslåede kulstofbesparelser i forbindelse med at køre disse arbejdsbelastninger i Azure i forhold til datacentre i det lokale miljø. Disse data kan bruges til rapportering af drivhusgasser i forbindelse med scope 3-emissioner. Adgangen til Microsoft Sustainability Calculator kræver dit lejer-id og din adgangsnøgle, der typisk er tilgængelige via din organisations Azure-administrator.

Hvis du vil bruge denne app, skal du bruge oplysningerne fra Azure Enterprise Portal. Virksomhedens systemadministratorer kan hjælpe dig med at hente disse oplysninger. Gennemse disse instruktioner, og få de nødvendige oplysninger, inden du installerer appen. 

Denne version af connectoren understøtter kun virksomhedstilmeldinger fra [https://ea.azure.com](https://ea.azure.com/). Tilmeldinger i Kina understøttes ikke i øjeblikket.

## <a name="how-to-connect"></a>Sådan opretter du forbindelse
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

1. Vælg **Microsoft Sustainability Calculator** \> **Hent nu**.
1. Vælg **Installér** under **Installér denne Power BI-app?** .
1. Vælg feltet **Microsoft Sustainability Calculator** i ruden **Apps**.
1. Under **Kom i gang med din nye app** skal du vælge **Opret forbindelse**.

    ![Kom i gang med din nye app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

1. Indtast **firmanavn, brugerregistreringsnummer** og **antal måneder \>. Log på.** Herunder kan du se detaljer om, hvordan du [finder de pågældende parametre](#finding-parameters).

    ![Virksomhedstilmelding](media/service-connect-to-microsoft-sustainability-calculator/company-enrollment.png)

1. Vælg **Nøgle** som **godkendelsesmetode**, og vælg **Organisation** for **Niveau for beskyttelse af personlige oplysninger**.
1. Indtast din **adgangsnøgle** for **Nøgle\>. Log på**.

    ![Adgang med adgangsnøgle](media/service-connect-to-microsoft-sustainability-calculator/access-key-entry.png)

1. Importprocessen starter automatisk. Når processen er fuldført, vises et nyt dashboard samt en ny rapport og model i **navigationsruden**. Vælg rapporten for at få vist de importerede data.

## <a name="finding-parameters"></a>Søgning efter parametre

Hvis du vil finde din virksomheds **registrerings-ID** og **adgangsnøgle**, skal du kontakte din Azure-administrator for at få de nødvendige oplysninger. Din administrator:

1. Logger på [Azure Enterprise Portal](https://ea.azure.com) og klikker på **Administrer** på båndet til venstre for at få adgang til **tilmeldingsnummeret** som vist nedenfor
2. Klikker på [Rapporter](https://ea.azure.com) i **Azure Enterprise Portal** og derefter API-adgangsnøgle, som vist nedenfor, for at få den primære nøgle til registreringskontoen

## <a name="using-the-app"></a>Brug af appen

Hvis du vil opdatere parametrene på et tidspunkt, skal du gå til indstillingerne for **datasæt** og få adgang til det, der er knyttet til apparbejdsområdet, og opdatere lejer-id, firmanavn eller datamåneder. Når du har anvendt parametrene, skal du klikke på **Opdater** for at genindlæse dataene med de nye parametre.