---
title: Forbered migrering til Power BI
description: Vejledning til trin forud for migrering til Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: fba37d9f73ea0f61d8a43dc46cd13a5835d4d2a9
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/29/2020
ms.locfileid: "91525794"
---
# <a name="prepare-to-migrate-to-power-bi"></a>Forbered migrering til Power BI

Denne artikel indeholder handlinger, du kan overveje, før du migrerer til Power BI.

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="Billede, der viser faserne i en migrering til Power BI. Trinnene forud for migrering er fremhævet i denne artikel.":::

> [!NOTE]
> Du kan finde en komplet forklaring af ovenstående grafik under [Oversigt over migrering til Power BI](powerbi-migration-overview.md).

Trinnene forud for migrering fremhæver planlægning på forhånd, hvilket er et vigtig forberedelsestrin forud for gennemførelsen af de fem migreringsfaser. De fleste trin forud for migrering forekommer én gang, selvom nogle af delene kan være iterativ for hver forretningsenhed eller afdeling i større organisationer.

Outputtet fra trinnene forud for migrering omfatter en indledende styringsmodel, indledende planlægning af udrulning på højt niveau samt en oversigt over de rapporter og data, der skal migreres. Yderligere oplysninger fra aktiviteter i fase 1, 2 og 3 er nødvendige for fuldt ud at estimere, hvor stor en indsats migrering af de enkelte løsninger kræver.

> [!TIP]
> De fleste af de emner, denne artikel omhandler, gælder også for et Power BI-standardimplementeringsprojekt.

## <a name="create-costbenefit-analysis-and-evaluation"></a>Udfør en analyse af omkostninger/fordele og en evaluering

Nogle af vigtigste overvejelser under den indledende evaluering omfatter:

- Klarhed over virksomhedscasen og BI-strategien for at opnå en bestemt ønsket tilstand i fremtiden.
- Klarhed over, hvad succes betyder, og hvordan fremskridt og succes måles i forbindelse med migreringsinitiativet.
- Resultaterne af beregningen af omkostningsestimater og investeringsafkast.
- Vellykkede resultater af flere produktive Power BI-initiativer, som har et mindre omfang og et lavere kompleksitetsniveau.

## <a name="identify-stakeholders-and-executive-support"></a>Identificer interessenter og ledelsessupport

Flere overvejelser i forbindelse med identificering af interessenter omfatter:

- Sørg for at være enige med interessenterne om forretningscasen og BI-strategien.
- Inddrag repræsentanter fra hele forretningsenheden, også selvom deres indhold er planlagt til at blive migreret på et senere tidspunkt, for at forstå deres motivation og bekymringer.
- Inddrag Power BI-mestre tidligt.
- Opret – og følg – en kommunikationsplan med interessenter.

> [!TIP]
> Hvis du er bange for, at du begynder at kommunikere for meget, så har du sikkert ret.

## <a name="generate-initial-governance-model"></a>Generér en model for indledende styring

Flere af de vigtigste punkter, der skal håndteres tidligt i implementeringen af Power BI, omfatter:

- Bestemte mål for indførelse af Power BI, og hvordan Power BI passer ind i den overordnede BI-strategi for organisationen.
- Hvordan Power BI-administratorrollen skal håndteres, især i decentraliserede organisationer.
- Politikker til at opnå pålidelige data: brug af autoritative datakilder, håndtering af problemer med datakvaliteten og brug af ensartet terminologi og almindelige definitioner.
- Strategi for sikkerhed og beskyttelse af personlige oplysninger for datakilder, datamodeller, rapporter og levering af indhold til interne og eksterne brugere.
- Hvordan interne og eksterne krav til overholdelse af angivne standarder og overvågningskrav opfyldes.

