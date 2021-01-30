---
title: Indsaml krav til migrering til Power BI
description: Vejledning i indsamling og prioritering af krav ved migrering til Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 13cac1198010b9cd53d9fd3af2b9575d2f9b3809
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087125"
---
# <a name="gather-requirements-to-migrate-to-power-bi"></a>Indsaml krav til migrering til Power BI

I denne artikel beskrives **fase 1**, der omhandler indsamling og prioritering af krav ved migrering til Power BI.

:::image type="content" source="media/powerbi-migration-requirements/migrate-to-powerbi-stage-1.png" alt-text="Billede, der viser faserne i en migrering til Power BI. Der fokuseres på fase 1 i denne artikel.":::

> [!NOTE]
> Du kan finde en komplet forklaring af ovenstående grafik under [Oversigt over migrering til Power BI](powerbi-migration-overview.md).

I fase 1 fokuseres der på indsamling af oplysninger og planlægning af en individuel løsning, der migreres til Power BI.

Resultatet af fase 1 omfatter detaljerede krav, der prioriteres. Der skal dog udføres yderligere aktiviteter i trin 2 og 3, for at du kan vurdere, hvilken indsats det kræver.

> [!IMPORTANT]
> Fase 1-5 repræsenterer aktiviteter, der er relateret til en bestemt løsning. Der er beslutninger og aktiviteter på organisationsniveau/lejerniveau, som påvirker processen på løsningsniveau. Nogle af disse planlægningsaktiviteter på et højere niveau er beskrevet i artiklen [Oversigt over migrering til Power BI](powerbi-migration-overview.md). Hvis det er relevant, skal beslutninger tages på organisationsniveau for at sikre effektivitet og konsistens.

> [!TIP]
> De fleste af de emner, denne artikel omhandler, gælder også for et Power BI-standardimplementeringsprojekt.

## <a name="compile-requirements"></a>Kompiler krav

Lageret med eksisterende BI-artefakter, der kompileres i [trinnene før migrering](powerbi-migration-pre-migration-steps.md), bliver input til kravene til den nye løsning, der skal oprettes i Power BI. Indsamling af krav handler om at forstå den aktuelle tilstand, og hvilke elementer brugerne ønsker at få ændret eller omlagt, når rapporter skal have et nyt design i Power BI. Detaljerede krav er nyttige i forbindelse med planlægning af udrulning i [fase 2](powerbi-migration-planning.md)under udarbejdelse af blåstempling i [fase 3](powerbi-migration-proof-of-concept.md), og når du opretter den produktionsklare løsning i [trin 4](powerbi-migration-create-validate-content.md).

### <a name="gather-report-requirements"></a>Indsaml rapportkrav

Kompiler grundige og letlæselige oplysninger om rapporter, f. eks.:

- **Formål, målgruppe og forventet handling:** Identificer det formål og den forretningsproces, der gælder for hver rapport, samt målgruppen, den analytiske arbejdsproces og den forventede handling, der skal udføres af rapportens forbrugere.
- **Den måde forbrugerne bruger rapporten på:** Overvej at iagttage forbrugere af den eksisterende rapport for at forstå, præcis hvordan de bruger den. Du finder måske ud af, at visse elementer i rapporten kan fjernes eller forbedres i den nye Power BI-version. Denne proces omfatter en ekstra tidsinvestering, men den er værdifuld for kritiske rapporter eller rapporter, der bruges ofte.
- **Ejer og ekspert inden for emnet:** Identificer rapport ejeren og eventuelle eksperter inden for emnet, der er knyttet til rapporten eller datadomænet. De kan fremover blive ejerne af den nye Power BI-rapport. Medtag eventuelle specifikke krav til ændringsstyring (som typisk er forskellige for henholdsvis it-administrerede og virksomhedsadministrerede løsninger) samt godkendelser, der er nødvendige, når der foretages ændringer fremover.
- **Metode til levering af indhold:** Tydeliggør rapportforbrugernes forventninger til levering af indhold. Det kan være levering i form af interaktiv udførelse efter behov, levering, der er integreret i et brugerdefineret program, eller levering efter en tidsplan ved hjælp af et mailabonnement. Der kan også være krav til udløsning af beskeder.
- **Behov i forbindelse med interaktivitet:** Fastlæg krav til _skal have_- og _godt at have_-interaktivitet, f. eks. filtre, detailudledning eller detailadgang.
- **Datakilder:** Sørg for, at alle datakilder, der kræves af rapporten, er fundet, og at behov i forbindelse med dataventetid (dataopdatering) er forstået. Identificer krav til historiske data, tendenser og datasnapshot for hver rapport, så de kan justeres i forhold til datakravene. Dokumentation af datakilden kan også være nyttig på et senere tidspunkt, når du udfører datavalidering af en ny rapport med dens kildedata.
- **Sikkerhedskrav:** Tydeliggør sikkerhedskrav (f. eks. tilladte læsere, tilladte redaktører og eventuelle krav til sikkerhed på rækkeniveau), herunder eventuelle undtagelser i forhold til normal organisationssikkerhed. Dokumenter et niveau for datafølsomhed, beskyttelse af personlige oplysninger og/eller lovmæssige krav.
- **Beregninger, KPI'er og forretningsregler:** Identificer og dokumenter alle beregninger, KPI'er og forretningsregler, der i øjeblikket er defineret i den eksisterende rapport, så de kan justeres i forhold til datakravene.
- **Krav til anvendelighed, layout og udseende:** Identificer de specifikke behov i forbindelse med krav til anvendelighed, layout og udseende, der er relateret til datavisualiseringer, gruppering, sortering og betinget synlighed. Medtag eventuelle specifikke overvejelser, der er relateret til levering til mobilenheder.
- **Behov for udskrivning og eksport:** Find ud af, om der er krav, der er specifikke for udskrivning, eksport eller et pixel – perfekt layout. Disse behov påvirker, hvilke typer rapporter der er mest passende (f. eks. en Power BI- eller Excel-rapport eller en sideinddelt rapport). Vær opmærksom på, at brugerne har tendens til at lægge stor vægt på, hvordan de altid har gjort tingene, så være ikke bange for at udfordre deres måde at tænke på. Husk at fokusere på _forbedringer_ i stedet for _ændringer_.
- **Risici eller overvejelser:** Find ud af, om der er andre tekniske eller funktionelle krav til rapporter samt eventuelle risici eller overvejelser vedrørende de oplysninger, der præsenteres i dem.
- **Åbne problemer og ventende opgaver:** Identificer eventuel fremtidig vedligeholdelse, kendte problemer eller udskudte anmodninger for at føje dem til rækken af aktuelt ventende opgaver.

