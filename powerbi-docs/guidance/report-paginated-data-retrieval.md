---
title: Vejledning til datahentning for sideinddelte rapporter
description: Vejledning til oprettelse af datakilder og datasæt for sideinddelte rapporter i Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/16/2020
ms.openlocfilehash: c29e4dfa97b91cb16fc76d095ce05a04b906ee7f
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088091"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Vejledning til datahentning for sideinddelte rapporter

Denne artikel henvender sig til rapportforfattere, der designer [sideinddelte rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md) i Power BI. Den indeholder anbefalinger, der kan hjælpe dig med at designe effektiv hentning af data.

## <a name="data-source-types"></a>Datakildetyper

Sideinddelte rapporter understøtter som standard både relationsdatakilder og analysedatakilder. Disse kilder er yderligere kategoriseret som enten cloudbaserede eller fra det lokale miljø. Datakilder i det lokale miljø – uanset om de er hostet i det lokale miljø eller på en virtuel maskine – kræver en datagateway, så Power BI kan oprette forbindelse. Cloudbaseret betyder, at Power BI kan oprette forbindelse direkte ved hjælp af en internetforbindelse.

Hvis du kan vælge datakildetypen (muligvis i et nyt projekt), anbefaler vi, at du bruger cloudbaserede datakilder. Sideinddelte rapporter kan oprette forbindelse til netværk med lavere ventetid, især når datakilderne er placeret i samme område som din Power BI-lejer. Det er også muligt at oprette forbindelse til disse kilder ved hjælp af enkeltlogon (SSO). Det betyder, at rapportbrugerens identitet kan flyde til datakilden, hvilket gør det muligt at gennemtvinge tilladelser på rækkeniveau pr. bruger. I øjeblikket understøttes SSO for datakilder i det lokale miljø ikke (dvs. SQL Server Analysis Services kan ikke gennemtvinge tilladelser på rækkeniveau pr. bruger).

> [!NOTE]
> Selvom det i øjeblikket ikke er muligt at oprette forbindelse til databaser i det lokale miljø ved hjælp af SSO, kan du stadig gennemtvinge tilladelser på rækkeniveau. Det gøres ved at overføre det integrerede felt **UserID** til en parameter for en datasætforespørgsel. Datakilden skal gemme UPN-værdier (User Principal Name) på en måde, så forespørgselsresultaterne kan blive korrekt filtreret.
>
> Du kan f.eks. overveje at gemme hver enkelt sælger som en række i tabellen **Sælger**.  Tabellen indeholder kolonner til UPN og også sælgerens salgsområde. På forespørgselstidspunktet filtreres tabellen efter UPN for rapportbrugeren, og den er også relateret til salgsfakta ved hjælp af en indre joinforbindelse. På den måde filtrerer forespørgslen rækker med salgsfakta effektivt til dem i rapportbrugerens salgsområde.

### <a name="relational-data-sources"></a>Relationelle datakilder

Relationelle datakilder er generelt også velegnede til driftsmæssige rapporter som f.eks. salgsfakturaer. De er også egnet til rapporter, der skal hente meget store datasæt (over 10.000 rækker). Relationelle datakilder kan også definere lagrede procedurer, som kan udføres af rapportdatasæt. Lagrede procedurer giver flere fordele:

- Parameterisering
- Indkapsling af programmeringslogik, der giver mulighed for mere komplekse dataforberedelser (f.eks. midlertidige tabeller, markører eller brugerdefinerede skalarfunktioner).
- Forbedret vedligeholdelse, så lagret procedurelogik nemt kan opdateres. I nogle tilfælde kan det gøres uden at ændre sideinddelte rapporter og publicere dem igen (hvis kolonnenavne og datatyper forbliver uændrede).
- Bedre ydeevne, da deres udførelsesplaner cachelagres til genbrug.
- Genbrug af lagrede procedurer på tværs af flere rapporter.

I Power BI Report Builder kan du bruge den relationelle forespørgselsdesigner til at konstruere en forespørgselssætning grafisk, men kun for Microsoft-datakilder.

### <a name="analytic-data-sources"></a>Analysedatakilder

