---
title: Oversigt over migrering til Power BI
description: Få mere at vide om, hvordan du planlægger og udfører en migrering fra et andet tredjeparts-BI-værktøj til Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 8f8e58f61d2baa66cd0baf351857656588cfbe9f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419239"
---
# <a name="power-bi-migration-overview"></a>Oversigt over migrering til Power BI

Kunderne standardiserer i stigende grad, så de udelukkende baserer deres datakultur på Power BI, hvilket omfatter muligheden for administreret selvbetjenings-BI (SSBI), rationalisering af levering af virksomheds-BI og løsning af økonomiske problemer. Formålet med denne artikelserie om migrering til Power BI er at give dig en vejledning i, hvordan du planlægger og udfører en migrering fra et BI-tredjepartsværktøj til Power BI.

Artiklerne i serien om migrering til Power BI omfatter:

1. Oversigt over migrering til Power BI (denne artikel)
1. [Forbered migrering til Power BI](powerbi-migration-pre-migration-steps.md)
1. [Indsaml krav til migrering til Power BI (fase 1)](powerbi-migration-requirements.md)
1. [Planlæg udrulning ved migrering til Power BI (fase 2)](powerbi-migration-planning.md)
1. [Foretag blåstempling ved migrering til Power BI (fase 3)](powerbi-migration-proof-of-concept.md)
1. [Opret indhold ved migrering til Power BI (fase 4)](powerbi-migration-create-validate-content.md)
1. [Udrul til Power BI (fase 5)](powerbi-migration-deploy-support-monitor.md)
1. [Få mere viden fra kundemigrering til Power BI](powerbi-migration-learn-from-customers.md)

Der er to forudsætninger: Din organisation har i øjeblikket en ældre BI-platform, og det er besluttet af migrere indhold og brugere til Power BI. Migrering til Power BI-tjenesten er det primære fokus i denne serie. Der kan være yderligere overvejelser for nationale cloud-kunder ud over det, der er beskrevet i denne artikelserie.

I følgende diagram vises fire faser på højt niveau til udrulning af Power BI i din organisation.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="Billede, der viser de fire faser på højt niveau, som er beskrevet i følgende tabel.":::

|Fase|Beskrivelse|
|--------|-----------|
|![Fase 1.](media/common/icon-01-red-30x30.png)|**Konfigurer og evaluer Power BI.** Den første fase omfatter oprettelse af den første Power BI-arkitektur. På dette tidspunkt håndteres den indledende udrulning og planlægning af styring samt Power BI-evalueringer, herunder analyser af afkastningsgrad og rentabilitet.|
|![Fase 2.](media/common/icon-02-red-30x30.png)|**Opret hurtigt nye løsninger i Power BI.** I den anden fase kan forfattere, der bruger selvbetjening begynde at bruge og evaluere Power BI efter behov, og der kan hurtigt opnås værdi med Power BI. I aktiviteterne i fase 2 lægges der stor vægt på fleksibilitet og hurtig forretningsværdi, hvilket er vigtigt for at opnå accept ved valg af et nyt BI-værktøj, f. eks. Power BI. Af denne årsag viser diagrammet aktiviteter i fase 2 side om side med migreringsaktiviteterne i fase 3.|
|![Fase 3.](media/common/icon-03-red-30x30.png)|**Migrer BI-aktiver fra en ældre platform til Power BI.** Den tredje fase behandler migreringen til Power BI. Det er det, der fokuseres på, i denne artikelserie om migrering til Power BI. Der beskrives fem specifikke migreringsfaser i næste afsnit.|
|![Fase 4.](media/common/icon-04-red-30x30.png)|**Anvend, styr og overvåg Power BI.** Den sidste fase omfatter igangværende aktiviteter, f. eks. understøttelse af en datakultur, kommunikation og uddannelse. Disse aktiviteter har stor indflydelse på en effektiv Power BI-implementering. Det er vigtigt, at du har styrings-og sikkerhedspolitikker og -processer, der er relevante for din organisation, samt overvågning, så du kan skalere, vækste og løbende forbedre.|

