---
title: Udrul til Power BI
description: Vejledning til udrulning, support og overvågning af indhold, når der migreres til Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: bfa3ffad111c7ab819ed1269586a7b32ccf43bba
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419262"
---
# <a name="deploy-to-power-bi"></a>Udrul til Power BI

Denne artikel indeholder en beskrivelse af **fase 5**, som omhandler udrulning, support og overvågning af indhold, når der migreres til Power BI.

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="Billede, der viser faserne i en migrering til Power BI. Der fokuseres på fase 5 i denne artikel.":::

> [!NOTE]
> Du kan finde en komplet forklaring af ovenstående grafik under [Oversigt over migrering til Power BI](powerbi-migration-overview.md).

Det primære fokus i fase 5 er at udrulle den nye Power BI-løsning til produktion.

Outputtet fra denne fase er en produktionsløsning, der er klar til brug i virksomheden. Når du arbejder med en agil metode, er det acceptabelt at have nogle planlagte forbedringer, der leveres i en fremtidig gentagelse. Support og overvågning er både vigtigt i denne fase og løbende.

> [!TIP]
> Med undtagelse af at køre tidligere rapporter parallelt og tage dem ud af drift, hvilket drøftes nedenfor, gælder de emner, der drøftes i denne artikel, også for et Power BI-standardimplementeringsprojekt.

## <a name="deploy-to-test-environment"></a>Udrul i testmiljø

Der findes et generelt testmiljø til it-administrerede løsninger eller løsninger, der er kritiske for virksomhedens produktivitet. Et testmiljø er placeret mellem udvikling og produktion, og det er ikke nødvendigt til alle Power BI-løsninger. Et testarbejdsområde kan fungere som en stabil placering, der er adskilt fra udvikling, til test af brugeraccept, som skal udføres, før der udgives til produktion.

Hvis dit indhold er blevet publiceret i et arbejdsområde i en Premium-kapacitet, kan [udrulningspipelines](../create-reports/deployment-pipelines-overview.md) forenkle udrulningsprocessen for udviklings-, test- og produktionsarbejdsområder. Alternativt kan publiceringen udføres manuelt eller ved hjælp af [PowerShell-scripts](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/).

### <a name="deploy-to-test-workspace"></a>Udrul til testarbejdsområde

Vigtige aktiviteter under en udrulning til testarbejdsområdet omfatter typisk:

- **Forbindelsesstrenge og -parametre:** Tilpas forbindelsesstrenge for datasæt, hvis datakilden varierer mellem udvikling og test. [Parameterisering](../connect-data/service-parameters.md) kan bruges til effektivt at administrere forbindelsesstrenge.
- **Indhold i arbejdsområde:** Publicer datasæt og rapporter i testarbejdsområder, og opret dashboards.
- **App.** Publicer en [app](../consumer/end-user-apps.md) ved hjælp af indholdet fra testarbejdsområdet, hvis det udgør en del af processen til test af brugeraccept. Normalt er apptilladelser begrænset til et mindre antal personer, der er involveret i test af brugeraccept.
- **Opdatering af data:** [Planlæg opdateringen af datasættet](../connect-data/refresh-scheduled-refresh.md) for alle Import-datasæt for perioden, når test af brugeraccept forekommer aktivt.
- **Sikkerhed:** Opdater eller bekræft [arbejdsområderoller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). Test af adgang til arbejdsområdet omfatter et mindre antal personer, der er involveret i test af brugeraccept.