Analysedatakilder er velegnede til både driftsmæssige rapporter og analyserapporter og kan levere hurtige opsummerede forespørgselsresultater selv for meget store datamængder. Modelmålinger og KPI'er kan indkapsle komplekse forretningsregler for at opnå en opsummering af data. Disse datakilder er dog ikke egnet til rapporter, der skal hente meget store datasæt (over 10.000 rækker).

I Power BI Report Builder kan du vælge mellem to forespørgselsdesignere: Analysis Services DAX-forespørgselsdesigneren og Analysis Services MDX-forespørgselsdesigneren. Disse designere kan bruges til datakilder til Power BI-datasæt eller en SQL Server Analysis Services- eller Azure Analysis Services-model, både tabelbaserede og flerdimensionelle.

Vi anbefaler, at du bruger DAX-forespørgselsdesigneren, hvis den fuldstændig opfylder dine behov i forbindelse med forespørgsler. Hvis modellen ikke definerer de metoder, du har brug for, skal du skifte til forespørgselstilstand. I denne tilstand kan du tilpasse forespørgselssætningen ved at tilføje udtryk (for at opnå opsummering).

MDX-forespørgselsdesigneren kræver, at din model indeholder målinger. Designeren har to egenskaber, der ikke understøttes af DAX-forespørgselsdesigneren. Det giver dig især mulighed for at:

- Definere beregnede medlemmer på forespørgselsniveau (i MDX).
- Konfigurere dataområder for at anmode om [serversammenlægninger](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) i ikke-detaljerede grupper. Hvis du skal præsentere oversigter over semi- eller ikke-additive målinger (f.eks. Time Intelligence-beregninger eller særskilte optællinger) i din rapport, er det sandsynligvis mere effektivt at bruge serversamlinger end at hente detaljerækker på lavt niveau og have rapporten til at beregne opsummeringer.

## <a name="query-result-size"></a>Størrelse på forespørgselsresultat

Generelt er det bedst kun at hente de data, der kræves af din rapport. Undgå derfor at hente kolonner eller rækker, der ikke er nødvendige i rapporten.

Hvis du vil begrænse rækker, skal du altid anvende de mest restriktive filtre og definere samlede forespørgsler. Saml forespørgselsgrupper og opsummer kildedata for at hente resultater med højere detaljegrad. Du kan f.eks. overveje, at rapporten skal vise en oversigt over sælgers salg. Du kan i stedet for at hente alle salgsordrerækker oprette en datasætforespørgsel, der grupperer efter sælger, og som opsummerer salg for hver gruppe.

## <a name="expression-based-fields"></a>Udtryksbaserede felter

Det er muligt at udvide et rapportdatasæt med felter, der er baseret på udtryk. Hvis dit datasæt f.eks. henter kunders fornavn og efternavn, vil du måske have et felt, der sammenkæder de to felter for at oprette kundens fulde navn. Du har to muligheder for at opnå denne beregning. Du kan:

- Oprette et _beregnet felt_, som er et datasætfelt, der er baseret på et udtryk.
- Indsætte et udtryk direkte i datasætforespørgslen (ved hjælp af det oprindelige sprog for din datakilde), hvilket resulterer i et regulært datasætfelt.

Vi anbefaler den sidstnævnte mulighed, når det er muligt. Der er to gode grunde til, at det er bedst at indsætte udtryk direkte i forespørgselsdatasættet:

- Det er muligt, at datakilden er optimeret til at evaluere udtrykket mere effektivt end Power BI (det er især tilfældet for relationelle databaser).
- Rapportens ydeevne forbedres, fordi der ikke er behov for, at Power BI materialiserer beregnede felter før rapportgengivelsen. Beregnede felter kan mærkbart forlænge rapportens gengivelsestid, når datasæt henter et stort antal rækker.

## <a name="field-names"></a>Feltnavne

Når du opretter et datasæt, navngives dets felter automatisk efter forespørgslens kolonner. Det er muligt, at disse navne hverken er brugervenlige eller intuitive. Det er også muligt, at kolonnenavne i kildeforespørgslen indeholder tegn, der ikke er tilladt i RDL-objekt-id'er (Report Definition Language), f.eks. mellemrum og symboler. I dette tilfælde erstattes de forbudte tegn med et understregningstegn (_).