> [!IMPORTANT]
> En formel migrering til Power BI sker næsten altid parallelt med udviklingen af en ny Power BI-løsning. _Power BI-løsning_ er en generisk term, der omfatter brug af både data og rapporter. En enkelt Power BI Desktop-fil (pbix) kan indeholde en datamodel eller en rapport eller begge dele. Der opfordres til [adskillelse af datamodellen fra rapporter](../guidance/report-separate-from-model.md) af hensyn til genbrug af data, men det er ikke påkrævet.
>
> Når du bruger Power BI til at udarbejde nye krav, mens du planlægger og udfører den formelle migrering, kan du få hjælp til at købe. Samtidige faser giver indholdsforfattere en praktisk, virkelighedslignende oplevelse med Power BI.

## <a name="five-stages-of-a-power-bi-migration"></a>Fem faser i en migrering til Power BI

Fase 3 i diagrammet vedrører migrering til Power BI. I denne fase er der fem almindelige faser.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="Billede, der viser faserne i en migrering til Power BI, som efterfølgende beskrives.":::

Følgende faser, der vises i det forrige diagram, er:

- [Trin før migrering](#pre-migration-steps)
- [Trin 1: Indsaml krav, og prioriter](#stage-1-gather-requirements-and-prioritize)
- [Fase 2: Planlæg udrulning](#stage-2-plan-for-deployment)
- [Fase 3: Foretag blålstempling](#stage-3-conduct-proof-of-concept)
- [Fase 4: Opret og valider indhold](#stage-4-create-and-validate-content)
- [Fase 5: Udrul, understøt og overvåg](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>Trin før migrering

Trinnene før migrering omfatter handlinger, du kan overveje, inden du starter et projekt til migrering af indhold fra en ældre BI-platform til Power BI. Det omfatter typisk den oprindelige planlægning af udrulning på lejerniveau. Du kan finde flere oplysninger om disse aktiviteter i [Forbered migrering til Power BI](powerbi-migration-pre-migration-steps.md).

### <a name="stage-1-gather-requirements-and-prioritize"></a>Fase 1: Indsaml krav, og prioriter

I fase 1 fokuseres der på indsamling af oplysninger og planlægning af migreringen af en enkelt løsning. Denne proces skal være iterativ og begrænses til en rimelig indsats. Resultatet af fase 1 omfatter en prioriteret oversigt over rapporter og data, der skal migreres. Det er nødvendigt med yderligere aktiviteter i fase 2 og 3, for at du kan vurdere, hvilken indsats det kræver. Du kan finde flere oplysninger om aktiviteterne i fase 1 under [Indsaml krav til migrering til Power BI](powerbi-migration-requirements.md).

### <a name="stage-2-plan-for-deployment"></a>Fase 2: Plan for udrulning

I fase 2 fokuseres der på, hvordan de krav, der er defineret i fase 1, kan opfyldes for hver specifik løsning. Resultatet af fase 2 omfatter så mange detaljer som muligt, der kan guide processen, selvom det er en iterativ, ikke-lineær proces. Oprettelse af en blåstempling (i trin 3) kan ske parallelt med denne fase. Selv når du opretter løsningen (i trin 4), kan der dukke yderligere oplysninger frem, der påvirker beslutninger om udrulningsplanen. I udrulningsplanlægningen i fase 2 fokuseres der på løsningsniveauet, samtidig med at de beslutninger, der allerede er truffet på organisationsniveau, respekteres. Du kan finde flere oplysninger om aktiviteterne i fase 2 under [Planlæg udrulning ved migrering til Power BI](powerbi-migration-planning.md).

### <a name="stage-3-conduct-proof-of-concept"></a>Fase 3: Foretag blåstempling

I fase 3 fokuseres der på løsning af ukendte problemer og afhjælpning af risici så tidligt som muligt. En teknisk blåstempling er nyttig til validering af forudsætninger, og den kan udføres iterativt sammen med planlægning af en udrulning (fase 2). Resultatet af denne fase er en Power BI-løsning, der har et begrænset omfang. Bemærk, at det ikke er meningen, at denne blåstempling skal være engangsarbejde. Det kræver dog sandsynligvis yderligere arbejde i fase 4 for at gøre den klar til produktion. I den forbindelse kan du i din organisation henvise til denne aktivitet som enten en prototype, et pilotprojekt, en mockup, en hurtig start eller en MVP (minimally viable product). Det er ikke altid nødvendigt at gennemføre en blåstempling, og det kan også finde sted mere uformelt. Du kan finde flere oplysninger om aktiviteterne i fase 3 under [Foretag blåstempling ved migrering til Power BI](powerbi-migration-proof-of-concept.md).

### <a name="stage-4-create-and-validate-content"></a>Fase 4: Opret og valider indhold

Fase 4 er der, hvor det faktiske arbejde med at konvertere blåstemplingen til en produktionsklar løsning udføres. Resultatet af denne fase er en fuldført Power BI-løsning, der er valideret i et udviklingsmiljø. Den skal være klar til udrulning i fase 5. Du kan finde flere oplysninger om aktiviteterne i fase 4 under [Opret indhold for at migrere til Power BI](powerbi-migration-create-validate-content.md).

### <a name="stage-5-deploy-support-and-monitor"></a>Fase 5: Udrul, understøt og overvåg

Det primære fokus i fase 5 er at udrulle den nye Power BI-løsning til produktion. Resultatet af denne fase er en produktionsløsning, der aktivt bruges af virksomhedsbrugere. Når du bruger en fleksibel metodologi, er det acceptabelt at have nogle planlagte forbedringer, der leveres i en fremtidig gentagelse. Afhængigt af dit komfortniveau i Power BI, f. eks. minimering af risici og brugerafbrydelser, kan du vælge at foretage en midlertidig gemt installation. Du kan også starte med at udrulle til en mindre gruppe pilotbrugere. Support og overvågning er også vigtig på dette stadium og på løbende basis. Du kan finde flere oplysninger om aktiviteterne i fase 5 under [Migrer til Power BI](powerbi-migration-deploy-support-monitor.md).

> [!TIP]
> De fleste af de begreber, der er beskrevet i denne artikelserie om migrering til Power BI, gælder også for et Power BI-standardimplementeringsprojekt.

## <a name="consider-migration-reasons"></a>Overvej årsagerne til migrering

Aktivering af en produktiv og sund datakultur er et primært mål for mange organisationer. Power BI er et glimrende værktøj, der gør det lettere at nå dette mål. De tre almindelige årsager til, at du kan overveje at overføre til Power BI, kan koges ned til følgende:

- **Aktivér administreret selvbetjenings-BI** ved at introducere nye funktioner, der styrker brugercommunity'et for selvbetjenings-BI. Power BI giver en bredere adgang til oplysninger og beslutningstagning, så afhængigheden af specialister, der kan være svære at finde, reduceres.
- **Rationaliser leveringen af virksomheds-BI** for at imødekomme krav, der ikke imødekommes af eksisterende BI-værktøjer, samtidig med at du reducerer kompleksitetsniveauet og ejeromkostningerne og/eller standardiserer fra flere BI-værktøjer, der aktuelt er i brug.
- **Løs økonomiske belastninger** for at øge produktiviteten med færre ressourcer, tid og personale.

## <a name="achieve-power-bi-migration-success"></a>Opnå succes med migrering til Power BI

Enhver migrering er lidt anderledes. Den kan afhænge af organisationsstrukturen, datastrategierne, dataadministrationens modenhed og organisationens målsætninger. Der er dog nogle fremgangsmåder, vi hele tiden ser hos de af vores kunder, der opnår en vellykket migrering til Power BI.

- **Støtte fra ledelsen:** Identificer en støtte i ledelsen tidligt i processen. Denne person skal være en, der aktivt understøtter BI i organisationen og er personligt investeret i at opnå et positivt resultat af migreringen. Det er ideelt, at støttepersonen fra ledelsen har den ultimative myndighed og ansvarlighed i forbindelse med de resultater, der er knyttet til Power BI.
- **Uddannelse, support og kommunikation:** Det er mere end blot en investering i teknologi. Alle BI- eller analyseprojekter er også en investering i mennesker, så overvej at investere tidligt i brugeruddannelse og -support. Du bør også oprette en kommunikationsplan med en gennemsigtig forklaring af, hvad der sker og hvorfor, til alle interessenter, og opstille realistiske forventninger. Sørg for at inkludere en feedbackløkke i din kommunikationsplan for at indsamle input fra interessenter.
- **Hurtige fordele:** Prioriter i første omgang elementer med høj værdi, der har en konkret værdi for virksomheden og er presserende. I stedet for udelukkende at forsøge at overføre rapporter nøjagtigt, som de vises på den gamle BI-platform, skal du fokusere på det forretningsspørgsmål, som rapporten prøver at besvare – herunder den handling, der skal udføres – når du skal designe den nye rapport.
- **Modernisering og forbedringer:** Vær villig til at overveje, hvordan tingene altid er blevet gjort. En migrering kan give dig mulighed for forbedringer. Det kan f. eks. eliminere klargøring af manuelle data eller flytte forretningsregler, der er begrænset til en enkelt rapport. Overvej at omstrukturere, modernisere og konsolidere eksisterende løsninger, når indsatsen kan begrundes. Det kan omfatte konsolidering af flere rapporter til én, eller fjernelse af ældre artefakter, der ikke er blevet brugt i et stykke tid.
- **Løbende undervisning:** Vær forberedt på at bruge en faseinddelt tilgang, mens du hele tiden lærer og tilpasser. Arbejd med korte, iterative cyklusser for hurtigt at skabe værdi. Gør det til en vane hyppigt at udføre mindre blåstemplinger for at mininimere risikoen for ukendte problemer, validere forudsætninger og få mere at vide om nye funktioner. Da Power BI er en cloudtjeneste, der opdateres månedligt, er det vigtigt, at du holder øje med udviklingen og justerer kurset, når det er relevant.
- **Modstand mod ændring:** Forstå, at der kan være forskellige niveauer af modstand mod ændringer – nogle brugere vil have modstand mod at sætte sig ind i et nyt værktøj. Det kan også være, at nogle af de professionelle, der har dedikeret meget tid og arbejde til at blive eksperter i et andet BI-værktøj, føler sig overflødige. Vær forberedt, da det kan resultere i interne politiske uenigheder, især i virksomheder, der er meget decentraliserede.
- **Begrænsninger:** Vær realistisk, hvad angår migreringsplaner, herunder finansiering, tidsestimater samt roller og ansvar for alle involverede.

## <a name="acknowledgments"></a>Bekræftelser

Denne artikelserie er skrevet af Melissa Coates, Data Platform MVP og ejer af [Coates Data Strategies](https://www.coatesdatastrategies.com/). Bidragydere og anmeldere omfatter Marc Reguera, Venkatesh Titte, Patrick Baumgartner, Tamer Farag, Richard Tkachuk, Matthew Roche, Adam Saxton, Chris Webb, Mark Vaillancourt, Daniel Rubiolo, David Iseminger og Peter Myers.

## <a name="next-steps"></a>Næste trin

I [næste artikel i denne artikelserie om migrering til Power BI](powerbi-migration-pre-migration-steps.md)kan du få mere at vide om trinnene før migrering, når du migrerer til Power BI.

Andre nyttige ressourcer omfatter:

- [Microsofts BI-transformation](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Hvidbog om planlægning af en Power BI Enterprise-installation](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Overfør SSRS-rapporter til Power BI](migrate-ssrs-reports-to-power-bi.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

Der findes erfarne Power BI-partnere, som kan hjælpe din organisation med at gennemføre migreringsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).
