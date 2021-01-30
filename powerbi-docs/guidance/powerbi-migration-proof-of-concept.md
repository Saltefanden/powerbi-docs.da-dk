---
title: Foretag blåstempling ved migrering til Power BI
description: Vejledning i blåstempling ved migrering til Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: a51aaee15fc2a5e8d8facc1d34c0724dfa71d663
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086504"
---
# <a name="conduct-proof-of-concept-to-migrate-to-power-bi"></a>Foretag blåstempling ved migrering til Power BI

I denne artikel beskrives **fase 3**, der omfatter blåstempling for at afhjælpe risici og imødekomme ukendte problemer så tidligt som muligt ved migrering til Power BI.

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="Billede, der viser faserne i en migrering til Power BI. Der fokuseres på fase 3 i denne artikel.":::

> [!NOTE]
> Du kan finde en komplet forklaring af ovenstående grafik under [Oversigt over migrering til Power BI](powerbi-migration-overview.md).

I fase 3 fokuseres der på at løse ukendte problemer og afhjælpe risici så tidligt som muligt. En teknisk blåstempling er nyttig til validering af forudsætninger. Det kan ske iterativt sammen med planlægning af en udrulning af løsninger (beskrevet i [fase 2](powerbi-migration-planning.md)).

Resultatet af denne fase er en Power BI-løsning, der har et begrænset omfang, imødekommer de indledende åbne spørgsmål og er parat til yderligere arbejde i [fase 4](powerbi-migration-create-validate-content.md), så den bliver klar til produktion.

> [!IMPORTANT]
> Det er ikke meningen, at denne blåstempling skal være engangsarbejde. I stedet forventer vi, at det er en tidlig gentagelse af den løsning, der er klar til produktion. I din organisation kan du henvise til denne aktivitet som en prototype, et pilotprojekt, en mockup, en hurtig start eller en MVP (minimally viable product). Det er ikke altid nødvendigt at gennemføre en blåstempling, og det kan også ske mere uformelt.

> [!TIP]
> De fleste af de emner, denne artikel omhandler, gælder også for et Power BI-standardimplementeringsprojekt. Efterhånden som din organisation bliver mere erfaren med Power BI, bliver behovet for blåstempling mindre. Men på grund af udgivelseshyppigheden for Power BI og den løbende introduktion af nye funktioner, kan du jævnligt udføre tekniske blåstempling med henblik på læring.

## <a name="set-poc-goals-and-scope"></a>Angiv mål og omfang for blåstempling

Når du udfører en blåstempling, skal du fokusere på følgende mål:

- Bekræft dine forudsætninger for, hvordan en funktion fungerer.
- Sæt dig ind i forskelle mellem den måde Power BI fungerer på sammenlignet med den ældre BI-platform.
- Valider den indledende forståelse af visse krav sammen med eksperter inden for emnet.
- Opret et lille datasæt med reelle data for at få indblik i og registrere eventuelle problemer med datastrukturen, relationerne, datatyperne eller dataværdierne.
- Eksperimenter med og valider udtryk med [DAX-syntaks](/dax/), der bruges af modelberegninger.
- Test forbindelsen til datakilden ved hjælp af en gateway (hvis det skal være en gatewaykilde).
- Test opdateringen af data ved hjælp af en gateway (hvis det skal være en gatewaykilde).
- Kontrollér sikkerhedskonfigurationer, herunder sikkerhed på rækkeniveau, når det er relevant.
- Eksperimenter med layout og udseende.
- Kontrollér, at al funktionalitet i Power BI-tjenesten fungerer som forventet.

Området for blåstempling afhænger af, hvad de ukendte problemer er, eller hvilke mål der skal valideres sammen med kolleger. Hvis du vil reducere kompleksiteten, skal du sørge for, at blåstemplingens omfang er så begrænset som muligt.

Det gælder som oftest for en migrering, at kravene er velkendte, fordi der er en eksisterende løsning at starte med. Afhængigt af omfanget af forbedringer, der skal foretages, eller eksisterende Power BI-kompetencer, er en blåstempling stadig meget værd. Derudover kan hurtig prototyper med feedback fra forbrugerne være velegnet til hurtigt at afklare krav – især hvis der foretages forbedringer.

> [!IMPORTANT]
> Selvom en blåstempling kun indeholder et undersæt af data eller kun indeholder begrænsede visuals, er det ofte vigtigt at gennemføre den fra start til slut. Det vil sige fra udvikling i Power BI Desktop til udvikling i et udviklingsarbejdsområde i Power BI-tjenesten. Det er den eneste måde, du kan fuldføre målsætningerne for blåstempling på. Det er især tilfældet, når Power BI-tjenesten skal levere kritisk funktionalitet, du ikke har brugt før, f. eks. et DirectQuery-datasæt, der bruger enkeltlogon. Under blåstemplingen skal du fokusere på de aspekter, du er i tvivl om eller skal bekræfte sammen med andre.

