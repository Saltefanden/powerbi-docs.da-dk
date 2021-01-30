---
title: Her skal du bruge sideinddelte rapporter i Power BI
description: Vejledning til, hvornår du skal bruge sideinddelte rapporter i Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/04/2020
ms.openlocfilehash: a8cf6611597ec0dcf9f207b62e7e9e9f5035cfca
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087999"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Her skal du bruge sideinddelte rapporter i Power BI

Denne artikel henvender sig til rapportforfattere, der designer rapporter til Power BI. Den indeholder forslag, der kan hjælpe dig med at vælge, hvornår du skal udvikle [sideinddelte rapporter i Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md).

> [!NOTE]
> Udgivelse af sideinddelte rapporter i Power BI kræver et Power BI Premium-abonnement. Rapporter gengives kun, når de er i et arbejdsområde i en kapacitet, der har [arbejdsbelastningen for sideinddelte rapporter aktiveret](../admin/service-admin-premium-workloads.md#paginated-reports).

Sideinddelte rapporter i Power BI er optimeret til **udskrivning** eller **generering af PDF**. De giver dig også mulighed for at oprette layout med megen formatering og perfekt pixel. Så sideinddelte rapporter er velegnede til driftsrapporter, f.eks. salgsfakturaer.

Som kontrast er Power BI-rapporter optimeret til **udforskning og interaktivitet**. De kan også præsentere dine data ved hjælp af et omfattende udvalg af ultramoderne visualiseringer. Power BI-rapporter er derfor ideelle til analyserapporter, hvilket gør det muligt for dine rapportbrugere at udforske data og finde relationer og mønstre.

Vi anbefaler, at du evt. overvejer at bruge en sideinddelt rapport i Power BI, når:

- Du ved, at rapporten skal være trykt eller udskrevet som et PDF-dokument.
- Datagitterlayout kan udvides og overskrides. Tag højde for, at en tabel eller matrix i en Power BI-rapport ikke kan tilpasse størrelsen dynamisk, så der vises alle data – den viser i stedet rullepaneler. Men hvis den udskrives, vil det ikke være muligt at rulle for at få vist alle de data, der ikke er synlige.
- Funktionerne med sideinddeling i Power BI er en stor fordel for dig. Mange af disse rapportscenarier beskrives senere i denne artikel.

## <a name="legacy-reports"></a>Ældre rapporter

Når du allerede har SSRS-rapporter (SQL Server Reporting Services) [RDL-rapporter (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs), kan du vælge at udvikle dem igen som [Power BI-rapporter](../consumer/end-user-reports.md) eller overføre dem som sideinddelte rapporter til Power BI. Du kan få flere oplysninger ved at se [Overfør SQL Server Reporting Services-rapporter til Power BI](migrate-ssrs-reports-to-power-bi.md).

Når du har udgivet en sideinddelt rapport til et Power BI-arbejdsområde, er de sideinddelte rapporter tilgængelige side om side med Power BI-rapporter. De kan derefter nemt distribueres ved hjælp af [Power BI-apps](../collaborate-share/service-create-distribute-apps.md).

Du kan overveje at udvikle SSRS-rapporter i stedet for at overføre dem. Det er især tilfældet for de rapporter, der er beregnet til at levere analyser. I disse tilfælde vil Power BI-rapporter sandsynligvis levere bedre rapporter for brugeren.

## <a name="paginated-report-scenarios"></a>Scenarier med sideinddelte rapporter

Der er mange overbevisende scenarier, når du kan få fordel af at udvikle en sideinddelt rapport i Power BI. Mange er funktioner eller egenskaber, der ikke understøttes af Power BI-rapporter.

- **Klar til udskrivning**: Sideinddelte rapporter er optimeret til udskrivning eller generering af PDF. Når det er nødvendigt, kan dataområder udvides og overskrides til flere sider på en kontrolleret måde. Dine rapportlayout kan definere margener og sidehoveder samt sidefødder.
- **Gengivelsesformater**: Power BI kan gengive sideinddelte rapporter i forskellige formater. Formater omfatter Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML og MHTML. (MHTML-formatet bruges af Power BI-tjenesten til at gengive rapporter). Dine rapportbrugere kan vælge at eksportere i det format, der passer til dem.
- **Præcisionslayout**: Du kan designe layout med megen formatering og med perfekt pixel – til den nøjagtige størrelse og placering, der er konfigureret i brøkdele af tommer eller centimeter.
- **Dynamisk layout**: Du kan fremstille meget dynamiske layout ved at angive mange rapportegenskaber, der skal bruge VB.NET-udtryk. Udtryk har adgang til mange kerne .NET Framework-biblioteker.
- **Gengivelsesspecifikt layout**: Du kan bruge udtryk til at redigere rapportlayoutet på baggrund af det anvendte gengivelsesformat. Du kan f.eks. designe rapporten til at deaktivere skiftende synlighed (for at opnå detailudledning og færre detaljer), når den gengives ved hjælp af et ikke-interaktivt format, f.eks. PDF.
- **Oprindelige forespørgsler**: Du behøver ikke først at udvikle et Power BI-datasæt. Det er muligt at oprette oprindelige forespørgsler (eller bruge gemte procedurer) til alle [understøttede datakilder](../paginated-reports/paginated-reports-data-sources.md). Forespørgsler kan indeholde parametre.
- **Grafiske forespørgselsdesignere**: Power BI Report Builder indeholder grafiske forespørgselsdesignere, der kan hjælpe dig med at skrive og teste dine forespørgsler på datasæt.
- **Statiske datasæt**: Du kan definere et datasæt og angive data direkte i din rapportdefinition. Denne funktion er især nyttig til at understøtte en demo eller til levering af en blåstempling.
- **Dataintegration**: Du kan kombinere data fra forskellige datakilder eller med statiske datasæt. Det gøres ved at oprette brugerdefinerede felter ved hjælp af VB.NET-udtryk.
- **Parametre**: Du kan designe meget tilpassede oplevelser med parametre, herunder datadrevne og overlappende parametre. Det er også muligt at definere parameterstandarder. Disse oplevelser kan designes, så brugerne hurtigt kan angive relevante filtre. Parametre behøver desuden ikke at filtrere rapportdata. De kan bruges til at understøtte "what if"-scenarier eller dynamisk filtrering eller formatering.
- **Billeddata**: Din rapport kan gengive billeder, når de er gemt i binært format i en datakilde.
- **Brugerdefineret kode**: Du kan udvikle kodeblokke af VB.NET-funktioner i din rapport og bruge dem i et rapportudtryk.
- **Underrapporter**: Du kan integrere andre sideinddelte rapporter i Power BI (fra det samme arbejdsområde) i din rapport.
- **Fleksible datagitre**: Du har detaljeret kontrol over gitterlayout ved hjælp af tablix-dataområdet. Det understøtter også komplekse layout, herunder indlejrede og tilstødende grupper. Og det kan konfigureres til at gentage overskrifter, når de udskrives over flere sider. Det kan også integrere en underrapport eller andre visualiseringer, herunder datalinjer, minidiagrammer og indikatorer.
- **Afstandsdatatyper**: Kortdataområdet kan visualisere [SQL Server-afstandsdatatyper](/sql/relational-databases/spatial/spatial-data-sql-server). Derfor kan datatyperne GEOGRAFI og GEOMETRI bruges til at visualisere punkter, linjer eller polygoner. Det er også muligt at visualisere polygoner, der er defineret i ESRI-formfiler.
- **Moderne målere**: Radiale og lineære målere kan bruges til at få vist KPI-værdier og status. De kan også integreres i gitterdataområder, der gentages i grupper.
- **HTML-gengivelse**: Du kan få vist formateret tekst, når den gemmes som HTML.
- **Brevfletning**: Du kan bruge pladsholdere til tekstfelter til at indsætte dataværdier i tekst. På denne måde kan du oprette en brevfletningsrapport.
- **Interaktivitetsfunktioner**: Interaktive funktioner omfatter skift af synlighed (for at opnå detailudledning og færre detaljer), links, interaktiv sortering og værktøjstip. Du kan også tilføje links, der indeholder detaljeadgang til Power BI-rapporter eller andre sideinddelte rapporter i Power BI. Links kan også springe til en anden placering i samme rapport.
- **Abonnementer**: Power BI kan levere sideinddelte rapporter efter en tidsplan som mails med vedhæftede filer af rapporter i ethvert format, der understøttes.
- **Pr. bruger-layout**: Du kan oprette dynamiske rapportlayout på baggrund af den godkendte bruger, der åbner rapporten. Du kan designe rapporten, så du kan filtrere data anderledes, skjule dataområder eller visualiseringer, anvende forskellige formater eller angive brugerspecifikke parameterstandarder.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Hvad er sideinddelte rapporter i Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Overfør SQL Server Reporting Services-rapporter til Power BI](migrate-ssrs-reports-to-power-bi.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