> [!NOTE]
> Du kan finde flere oplysninger om muligheder for udrulning til udvikling, test og produktion i afsnit 9 i [Whitepaper om planlægning af en udrulning af Power BI i en virksomhed](https://aka.ms/PBIEnterpriseDeploymentWP).

### <a name="conduct-user-acceptance-testing"></a>Udfør test af brugeraccept

General omfatter test af brugeraccept virksomhedsbrugere, der er eksperter på området. Efter bekræftelsen godkender de, at det nye indhold er nøjagtigt, at det opfylder kravene, og at det kan udrulles, så andre kan bruge det.

Formalitetsgraden af denne proces for test af brugeraccept, herunder nedskrevne godkendelser, afhænger af din praksis for administration af ændringer.

## <a name="deploy-to-production-environment"></a>Udrul til produktionsmiljø

Der er flere overvejelser i forbindelse med udrulning til produktionsmiljøet.

### <a name="conduct-a-staged-deployment"></a>Udfør en faseinddelt udrulning

Hvis du forsøger at minimere risici og brugerafbrydelser, eller hvis der er andre bekymringer, kan du vælge at udføre en faseinddelt udrulning. Den første udrulning til produktionen kan involvere en mindre gruppe pilotbrugere. Med et pilotprogram kan der aktivt anmodes om feedback fra pilotbrugerne.

Udvid tilladelser i produktionsarbejdsområdet eller appen gradvist, indtil hele målgruppen har tilladelse til den nye Power BI-løsning.

> [!TIP]
> Brug [aktivitetsloggen i Power BI](../admin/service-admin-auditing.md) til at forstå, hvordan forbrugere indfører og bruger den nye Power BI-løsning.

### <a name="handle-additional-components"></a>Håndter yderligere komponenter

Under udrulningsprocessen skal du måske arbejde sammen med dine Power BI-administratorer for at håndtere yderligere krav, der er nødvendige for at yde support til hele løsningen, f.eks.:

- **Vedligeholdelse af gateway:** En [ny datakilde](../connect-data/service-gateway-data-sources.md) skal måske registreres i datagatewayen.
- **Drivere og connectorer til gateway:** En ny privatejet datakilde kræver måske installation af en ny driver eller en brugerdefineret connector på hver server i gatewayklyngen.
- **Opret en ny Premium-kapacitet:** Du kan muligvis bruge en eksisterende [Premium-kapacitet](../admin/service-premium-capacity-manage.md). Eller der kan være situationer, hvor der er behov for en ny Premium-kapacitet. Det kan være tilfældet, når du med vilje ønsker at adskille en arbejdsbelastning i en afdeling.
- **Konfigurer et Power BI-dataflow:** Aktiviteter for dataforberedelse kan konfigureres én gang i et [Power BI-dataflow](../transform-model/dataflows/dataflows-introduction-self-service.md) ved hjælp af Power Query Online. Det hjælper med at forhindre replikering af dataforberedelse i mange forskellige Power BI Desktop-filer.
- **Registrer en ny visualisering til organisationer:** Registrering af [visualiseringer til organisationer](../developer/visuals/power-bi-custom-visuals-organization.md) kan udføres via administrationsportalen for brugerdefinerede visualiseringer, der ikke stammer fra AppSource.
- **Angiv udvalgt indhold:** Der findes en lejerindstilling, som styrer, hvem der kan angive [udvalgt indhold](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/) på startsiden i Power BI-tjenesten.
- **Konfigurer følsomhedsmærkater:** Alle [følsomhedsmærkater](../admin/service-security-data-protection-overview.md) er integreret i Microsoft Information Protection.

### <a name="deploy-to-production-workspace"></a>Udrul til produktionsarbejdsområde

Vigtige aktiviteter under en udrulning til produktionsarbejdsområdet omfatter typisk:

- **Administration af ændringer:** Hvis det er nødvendigt, kan du få godkendelse til at udrulle og formidle udrulningen til brugerpopulationen ved hjælp af din standardpraksis for administration af ændringer. Der kan være et godkendt vindue til administration af ændringer, hvor udrulninger til produktion er tilladt. Normalt anvendes det for it-administreret indhold, og det anvendes meget sjældnere for selvbetjent indhold.
- **Plan for annullering af opdatering:** I forbindelse med migrering forventes det, at det er den første migrering af en ny løsning. Hvis der allerede findes indhold, er det klogt, at have en plan for at vende tilbage til den forrige version, hvis det skulle blive nødvendigt. Til dette formål fungerer det godt, hvis du har tidligere versioner af Power BI Desktop-filerne (ved hjælp af versionsstyring på SharePoint eller OneDrive).
- **Forbindelsesstrenge og -parametre:** Tilpas forbindelsesstrenge for datasættet, når datakilden varierer mellem test og produktion. [Parameterisering](../connect-data/service-parameters.md) kan bruges effektivt til dette formål.
- **Opdatering af data:** [Planlæg opdateringen af datasættet](../connect-data/refresh-scheduled-refresh.md) for alle importerede datasæt.
- **Indhold i arbejdsområde:** Publicer datasæt og rapporter i produktionsarbejdsområdet, og opret dashboards. [Udrulningspipelines](../create-reports/deployment-pipelines-overview.md) kan forenkle processen for udrulning i udviklings-, test- og produktionsarbejdsområder, hvis dit indhold er blevet publiceret til arbejdsområder i en Premium-kapacitet.
- **App:** Hvis apps er en del af din strategi til distribution af indhold, kan du publicere en [app](../consumer/end-user-apps.md) ved hjælp af indholdet fra produktionsarbejdsområdet.
- **Sikkerhed:** Opdater og bekræft [arbejdsområderoller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) baseret på din strategi for distribution af og samarbejde om indhold.
- **Indstillinger for datasæt:** Opdater og bekræft indstillingerne for hvert datasæt, herunder:
  - [Anbefaling](../collaborate-share/service-endorse-content.md) (f.eks. certificeret eller fremhævet)
  - Legitimationsoplysninger til gatewayforbindelse eller datakilde
  - Planlagt opdatering
  - [Udvalgte spørgsmål i Spørgsmål og svar](../create-reports/service-q-and-a-create-featured-questions.md)
- **Indstillinger for rapport og dashboard:** Opdater og bekræft indstillingerne for hver rapport og hvert dashboard. De vigtigste indstillinger omfatter:
  - Beskrivelse
  - Kontakt eller gruppe
  - [Følsomhedsmærkat](../admin/service-security-apply-data-sensitivity-labels.md)
  - [Udvalgt indhold](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **Abonnementer:** Konfigurer rapportabonnementer, om nødvendigt.

> [!IMPORTANT]
> På dette tidspunkt har du nået en stor milepæl. Du kan fejre din bedrift ved at fuldføre migreringen.

### <a name="communicate-with-users"></a>Kommuniker med brugerne

Fortæl forbrugerne om den nye løsning. Giv dem besked om, hvor de kan finde indhold samt tilknyttet dokumentation, ofte stillede spørgsmål og selvstudier. Hvis du vil introducere det nye indhold, kan du overveje at hoste en frokostsession med læring, eller du kan forberede nogle on-demand-videoer.

Sørg for at inkludere instruktioner til, hvordan der anmodes om hjælp eller gives feedback.

### <a name="conduct-a-retrospective"></a>Udfør en evaluering

Overvej at udføre en evaluering for at undersøge, hvad der gik godt under migreringen, og hvad der kunne gøres bedre til den næste migrering.

## <a name="run-in-parallel"></a>Kør parallelt

I mange situationer kører den nye løsning parallelt med den tidligere løsning i en forudbestemt periode. Fordelene ved at køre parallelt omfatter følgende:

- Det reducerer risici, især hvis rapporterne anses for at være missionskritiske.
- Det giver brugerne tid til at vænne sig til den nye Power BI-løsning.
- Det gør det muligt at krydsreferere de oplysninger, der præsenteres i Power BI, med de tidligere rapporter.

## <a name="decommission-the-legacy-report"></a>Udtagelse af den tidligere rapport af drift

På et tidspunkt skal de rapporter, der er migreret til Power BI, deaktiveres på den tidligere BI-platform. Du kan tage tidligere rapporter ud af drift, når:

- Den forudbestemte periode for parallel kørsel, som skal være kommunikeret ud til brugerpopulationen, er udløbet. Det er ofte 30-90 dage.
- Alle brugere af det tidligere system har adgang til den nye Power BI-løsning.
- Der ikke længere er markant aktivitet i den tidligere rapport.
- Der ikke er opstået problemer med den nye Power BI-løsning, som kunne have en indvirkning på brugerproduktiviteten.

## <a name="monitor-the-solution"></a>Overvåg løsningen

Hændelser fra [Power BI-aktivitetsloggen](../admin/service-admin-auditing.md) kan bruges til at forstå forbrugsmønstre i forbindelse med den nye løsning (eller [udførelsesloggen](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view) for indhold, der udrulles i Power BI-rapportserver). Analyse af aktivitetsloggen kan hjælpe med at fastlægge, om den faktiske brug afviger fra forventningerne. Den kan også validere, om der er tilstrækkelig support til løsningen.

Her er nogle spørgsmål, der kan håndteres ved at gennemse aktivitetsloggen:

- Hvor ofte vises indholdet?
- Hvem får vist indholdet?
- Vises indholdet via en app eller et arbejdsområde?
- Anvender de fleste brugere en browser eller en mobilapp?
- Bruges der abonnementer?
- Oprettes der nye rapporter baseret på denne løsning?
- Opdateres indholdet regelmæssigt?
- Hvordan er sikkerheden defineret?
- Opstår der jævnligt problemer, f.eks. fejl under opdatering af data?
- Er der bekymrende aktiviteter (f.eks. markant eksportaktivitet eller adskillige separate delinger af rapporten), hvilket kan betyde, at yderligere træning er påkrævet?

> [!IMPORTANT]
> Sørg for, at der er nogen, som regelmæssigt gennemgår aktivitetsloggen. Det har ingen værdi i forhold til overvågning eller overholdelse af angivne standarder, hvis du blot registrerer den og gemmer historikken. Den virkelige værdi opstår, når der kan udføres proaktiv handling.

## <a name="support-the-solution"></a>Yd support til løsningen

Selvom migreringen er fuldført, er den efterfølgende periode altafgørende for at håndtere problemer og bekymringer om ydeevnen. Med tiden vil den migrerede løsning sandsynligvis gennemgå ændringer, i takt med at virksomhedsbehovene ændres.

Support plejer at foregå lidt anderledes, afhængigt af hvordan selvbetjent BI administreres på tværs af organisationen. Power BI-mestre i hele forretningsenheden fungerer ofte uformelt som den første supportlinje. Selvom det er en uformel rolle, er det en altafgørende rolle, som bør tilskyndes.

Det er også vigtigt at have en formel supportproces, der håndteres af it-medarbejdere via supportanmodninger, for at håndtere rutinemæssige systemorienterede anmodninger og med henblik på eskalering.

Du kan også have et [Center of Excellence (COE)](center-of-excellence-establish.md), der fungerer som interne konsulenter, som yder support til, uddanner og styrer Power BI i organisationen. Et COE kan være ansvarligt for at organisere nyttigt Power BI-indhold på en intern portal.

Til sidst skal det være tydeligt for forbrugere af indhold, hvem de skal kontakte, hvis de har spørgsmål til indholdet, og der skal være en mekanisme til at give feedback om problemer og forbedringer.

## <a name="next-steps"></a>Næste trin

I den [sidste artikel i denne serie](powerbi-migration-learn-from-customers.md) får du mere viden fra kunder, når der migreres til Power BI.

Andre nyttige ressourcer omfatter:

- [Microsofts BI-transformation](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Whitepaper om planlægning af en udrulning af Power BI i en virksomhed](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

Der findes erfarne Power BI-partnere, som kan hjælpe din organisation med at gennemføre migreringsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).