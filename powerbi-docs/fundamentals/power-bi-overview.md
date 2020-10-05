---
title: Hvad er Power BI?
description: Oversigt over Power BI, og hvordan de forskellige dele passer sammen – Power BI Desktop, Power BI-tjeneste, Power BI Mobil, rapportserver og Power BI Embedded.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 09/23/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 2c793cf0b7af6f6a7fdbc6196052ac357b6ddd12
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/26/2020
ms.locfileid: "91375325"
---
# <a name="what-is-power-bi"></a>Hvad er Power BI?
**Power BI** er en samling af softwaretjenester, apps og forbindelser, der arbejder sammen for at forvandle usammenhængende data til faste, visuelt fordybende og interaktive indsigter. Dine data kan være et Excel-regneark eller en samling cloudbaserede hybride data warehouses og hybride data warehouses i det lokale miljø. Med Power BI kan du nemt oprette forbindelse til dine datakilder, visualisere og finde vigtigt indhold samt dele det med alle, du vil.

## <a name="the-parts-of-power-bi"></a>Delene i Power BI
Power BI består af flere elementer, der alle arbejder sammen, og som starter med følgende tre grundlæggende punkter: 
- Et skrivebordsprogram til Windows, der hedder **Power BI Desktop**.
- En onlinetjeneste af typen SaaS (*Software som en service*) kaldet **Power BI-tjeneste**. 
- Power BI-**mobilapps** til Windows-, iOS- og Android-enheder.

![Skærmbillede af diagram over Power BI Desktop, Power BI-tjenesten og Power BI – Mobil, der viser integrationen af dem.](media/power-bi-overview/power-bi-overview-blocks.png)

Disse tre elementer &mdash; Power BI Desktop, tjenesten og mobilappsene &mdash; er designet til at lade dig oprette, dele og bruge forretningsindsigt på en måde, der opfylder dit behov og din rolle mest effektivt.

Ud over disse tre elementer indeholder Power BI også to andre elementer:

- **Power BI Report Builder** til oprettelse af sideinddelte rapporter, der skal deles i Power BI-tjenesten. Læs mere om [sideinddelte rapporter](#paginated-reports-in-the-power-bi-service) senere i denne artikel.
- **Power BI-rapportserver**, en rapportserver i det lokale miljø, hvor du kan publicere dine Power BI-rapporter, når du har oprettet dem i Power BI Desktop. Læs mere om [Power BI-rapportserver](#on-premises-reporting-with-power-bi-report-server) senere i denne artikel.

## <a name="how-power-bi-matches-your-role"></a>Sådan passer Power BI til din rolle
Din brug af Power BI kan afhænge af din rolle i et projekt eller på et team. Andre personer med andre roller bruger måske Power BI på en anden måde.

Du bruger f.eks. primært **Power BI-tjenesten** til at få vist rapporter og dashboards. En talfokuseret kollega med ansvar for oprettelse af forretningsrapporter bruger måske overvejende **Power BI Desktop** eller **Power BI Report Builder** til oprettelse af rapporter og udgiver derefter de pågældende rapporter til Power BI-tjenesten, hvor du kan se dem. En anden kollega arbejder måske med salg og bruger hovedsageligt **Power BI-telefonappen** til at overvåge sine salgskvoter og til at analysere nye salgsemners oplysninger.

Hvis du er udvikler, bruger du måske Power BI-API'er til at pushe data til datasæt eller til at integrere dashboards og rapporter i dine egne brugerdefinerede programmer. Har du en ide til et nyt visuelt element? Skab det selv, og del det med andre.  

Det kan også være, du bruger alle elementer af Power BI på forskellige tidspunkter, afhængigt af hvad du arbejder med, eller hvad din rolle er i et bestemt projekt.

Den måde, du bruger Power BI på, kan være baseret på, hvilken funktion eller tjeneste i Power BI der er det bedste værktøj i din situation. Du kan f.eks. bruge Power BI Desktop til at oprette rapporter for dit eget team om statistikker for kundeengagementer, og du kan få vist lager og produktionsfremskridt på et dashboard i realtid i Power BI-tjenesten. Du kan oprette en sideinddelt rapport over fakturaer, der kan sendes via mail, baseret på et Power BI-datasæt. Alle dele af Power BI er tilgængelige for dig, og derfor er det fleksibelt og overbevisende.

Udforsk dokumenter, der er relevante for din rolle:
- Power BI til [*erhvervsbrugere*](../consumer/end-user-consumer.md)
- Power BI Desktop til [*rapportoprettere*](desktop-what-is-desktop.md)
- Power BI Report Builder til [*rapportoprettere i virksomheder*](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- Power BI for [*administratorer*](../admin/service-admin-administering-power-bi-in-your-organization.md)
- Power BI til *udviklere*
    * [Integreret analyse med Power BI](../developer/embedded/embedding.md)
    * [Hvad er Power BI Embedded i Azure?](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)
    * [Visuals i Power BI](../developer/visuals/power-bi-custom-visuals.md)
    * [Hvad kan udviklere bruge Power BI-API'en til?](../developer/automation/overview-of-power-bi-rest-api.md)

## <a name="the-flow-of-work-in-power-bi"></a>Arbejdsgangen i Power BI
Et almindelig arbejdsproces i Power BI starter med, at du opretter forbindelse til datakilder i Power BI Desktop og opretter en rapport. Du publicerer derefter den pågældende rapport fra Power BI Desktop til Power BI-tjenesten og deler den, så erhvervsbrugere i Power BI-tjenesten og på mobilenhederne kan se og interagere med rapporten.

Denne arbejdsproces er almindelig og viser, hvordan de tre hovedelementer i Power BI komplementerer hinanden.

Her er en detaljeret [sammenligning af Power BI Desktop og Power BI-tjenesten](../fundamentals/service-service-vs-desktop.md).

## <a name="paginated-reports-in-the-power-bi-service"></a>Sideinddelte rapporter i Power BI-tjenesten

En anden arbejdsproces omfatter sideinddelte rapporter i Power BI-tjenesten. Rapportoprettere i virksomheder designer sideinddelte rapporter, der skal udskrives eller deles. De kan også dele disse rapporter i Power BI-tjenesten. De kaldes *sideinddelte*, fordi de er formateret til at passe godt på en side. De bruges ofte som driftsrapporter eller til udskrivning af formularer, f. eks. fakturaer eller transskriptioner. De viser alle data i en tabel, selvom tabellen strækker sig over flere sider. Power BI Report Builder er det separate værktøj, der bruges til oprettelse af sideinddelte rapporter.

:::image type="content" source="media/power-bi-overview/paginated-report-invoice-power-bi-service.png" alt-text="Skærmbillede af sideinddelt rapport i Power BI-tjenesten.":::

Læs mere om [sideinddelte rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md) i Power BI-tjenesten.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Rapportering i det lokale miljø med Power BI-rapportserveren

Hvad nu, hvis du har brug for at gemme dine rapporter i det lokale miljø, f.eks. bag en firewall?  Læs videre.

Du kan oprette, udrulle og administrere Power BI-rapporter i Power BI Desktop og sideinddelte rapporter i Report Builder med de brugsklare værktøjer og tjenester, der findes i Power BI-rapportserver.

![Diagram over Power BI-rapportserver, Power BI-tjenesten og Power BI – Mobil, der viser integrationen af dem.](media/power-bi-overview/power-bi-report-server2.png)

Power BI-rapportserveren er en løsning, som du udruller bag firewallen, og som derefter leverer dine rapporter til de rette brugere på forskellige måder, uanset om de skal vises i en webbrowser, på en mobilenhed eller som en mail. Og da Power BI-rapportserveren er kompatibel med Power BI i clouden, kan du flytte til clouden, når du er klar. 

Læs mere om [Power BI-rapportserver](../report-server/get-started.md).

## <a name="next-steps"></a>Næste trin
- [Hurtig start: Find vej i Power BI-tjenesten](../consumer/end-user-experience.md)   
- [Selvstudium: Kom i gang med Power BI-tjenesten](service-get-started.md)
- [Hurtig start: Opret forbindelse til data i Power BI Desktop](../connect-data/desktop-quickstart-connect-to-data.md)