> [!IMPORTANT]
> Den mest effektive styringsmodel bestræber sig på at balancere bemyndigelse af brugere med det nødvendige kontrolniveau. Hvis du vil have flere oplysninger, kan du læse mere under [central disciplin](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) og [fleksibilitet på grænseenheder](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="conduct-initial-deployment-planning"></a>Udfør indledende planlægning af udrulning

Indledende planlægning af udrulning omfatter definition af standarder, politikker og indstillinger for organisationens implementering af Power BI.

Bemærk, at [fase 2](powerbi-migration-planning.md) refererer til planlægning af udrulning på løsningsniveau. Aktiviteterne i fase 2 bør respektere beslutningerne på organisationsniveau, når det er muligt.

Nogle af de vigtigste punkter, der skal håndteres tidligt i implementeringen af Power BI, omfatter:

- Beslutninger om [indstillinger for Power BI-lejer](admin-tenant-settings.md), som bør dokumenteres.
- Beslutninger om [administration af arbejdsområder](../collaborate-share/service-new-workspaces.md), som bør dokumenteres.
- Overvejelser og indstillinger relateret til data og [metoder til distribution af indhold](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md), f.eks. apps, arbejdsområder, deling, abonnementer og integrering af indhold.
- Indstillinger relateret til [tilstande for datasæt](../connect-data/service-dataset-modes-understand.md), f.eks. brug af Import-tilstand, DirectQuery-tilstand eller en kombination af disse to tilstande i en [Sammensat model](composite-model-guidance.md).
- [Sikring af data og adgang](../admin/service-admin-power-bi-security.md).
- Arbejde med [delte datasæt](../connect-data/service-datasets-share.md) med henblik på genanvendelighed.
- Anvendelse af [datacertificering](../connect-data/service-datasets-certify.md) for at fremme brugen af autoritative og pålidelige data.
- Brug af forskellige [rapporttyper](../create-reports/index.yml), herunder Power BI-rapporter, Excel-rapporter eller sideinddelte rapporter til forskellige use cases eller forretningsenheder.
- Tilgange til administration af ændringer med henblik på at administrere centraliserede BI-artefakter og forretningsadministrerede BI-artefakter.
- Oplæringsplaner til forbrugere, dataudformere, rapportforfattere og administratorer.
- Support til indholdsforfattere ved hjælp af [Power BI Desktop-skabeloner](../create-reports/desktop-templates.md), [brugerdefinerede visualiseringer](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/) og dokumenterede standarder for rapportdesign.
- Procedurer og processer til administration af brugerkrav, f.eks. anmodning om nye licenser, tilføjelse af nye datakilder for gateways, indhentning af tilladelse til datakilder for gateways, anmodning om nye arbejdsområder, ændringer af tilladelser til arbejdsområder og andre almindelige krav, der kan opstå med jævne mellemrum.

> [!IMPORTANT]
> Planlægning af udrulning er en iterativ proces. Beslutningerne om udrulning redefineres og forstærkes mange gange, i takt med at din organisations erfaring med Power BI vokser, og i takt med at Power BI udvikler sig. De beslutninger, der træffes under denne proces, bruges under planlægningen af udrulningen på løsningsniveau, hvilket drøftes i [fase 2](powerbi-migration-planning.md) af migreringsprocessen.

## <a name="establish-initial-architecture"></a>Fastlæg den indledende arkitektur

Din [arkitektur for BI-løsningen](center-of-excellence-business-intelligence-solution-architecture.md) udvikler sig og modnes over tid. Opgaver til konfiguration af Power BI, som skal håndteres med det samme, omfatter:

- Konfiguration og integration af Power BI-lejer med Azure Active Directory.
- Definer [Power BI-administratorer](../admin/service-admin-role.md).
- Fremskaf og tildel indledende [brugerlicenser](../admin/service-admin-licensing-organization.md).
- Konfigurer og gennemse [indstillinger for Power BI-lejer](admin-tenant-settings.md).
- Konfigurer [arbejdsområderoller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces), og tildel adgang til sikkerhedsgrupper og brugere i Azure Active Directory.
- Konfigurer en indledende [datagateway](../connect-data/service-gateway-deployment-guidance.md)-klynge – med en plan om regelmæssig opdatering.
- Fremskaf en indledende [licens til en Premium-kapacitet](../admin/service-admin-premium-purchase.md) (hvis relevant).
- Konfigurer [arbejdsbelastninger i en Premium-kapacitet](../admin/service-admin-premium-workloads.md) – med en plan om løbende administration.

## <a name="define-success-criteria-for-migration"></a>Definer succeskriterier for migrering

Den første opgave er at forstå, hvordan en vellykket migrering af en enkelt løsning ser ud. Spørgsmål, som du måske vil stille, omfatter:

- **Hvad er den specifikke motivation for og det bestemte formål med denne migrering?** Du kan finde flere oplysninger under [Overblik over migrering til Power BI (Overvej migreringsårsager)](powerbi-migration-overview.md#consider-migration-reasons). Denne artikel indeholder en beskrivelse af de mest almindelige årsager til at migrere til Power BI. Dine mål skal være specificeret på organisationsniveau. Migrering af én tidligere BI-løsning kan drage fordel af markante omkostningsbesparelser, hvorimod fokus kan være på at opnå optimeringsfordele ved migrering af en anden tidligere BI-løsning.
- **Hvad er de forventede omkostninger/fordele eller det forventede investeringsafkast ved denne migrering?** Det kan være nyttigt at have en klar forståelse af, hvilke forventninger der er relateret til omkostningerne, øget funktionalitet, reduceret kompleksitet eller øget fleksibilitet, når succesen skal måles. Det kan give ledende principper for at hjælpe med beslutningsprocessen under migreringen.
- **Hvilke KPI'er bruges til at måle succes?** Følgende liste indeholder nogle eksempler på KPI'er:
    - Antallet af rapporter, der gengives fra den tidligere BI-platform, falder måned efter måned.
    - Antallet af rapporter, der gengives fra Power BI, stiger måned efter måned.
    - Antallet af Power BI-rapportbrugere stiger kvartal efter kvartal.
    - Procentdelen af rapporter, der er migreret til produktion, efter måldato.
    - Reducering af omkostninger for licenser år efter år.

> [!TIP]
> [Power BI-aktivitetsloggen](../admin/service-admin-auditing.md) kan bruges som en kilde til at måle fremskridtet af KPI'erne.

## <a name="prepare-inventory-of-existing-reports"></a>Forbered en oversigt over eksisterende rapporter

Forberedelse af en oversigt over eksisterende rapporter på den tidligere BI-platform er et vigtigt skridt mod at forstå, hvad der allerede findes. Resultatet af dette trin bruges som input til at vurdere indsatsniveauet for migrering. Aktiviteter, der er relateret til forberedelse af en oversigt, kan omfatte:

1. **Oversigt over rapporter:** Udarbejd en liste over rapporter og dashboards, der er kandidater til migrering.
2. **Oversigt over datakilder:** Udarbejd en liste over alle datakilder, som eksisterende rapporter tilgår. Den bør omfatte både datakilder for virksomheden og afdelinger samt personlige datakilder. I forbindelse med denne proces kan der afdækkes datakilder, som it-afdelingen ikke havde kendskab til tidligere, hvilket ofte omtales som _skygge-it_.
3. **Overvågningslog:** Hent data fra overvågningsloggen for den tidligere BI-platform for at forstå forbrugsmønstre og hjælpe med prioriteringen. Vigtige oplysninger, der skal hentes fra overvågningsloggen, omfatter:
    - Det gennemsnitlige antal gange, hver rapport blev udført pr. uge/måned/kvartal.
    - Det gennemsnitlige antal forbrugere pr. rapport pr. uge/måned/kvartal.
    - Forbrugerne af hver rapport, især rapporter der bruges af ledelsen.
    - Den seneste dato, hvor hver rapport blev udført.

> [!NOTE]
> I mange tilfælde migreres indholdet ikke til Power BI præcis, som de er. Migreringen udgør en mulighed for at redesigne dataarkitekturen og/eller forbedre leveringen af rapporten. Udarbejdelse af en oversigt over rapporter er altafgørende for at forstå, hvad der findes i øjeblikket, så du kan begynde at vurdere, hvilken form for omstrukturering der er nødvendig. De resterende artikler i denne serie indeholder en mere detaljeret beskrivelse af forbedringerne.

## <a name="explore-automation-options"></a>Udforsk automatiseringsmulighederne

Det er ikke muligt at automatisere en konverteringsproces til Power BI fuldt ud.

Udarbejdelse af en oversigt over eksisterende data og rapporter kan automatiseres, når du har et eksisterende værktøj, der kan gøre det for dig. Omfanget af automatisering af nogle dele af migreringsprocessen, f.eks. udarbejdelse af en oversigt over eksisterende data, afhænger i høj grad af de værktøjer, du har.

## <a name="next-steps"></a>Næste trin

I den [næste artikel i denne serie om migrering til Power BI](powerbi-migration-requirements.md) får du mere at vide om fase 1, som handler om at indsamle og prioritere krav, når der migreres til Power BI.

Andre nyttige ressourcer omfatter:

- [Microsofts BI-transformation](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Whitepaper om planlægning af en udrulning af Power BI i en virksomhed](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

Der findes erfarne Power BI-partnere, som kan hjælpe din organisation med at gennemføre migreringsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).