Vi anbefaler, at du først bekræfter, at alle feltnavne er brugervenlige, præcise og meningsfulde. Hvis det ikke er tilfældet, foreslår vi, at du omdøber dem, _før_ du begynder rapportlayoutet. Det skyldes, at omdøbte felter ikke replikeres i de udtryk, der bruges i rapportlayoutet. Hvis du beslutter at omdøbe felter, efter at du har påbegyndt rapportlayoutet, skal du finde og opdatere alle brudte udtryk.

## <a name="filter-vs-parameter"></a>Filter vs. parameter

Det er sandsynligt, at dine design af sideinddelte rapporter indeholder rapportparametre. Rapportparametre bruges normalt til at bede din rapportbruger om at filtrere rapporten. Du har som forfatter til en sideinddelt rapport to måder at opnå rapportfiltrering på. Du kan knytte en rapportparameter til:

- Et _datasætfilter_, hvor værdierne for rapportparameteren bruges til at filtrere de data, der allerede er hentet af datasættet.
- En _datasætparameter_, hvor værdierne for rapportparameteren indsættes i den oprindelige forespørgsel, der blev sendt til datakilden.

> [!NOTE]
> Alle rapportdatasæt cachelagres pr. _session_ i op til 10 minutter _efter deres seneste brug_. Et datasæt kan genbruges, når der sendes nye parameterværdier (filtrering), når rapporten gengives i et andet format, eller når der interageres med rapportdesignet på en eller anden måde, f.eks. ved at slå synlighed til og fra eller gennem sortering.

Overvej derefter et eksempel på en salgsrapport, der har en enkelt rapportparameter for at filtrere rapporten efter et enkelt år. Datasættet henter salg for _alle år_. Det sker, fordi rapportparameteren er knyttet til filtre for datasættet. Rapporten viser data for det ønskede år, som er et undersæt af data for datasættet. Når rapportbrugeren ændrer rapportparameteren til et andet år og derefter får vist rapporten, er Power BI ikke nødt til at hente nogen kildedata. Der anvendes i stedet et andet filter på datasættet, der allerede er cachelagret. Når datasættet er cachelagret, kan filtreringen foregå meget hurtigt.

Overvej nu et andet rapportdesign. Denne gang knytter rapportdesignet rapportparameteren for salgsår til en datasætparameter. På denne måde indsætter Power BI værdien for år i den oprindelige forespørgsel, og datasættet henter kun data for det pågældende år. Hver gang rapportens bruger ændrer værdien for rapportparameteren for år og derefter får vist rapporten, henter datasættet et nyt forespørgselsresultat for det pågældende år.

Begge designmetoder kan filtrere rapportdata, og begge design kan fungere godt i dine rapportdesign. Et optimeret design er dog afhængigt af de forventede datamængder, dataenes omskiftelighed og rapportbrugernes forventede adfærd.

Vi anbefaler _filtrering af datasæt_, når du forventer, at et andet undersæt af datasættets rækker genbruges mange gange (derved gemmes gengivelsestidspunktet, da det ikke er nødvendigt at hente nye data). I dette scenarie kan du se, at det godt kan betale sig at hente et stort datasæt, i forhold til hvor mange gange det genbruges. Det er derfor nyttigt i forbindelse med forespørgsler, der er tidskrævende at generere. Men vær opmærksom på, at cachelagring af store datasæt pr. bruger kan have en negativ indvirkning på ydeevnen og kapacitetsgennemløbet.

Vi anbefaler _datasætparameterisering_, når du forventer, at det er usandsynligt, at der anmodes om et andet undersæt af datasættets rækker, eller når antallet af datasætrækker, der skal filtreres, sandsynligvis vil være meget stort (og ikke effektivt at cachelagre). Denne designmetode fungerer også, når dit datalager er flygtigt. I dette tilfælde vil alle ændringer af rapportparameterværdier medføre, at der hentes opdaterede data.

## <a name="non-native-data-sources"></a>Ikke-oprindelige datakilder

Hvis du har brug for at udvikle sideinddelte rapporter baseret på datakilder, der ikke [oprindeligt understøttes af sideinddelte rapporter](../paginated-reports/paginated-reports-data-sources.md), kan du starte med at udvikle en Power BI Desktop-datamodel. På den måde kan du oprette forbindelse til mere end 100 [Power BI-datakilder](../connect-data/power-bi-data-sources.md). Når du har publiceret til Power BI-tjenesten, kan du derefter udvikle en sideinddelt rapport, der opretter forbindelse til Power BI-datasættet.