> [!TIP]
> Overvej krav til rangering ved at klassificere dem som _skal have_ eller _godt at have_. Ofte beder kunderne om alt det, de muligvis har brug for, på forhånd, fordi de tror, at det er deres eneste chance for at foretage anmodninger. Når du har adresseret prioriteter i flere gentagelser, kan du også gøre rækken af ventende problemer tilgængelig for interessenter. Det hjælper med kommunikation, beslutningstagning og sporing af ventende forpligtelser.

### <a name="gather-data-requirements"></a>Indsaml datakrav

Kompiler detaljerede oplysninger vedrørende data, f. eks.:

- **Eksisterende forespørgsler:** Identificer, om der findes eksisterende rapportforespørgsler eller lagrede procedurer, der kan bruges af en [DirectQuery-model](../connect-data/desktop-use-directquery.md) eller en [sammensat model](../transform-model/desktop-composite-models.md) eller kan konverteres til en importmodel.
- **Typer af datakilder:** Kompiler de typer af datakilder, der er nødvendige, herunder centraliserede datakilder (f. eks. en virksomheds data warehouse) samt ikke-standard-datakilder (f. eks. flade filer eller Excel-filer, der klargør virksomhedens datakilder til rapporteringsformål). Det er også vigtigt at finde ud af, hvor datakilder er placeret af hensyn til [datagatewayens](../connect-data/service-gateway-onprem.md) netværksmulighed.
- **Behov i forbindelse med datastruktur og rensning:** Fastlæg datastrukturen for hver af de nødvendige datakilder, og i hvilket omfang [datarensnings](../transform-model/desktop-query-overview.md)aktiviteter er nødvendige.
- **Dataintegration:** Vurder, hvordan dataintegration håndteres, når der er flere datakilder, og hvordan [relationer](../transform-model/desktop-create-and-manage-relationships.md) kan defineres mellem de enkelte modeltabeller. Identificer bestemte dataelementer, der er nødvendige for at forenkle modellen og [reducere dens størrelse](import-modeling-data-reduction.md).
- **Acceptabel dataventetid:** Fastlæg behovene i forbindelse med dataventetid for hver datakilde. Det påvirker beslutningerne om, hvilken [datalagringstilstand](../transform-model/desktop-storage-mode.md) der skal bruges. Det er også vigtigt at kende dataopdateringshyppigheden for importmodeltabeller.
- **Datamængde og -skalerbarhed:** Evaluer forventninger til datamængden, som vil indgå i beslutninger om [understøttelse af store modeller](../admin/service-premium-large-models.md) og design af DirectQuery-modeller eller [sammensatte modeller](../transform-model/desktop-composite-models.md). Overvejelser, der er relateret til behov for historiske data, er også vigtige. I forbindelse med større datasæt er det også nødvendigt at fastsætte regler for [trinvis opdatering af data](../admin/service-premium-incremental-refresh.md).
- **Målinger, KPI'er og forretningsregler:** Vurder behovene for målinger, KPI'er og forretningsregler. De påvirker beslutninger om, hvor logikken skal bruges: i datasættet eller i dataintegrationsprocessen.
- **Masterdata og datakatalog:** Overvej, om der er problemer med masterdata, der kræver opmærksomhed. Find ud af, om integration med et virksomhedsdatakatalog gør dataene nemmere at finde og letter adgangen til definitioner eller opretter ensartet terminologi, der accepteres af organisationen.
- **Sikkerhed og beskyttelse af personlige oplysninger:** Find ud af, om der er specifikke overvejelser vedrørende sikkerhed eller beskyttelse af personlige oplysninger for datasæt, herunder krav til [sikkerhed på rækkeniveau](../admin/service-admin-rls.md).
- **Åbne problemer og ventende opgaver:** Tilføj eventuelle kendte problemer, kendte problemer med datakvaliteten, fremtidig vedligeholdelse eller udskudte anmodninger på dette tidspunkt.

