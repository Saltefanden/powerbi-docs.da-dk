---
title: Forstå de tilladelses tokens, der kræves for at integrere et Power BI program
description: Få mere at vide om, hvilke tokens dit Power BI program skal godkende i forhold til Azure og Power BI-tjeneste.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: amshuste
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/17/2021
ms.openlocfilehash: 6a7847b0e89086094220a51a4893ffffd59d5642
ms.sourcegitcommit: fb408dfd39943dbec990a16bcf204671beb4f0aa
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2021
ms.locfileid: "100656563"
---
# <a name="embedded-analytics-application-tokens"></a>Tokens til integrerede analyseprogrammer

Hvis du vil bruge Power BI-indhold, skal du bruge et adgangstoken. Afhængigt af din løsning kan dette token enten være et [Azure ad-token](#azure-ad-token) eller et [indlejrings-token](#embed-token).

Hvis du bruger den *integrerede kunde* løsning, får dine webapps adgang til Power bi indhold (f. eks. rapporter, dashboards og felter) Ifølge det *integrerede token* , der blev genereret af dit program.

>[!NOTE]
>Når du bruger *integreringen til din kunde* løsning, kan du bruge enhver godkendelsesmetode til at give adgang til din Web App.

Hvis du bruger *integreringen til din organisations* løsning, vil dine webapps-brugere blive godkendt i forhold til Azure ad ved hjælp af deres egne legitimationsoplysninger. Dine apps har adgang til Power BI-indholdet, som de kan få adgang til på Power BI-tjeneste.

## <a name="azure-ad-token"></a>Azure AD-token

Du skal have et [Azure ad-token](#azure-ad-token)for både *at integrere dine kunder* og *integrere til dine organisations* løsninger. Dette token kræves til alle [rest API](/rest/api/power-bi/) -handlinger, og det udløber efter en time.

* I *integreringen til dine kunder* bruges Azure ad-tokenet til at generere det *integrerede token*.

* I *din organisations integration* bruges Azure ad-tokenet til at få adgang til Power bi.

## <a name="embed-token"></a>Integrer token

Når du bruger *integreringen til din kunde* løsning, skal din Web App vide, hvilket Power bi, som brugeren har adgang til. Brug det [integrerede token](/rest/api/power-bi/embedtoken) rest API'er til at oprette et *indlejre token*, som angiver følgende:

* Det indhold, som din web app-bruger har adgang til.

* Adgangsniveauet for WebApp-brugeren (få vist, Opret eller Rediger).

Du kan finde flere oplysninger under [overvejelser ved oprettelse af et indlejrings token](generate-embed-token.md).

## <a name="authentication-flows"></a>Godkendelses flow

I dette afsnit beskrives de godkendelsesprocesser, der er for at *integrere til dine kunder* , og *integreres i din organisations* integrations løsninger.

### <a name="embed-for-your-customers"></a>Integrer indhold for dine kunder

*Integrationen for din kunde* løsning bruger et ikke-interaktivt godkendelsesforløb. Brugerne behøver ikke at logge på Azure AD for at få adgang til Power BI. I stedet bruger din web app et dedikeret Azure AD-id til godkendelse i forhold til Azure AD og genererer det *integrerede token*. Den dedikerede identitet kan være en af følgende:

* **[Tjenesteprincipal](embed-service-principal.md)**

    Din web app bruger Azure AD [Service Principal Object](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) til at godkende i forhold til Azure ad og få et *Azure ad-token*, der kun er app. Dette er kun en godkendelsesmetode for *apps* , som anbefales af Azure ad.

    Når du bruger en *tjeneste Principal*, skal du [aktivere Power bi API'er-adgang](embed-sample-for-customers.md#step-6---service-principal-api-access) i indstillingerne for Power bi-tjeneste *administrator* . Dette gør det muligt for din web-app at få adgang til Power BI REST-API'erne. Hvis du vil bruge API-handlinger på et arbejdsområde, skal *tjenestens hoved* navn være et *medlem* eller en *administrator* af arbejdsområdet.

* **Masterbruger**

    Din web app bruger en brugerkonto til godkendelse i forhold til Azure AD og henter *Azure ad-tokenet*. *Master brugeren* skal have en [Power bi Pro](/power-bi/admin/service-admin-purchasing-power-bi-pro) eller [Premium pr. bruger-licens (PPU)](/power-bi/admin/service-premium-per-user-faq) .

    Når du bruger en *Master bruger* , skal du definere din apps [delegerede tilladelser](/azure/active-directory/develop/v2-permissions-and-consent) (også kaldet områder). Der kræves *hoved bruger* eller *lejeradministrator* for at give samtykke til at bruge disse tilladelser ved hjælp af Power bi rest-API'er.

Når du har fuldført godkendelse i forhold til Azure AD, vil webappen generere et [indlejrings token](/rest/api/power-bi/embedtoken) , så brugerne kan få adgang til bestemte Power bi-indhold.

>[!NOTE]
>* Hvis du vil integrere ved hjælp af *integreringen til din kunde* løsning, skal du bruge en kapacitet med en, EM eller P-SKU.
>* Hvis du vil [skifte til produktion](move-to-production.md) , skal du bruge en kapacitet.

I følgende diagram vises godkendelsesprocessen for *integreringen til din kunde* løsning.

>[!div class="mx-imgBorder"]
>:::image type="content" source="media\embed-tokens\paas-authentiction.png" alt-text="Et diagram over godkendelsesprocessen i en integrering til dine kunder Power B I integreret analyse løsning.":::

1. Web app-bruger godkender i forhold til din Web App (med din godkendelsesmetode).

2. Din web app bruger en *tjeneste Principal* eller en *Master bruger* til at godkende i forhold til Azure ad.

3. Din Web App henter et *Azure ad-token* fra Azure ad og bruger det til at få adgang til Power bi rest-API'er. Adgangen til Power BI REST-API'erne gives ifølge din godkendelsesmetode, som enten er *tjeneste Principal* eller *hoved bruger*.

4. Web-appen kalder en fælles API-handling for et [embeds token](/rest/api/power-bi/embedtoken) , som anmoder om det *integrerede token*. Det *integrerede token* angiver, hvilket Power bi indhold kan integreres.

5. REST API'EN returnerer det *integrerede token* til din Web App.

6. Web App overfører det integrerede token til brugerens webbrowser.

7. Web App-brugeren bruger det integrerede token til at få adgang til Power BI.

### <a name="embed-for-your-organization"></a>Integrer indhold for din organisation

*Integrationen til din organisations* løsning bruger et interaktivt godkendelsesforløb. Dine brugere godkendes i forhold til Azure AD ved hjælp af deres Power BI legitimationsoplysninger. Brugere skal give tilladelse til de API-tilladelser, der blev angivet, da appen blev registreret med Azure AD. Samtykket er givet i dialogboksen Microsoft *Permissions Badd* op. Når samtykke er givet, kan Power BI indhold, f. eks. rapporter og dashboards, som Web App-brugeren har adgang til, integreres.

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/requested-premissions.png" alt-text="Skærmbillede, der viser et pop op-vindue med Microsoft-tilladelser, som beder brugerne om at tildele tilladelser til at få adgang til Power B I.":::

>[!NOTE]
>* *Integrationen til din organisations* løsning understøtter ikke et SKU'er.
>* Hvis du vil [skifte til produktion](move-to-production.md) , skal du bruge en af følgende konfigurationer:
>    * Alle brugere med Pro-licenser.
>    * Alle brugere med PPU-licenser.
>    * En [kapacitet](embedded-capacity.md). Denne konfiguration gør det muligt for alle brugere at have gratis licenser.

Dette diagram viser et eksempel på godkendelsesprocessen for *integreringen til din organisations* løsning.

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/saas-authentiction.png" alt-text="Et diagram over godkendelsesprocessen i en integrering til din organisation Power B i en integreret analyse løsning.":::

1. Web app-bruger får adgang til webappen.

2. Web-appen omdirigerer webappens bruger til Azure AD.

3. Web App-brugeren godkender i forhold til Azure AD ved hjælp af sine Power BI legitimationsoplysninger.

4. Azure AD omdirigerer webappens bruger tilbage til webappen med Azure AD-tokenet (i et implicit bonus scenarie returneres det pågældende adgangstoken til brugerens browser).

5. Web App overfører Azure AD-tokenet til brugerens webbrowser.

6. Din Power BI web app bruger Azure AD-tokenet til at integrere Power BI indhold, f. eks. rapporter og dashboards, som Web App-brugeren har adgangsrettigheder til.

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Overvejelser i forbindelse med generering af et integreringstoken](generate-embed-token.md)

>[!div class="nextstepaction"]
>[Kapacitet og SKU'er i Power BI Embedded-analyser](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Har du flere spørgsmål? Prøv at spørge Power BI-community'et](https://community.powerbi.com/)