## <a name="handle-differences-in-power-bi"></a>Håndter forskelle i Power BI

Power BI kan bruges som et _modelbaseret værktøj_ eller som et _rapportbaseret værktøj_. En modelbaseret løsning omfatter udvikling af en datamodel, mens en rapportbaseret løsning opretter forbindelse til en datamodel, der allerede er udrullet.

På grund af den ekstreme fleksibilitet er der nogle aspekter ved Power BI, der kan være grundlæggende forskellige i forhold til den ældre BI-platform, du migrerer fra.

### <a name="consider-redesigning-the-data-architecture"></a>Overvej at designe dataarkitekturen igen

Hvis du migrerer fra en ældre BI-platform, der har sit eget semantiske lag, er oprettelsen af et importdatasæt sandsynligvis et godt valg. Power BI fungerer bedst sammen med et tabeldesign af typen [stjerneskema](star-schema.md). Hvis det tidligere semantiske lag ikke er et stjerneskema, kræver det muligvis en ændring af designet for at udnytte Power BI fuldt ud. Hvis du vil definere et semantisk lag, der er i overensstemmelse med designprincipperne for stjerneskemaer (herunder relationer, ofte brugte målinger og brugervenlige organisatoriske terminologi), fungerer det som et glimrende udgangspunkt for rapportforfattere, der bruger selvbetjening.

Hvis du migrerer fra en ældre BI-platform, hvor rapporter refererer til relationsdatakilder ved hjælp af SQL-forespørgsler eller lagrede procedurer, og hvis du planlægger at bruge Power BI i [DirectQuery-tilstand](../connect-data/desktop-use-directquery.md), kan du muligvis opnå en migrering af datamodellen, der er tæt på én til én.

> [!CAUTION]
> Hvis du kan se, at der oprettes mange Power BI Desktop-filer, der består af en enkelt importeret tabel, er det normalt en indikator på, at designet ikke er optimalt. Hvis du bemærker dette problem, skal du undersøge, om brugen af [delte datasæt](../connect-data/service-datasets-across-workspaces.md), der er oprettet ved hjælp af et design af typen [stjerneskema](star-schema.md), kan give et bedre resultat.

### <a name="decide-how-to-handle-dashboard-conversions"></a>Fastlæg, hvordan dashboardkonverteringer skal håndteres

I BI-branchen er et dashboard en samling visuals, der viser vigtige metrikværdier på en enkelt side. Men i Power BI repræsenterer et dashboard en bestemt visualiseringsfunktion, der kun kan oprettes i Power BI-tjenesten. Når du overfører et dashboard fra en ældre BI-platform, har du to valgmuligheder:

1. Det ældre dashboard kan oprettes igen som en Power BI-_rapport_. De fleste rapporter oprettes med Power BI Desktop. Sideinddelte rapporter og Excel-rapporter er alternative muligheder.
2. Det ældre dashboard kan oprettes igen som et Power BI-_dashboard_. [Dashboards](../fundamentals/service-basic-concepts.md#dashboards) er en visualiseringsfunktion i Power BI-tjenesten. Du opretter ofte dashboardsvisuals ved at fastgøre visuals fra en eller flere rapporter, Spørgsmål og svar eller Hurtig indsigt.

> [!TIP]
> Da dashboards er en Power BI-indholdstype, skal du undlade at bruge ordet _dashboard_ i navnet på en rapport eller et dashboard.

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>Fokuser på de store linjer, når du opretter visuals igen

Alle BI-værktøjer har sine styrker og fokusområder. Derfor har de rapportvisuals, du var afhængig af på en ældre BI-platform, muligvis ikke en ækvivalent, der kommer tæt på, i Power BI.

Når du opretter rapportvisuals igen, skal du fokusere mere på de store linjer, der behandles i rapporten. Det fjerner presset om at replikere alle visualdesigns på nøjagtigt den samme måde. Indholdsforbrugere værdsætter konsistens, når de bruger migrerede rapporter, men det er vigtigt ikke at blive fanget i tidskrævende diskussioner om små detaljer.

## <a name="next-steps"></a>Næste trin

I [næste artikel i denne serie om migrering til Power BI](powerbi-migration-create-validate-content.md)kan du få mere at vide om fase 4, der omhandler oprettelse og validering af indhold ved migrering til Power BI.

Andre nyttige ressourcer omfatter:

- [Microsofts BI-transformation](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Hvidbog om planlægning af en Power BI Enterprise-installation](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

Der findes erfarne Power BI-partnere, som kan hjælpe din organisation med at gennemføre migreringsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).