> [!IMPORTANT]
> Genbrug af data kan opnås ved hjælp af [delte datasæt](../connect-data/service-datasets-share.md), der eventuelt kan [certificeres](../collaborate-share/service-endorse-content.md) for at angive troværdighed og gøre dem nemmere at finde. Genbrug af dataklargøring kan opnås ved hjælp af [dataflow](../transform-model/dataflows/dataflows-introduction-self-service.md), der reducerer gentagen logik i flere datasæt. Dataflows kan også reducere belastningen på kildesystemer væsentligt, da dataene hentes mindre hyppigt – flere datasæt kan derefter importere data fra dataflowet.

## <a name="identify-improvement-opportunities"></a>Identificer muligheder for forbedring

I de fleste situationer sker der nogle ændringer og forbedringer. Det er sjældent, at en direkte en til en-migrering finder sted uden omstrukturering eller forbedring. Du kan overveje følgende tre typer forbedringer:

- **Konsolidering af rapporter:** Lignende rapporter kan konsolideres ved hjælp af teknikker som filtre, bogmærker eller tilpasning. Hvis du har færre rapporter, der hver især er mere fleksible, kan det betyde en væsentlig forbedring af oplevelsen for rapportforbrugere. Overvej at optimere datasæt for [Spørgsmål og svar (forespørgsler på naturligt sprog)](../natural-language/q-and-a-best-practices.md) for at give rapportforbrugerne endnu større fleksibilitet, så de kan oprette deres egne visualiseringer.
- **Forbedringer af effektiviteten:** Der identificeres ofte forbedringer under indsamling af krav. Det kan f. eks. være, når analytikere kompilerer tal manuelt, eller når en arbejdsproces kan strømlines. [Power Query](../transform-model/desktop-query-overview.md) kan spille en stor rolle for den erstatning af manuelle aktiviteter, der aktuelt udføres. Hvis forretningsanalytikere jævnligt udfører de samme aktiviteter igen og igen for at rense og klargøre data, kan Power Query-dataklargøringstrin, der kan gentages, give dig betydelige tidsbesparelser og reducere antallet af fejl.
- **Centralisering af datamodel:** Et autoritativt og certificeret datasæt fungerer som grundstenen for administreret selvbetjenings-BI. I dette tilfælde administreres dataene én gang, og analytikere har fleksibilitet til at bruge og klargøre disse data for at imødekomme deres behov for rapportering og analyse.

> [!NOTE]
> Hvis du vil vide mere om centralisering af datamodeller, kan du læse mere under [Disciplin centralt](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) og [Fleksibilitet hele vejen rundt](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="prioritize-and-assess-complexity"></a>Prioriter og vurder kompleksiteten

På dette tidspunkt er det oprindelige lager tilgængeligt og kan indeholde specifikke krav. Når du prioriterer de første sæt BI-artefakter, der er klar til migrering, skal rapporter og data både overvejes samlet og uafhængigt af hinanden.

Identificer rapporter med høj prioritet, der kan omfatte rapporter, der har følgende kendetegn:

- Tilføjer virksomheden en vigtig værdi.
- Udføres ofte.
- Kræves af ledende leder eller direktører.
- Omfatter et rimeligt niveau af kompleksitet (for at forbedre succespotentialet under de indledende migreringsgentagelser).

Identificer data med høj prioritet, som kan indeholde data, der har følgende kendetegn:

- Indeholder vigtige dataelementer.
- Er almindelige organisationsdata, der bruges i mange use cases.
- Kan bruges til at oprette et delt datasæt, som kan genbruges i rapporter og af mange rapportforfattere.
- Omfatter et rimeligt kompleksitetsniveau (for at forbedre succespotentialet under de indledende migreringsgentagelser).

## <a name="next-steps"></a>Næste trin

I [næste artikel i denne serie om migrering til Power BI](powerbi-migration-planning.md) kan du få mere at vide om fase 2, der omhandler planlægning af migrering for en enkelt Power BI-løsning.

Andre nyttige ressourcer omfatter:

- [Microsofts BI-transformation](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Hvidbog om planlægning af en Power BI Enterprise-installation](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

Der findes erfarne Power BI-partnere, som kan hjælpe din organisation med at gennemføre migreringsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).