## <a name="data-integration"></a>Dataintegration

Hvis du har brug for at kombinere data fra flere datakilder, har du to muligheder:

- **Kombiner rapportdatasæt**: Hvis datakilderne [oprindeligt understøttes af sideinddelte rapporter](../paginated-reports/paginated-reports-data-sources.md), kan du overveje at oprette beregnede felter, der bruger Report Builder-funktionerne [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) eller [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function).
- **Udvikl en Power BI Desktop-model**: Det er dog mere effektivt, hvis du udvikler en datamodel i Power BI Desktop. Du kan bruge Power-forespørgsel til at kombinere forespørgsler, der er baseret på en [vilkårlig understøttet datakilde](../connect-data/power-bi-data-sources.md). Når du har publiceret til Power BI-tjenesten, kan du derefter udvikle en sideinddelt rapport, der opretter forbindelse til Power BI-datasættet.

## <a name="sql-server-complex-data-types"></a>Komplekse datatyper i SQL Server

Eftersom SQL Server er en datakilde i det lokale miljø, skal Power BI oprette forbindelse via en gateway. Gatewayen understøtter dog ikke hentning af data til komplekse datatyper. Komplekse datatyper omfatter indbyggede typer, f.eks. [afstandsdatatyperne](/sql/relational-databases/spatial/spatial-data-sql-server) GEOMETRY og GEOGRAPHY og [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). De kan også inkludere brugerdefinerede typer, der er implementeret via en assembly class i Microsoft.NET Framework CLR (Common Language Runtime).

Afbildning af afstandsdata og analyser i kortvisualiseringen kræver SQL Server-afstandsdata. Det er derfor ikke muligt at arbejde med kortvisualiseringen, når SQL Server er din datakilde. Det vil fungere, hvis din datakilde er Azure SQL Database, fordi Power BI ikke opretter forbindelse via en gateway.

## <a name="data-related-images"></a>Datarelaterede billeder

Billeder kan bruges til at føje logoer eller billeder til dit rapportlayout. Når billeder relaterer til de rækker, der hentes af et rapportdatasæt, har du to muligheder:

- Det er muligt, at billeddata også kan hentes fra din datakilde (hvis de allerede er gemt i en tabel).
- Når billederne er gemt på en webserver, kan du bruge et dynamisk udtryk til at oprette URL-stien til billedet.

Du kan finde flere oplysninger og forslag under [Vejledning i billeder til sideinddelte rapporter](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Redundant hentning af data

Det er muligt, at rapporten henter redundante data. Dette kan ske, når du sletter forespørgselsfelter i datasættet, eller hvis rapporten indeholder ubenyttede datasæt. Du bør undgå disse situationer, da de medfører unødvendig belastning af dine datakilder, netværket og Power BI-kapacitetens ressourcer.

### <a name="deleted-query-fields"></a>Slettede forespørgselsfelter

På siden **Felter** i ruden **Egenskaber for datasæt** kan du slette datasættet _forespørgselsfelter_ (forespørgselsfelter knyttes til kolonner, der hentes af datasætforespørgslen). Report Builder fjerner dog ikke tilsvarende kolonner fra datasætforespørgslen.

Hvis du har brug for at slette forespørgselsfelter fra dit datasæt, anbefaler vi, at du fjerner de tilsvarende kolonner fra datasætforespørgslen. Report Builder fjerner automatisk alle redundante forespørgselsfelter. Hvis du har brug for at slette forespørgselsfelter, skal du også sørge for at ændre sætningen for datasætforespørgslen for at fjerne kolonnerne.

### <a name="unused-datasets"></a>Ubrugte datasæt

Når en rapport køres, evalueres alle datasæt – også selvom de ikke er knyttet til rapportobjekter. Derfor skal du sørge for at fjerne alle test- eller udviklingsdatasæt, før du publicerer en rapport.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Understøttede datakilder for sideinddelte rapporter i Power BI](../paginated-reports/paginated-reports-data-sources.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
