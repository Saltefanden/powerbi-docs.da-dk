---
title: Sikkerhed på rækkeniveau (RLS) med Power BI Desktop
description: Vejledning til gennemtvingelse af sikkerhed på rækkeniveau (RLS) i dine datamodeller med Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: v-pemyer
ms.openlocfilehash: 644e4499a335f18febadf33c371bd15e01499701
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349615"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Sikkerhed på rækkeniveau (RLS) i Power BI Desktop

Denne artikel henvender sig til designere af datamodeller, der arbejder med Power BI Desktop. Den beskriver god designpraksis for at gennemtvingelse af sikkerhed på rækkeniveau (RLS) i dine datamodeller.

Det er vigtigt at forstå RLS-filtres _tabelrækker_ . De kan ikke konfigureres til at begrænse adgangen til modelobjekter, herunder tabeller, kolonner og målinger.

> [!NOTE]
> Denne artikel beskriver ikke RLS, eller hvordan du konfigurerer det. Du kan finde flere oplysninger under [Begræns dataadgang med sikkerhed på rækkeniveau (RLS) for Power BI Desktop](../create-reports/desktop-rls.md).
>
> Den beskriver heller ikke gennemtvingelse af RLS i direkte forbindelser til eksterne modeller med Azure Analysis Services eller SQL Server Analysis Services. I disse tilfælde gennemtvinges RLS af Analysis Services. Når Power BI opretter forbindelse ved hjælp af enkeltlogon (SSO), gennemtvinger Analysis Services RLS (medmindre kontoen har administratorrettigheder).

## <a name="create-roles"></a>Opret roller

Det er muligt at oprette flere roller. Når du overvejer tilladelsesbehovene for en enkelt rapportbruger, skal du stræbe på at oprette en enkelt rolle, der giver alle disse tilladelser i stedet for et design, hvor en rapportbruger er medlem af flere roller. Det skyldes, at en rapportbruger kan tilknytte flere roller, enten direkte ved hjælp af deres brugerkonto eller indirekte via medlemskab af sikkerhedsgrupper. Flere rolletilknytninger kan resultere i uventede resultater.

Når en rapportbruger tildeles til flere roller, bliver RLS-filtre additive. Det betyder, at rapportbrugere kan se tabelrækker, der repræsenterer foreningen af disse filtre. I nogle scenarier er det desuden ikke muligt at garantere, at en rapportbruger ikke kan se rækker i en tabel. I modsætning til tilladelser, der anvendes på SQL Server-databaseobjekter (og andre tilladelsesmodeller), kan du derfor ikke anvende princippet "én gang afvist altid afvist".

Forestil dig en model med to roller: Den første rolle med navnet **Arbejdere** begrænser adgangen til alle rækker i tabellen **Løn** ved hjælp af følgende regeludtryk:

```dax
FALSE()
```

> [!NOTE]
> En regel returnerer ingen tabelrækker, når udtrykket evalueres til **falsk** .

Men en anden rolle med navnet **Ledere** giver adgang til alle rækker i tabellen **Løn** ved hjælp af følgende regeludtryk:

```dax
TRUE()
```

Vær forsigtig: Hvis en rapportbruger vil tilknytte begge roller, vil de se alle tabelrækkerne for **løn** .

## <a name="optimize-rls"></a>Optimer RLS

RLS fungerer ved automatisk at anvende filtre på alle DAX-forespørgsler, og disse filtre kan have en negativ indvirkning på forespørgslers ydeevne. Det betyder, at effektiv RLS kan reduceres til et godt modeldesign. Det er vigtigt at følge vejledningen til modeldesign, som beskrevet i følgende artikler:

- [Forstå, hvad et stjerneskema er, og hvorfor det er vigtigt for Power BI](star-schema.md)
- Alle artikler om relationsvejledning i [Dokumentation med Power BI-vejledning](./index.yml)

Generelt er det ofte mere effektivt at gennemtvinge RLS-filtre i dimensionstype tabeller og ikke faktatypetabeller. Og anvende veldesignede relationer for at sikre, at RLS-filtre overføres til andre modeltabeller. Undgå derfor at bruge DAX-funktionen [LOOKUPVALUE](/dax/lookupvalue-function-dax), når du kan opnå det samme resultat med modelrelationer.

Når RLS-filtre gennemtvinges på DirectQuery-tabeller, og der er relationer til andre DirectQuery-tabeller, skal du sørge for at optimere kildedatabasen. Det kan involvere design af relevante indekser eller brug af permanente beregnede kolonner. Du kan finde flere oplysninger under [Vejledning til DirectQuery-model i Power BI Desktop](directquery-model-guidance.md).

### <a name="measure-rls-impact"></a>Mål RLS-effekten

Det er muligt at måle RLS-filtres effekt på ydeevnen i Power BI Desktop ved hjælp af [Effektivitetsanalyse](../create-reports/desktop-performance-analyzer.md). Først skal du bestemme varighederne af rapporternes visualforespørgsel, når RLS ikke gennemtvinges. Brug derefter kommandoen **Vis som** under båndfanen **Modellering** til at gennemtvinge RLS og fastlægge og sammenligne forespørgselsvarigheder.

## <a name="configure-role-mappings"></a>Konfigurer rolletilknytninger

Efter publicering i Power BI skal du knytte medlemmer til datasætroller. Det er kun ejere af datasæt eller administratorer af arbejdsområder, der kan føje medlemmer til roller. Du kan finde flere oplysninger under [Sikkerhed på rækkeniveau (RLS) med Power BI Desktop (Administrer sikkerheden for din model)](../admin/service-admin-rls.md#manage-security-on-your-model).

Medlemmer kan være brugerkonti eller sikkerhedsgrupper. Når det er muligt, anbefaler vi, at du knytter sikkerhedsgrupper til datasætrollerne. Det involverer administration af medlemskaber af sikkerhedsgrupper i Azure Active Directory. Muligvis delegeres opgaven til dine netværksadministratorer.

## <a name="validate-roles"></a>Valider roller

Test de enkelte roller for at sikre, at de filtreres korrekt i modellen. Det gøres nemt ved hjælp af kommandoen **Vis som** under båndfanen **Modellering** .

Når modellen har dynamiske regler, der bruger DAX-funktionen [USERNAME](/dax/username-function-dax), skal du sørge for at teste, om de forventede værdier er der, og om der er _og uventede_ værdier. Når du integrerer Power BI-indhold – især ved hjælp af scenariet [Appen ejer data](../developer/embedded/embedding.md#embedding-for-your-customers) – kan applogik videresende en hvilken som helst værdi som et effektivt identitetsbrugernavn. Når det er muligt, kan du sikre, at utilsigtede eller skadelige værdier resulterer i filtre, der ikke returnerer nogen rækker.

Forestil dig et eksempel med Power BI Embedded, hvor appen overfører brugerens jobfunktion som det effektive brugernavn: Det er enten "Leder" eller "Medarbejder". Ledere kan se alle rækker, men medarbejdere kan kun se rækker, hvor kolonneværdien **Type** "Intern".

Følgende regeludtryk er defineret:

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

Problemet med dette regeludtryk er, at alle værdier undtagen "Medarbejder" returnerer _alle tabelrækker_ . Derfor returnerer en utilsigtet værdi som "Mdarbejder" ved en fejl alle tabelrækker. Det betyder, at det er mere sikkert at skrive et udtryk, der tester, om alle de forventede værdier findes. I det følgende forbedrede regeludtryk vil en uventet værdi resultere i, at tabellen ikke returnerer nogen rækker.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>Design delvis RLS

Nogle gange skal beregninger bruge værdier, der ikke er begrænset af RLS-filtre. En rapport kan f. eks. være nødt til at vise forholdet mellem indtægter for rapportbrugerens salgsområde og _alle indtægter_ .

Det er ikke muligt for et DAX-udtryk at tilsidesætte RLS – faktisk kan det ikke engang bestemmes, at RLS skal gennemtvinges, men du kan bruge en oversigtsmodeltabel. Der sendes en forespørgsel til oversigtsmodeltabellen for at hente indtægten for "alle områder", og den er ikke begrænset af nogen RLS-filtre.

Lad os se, hvordan du kan implementere dette designkrav. Forestil dig først følgende model design:

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="Der vises et billede af et modeldiagram. Det er beskrevet i følgende afsnit.":::

Modellen består af fire tabeller:

- I tabellen **Salesperson** gemmes der én række pr. sælger. Den indeholder kolonnen **EmailAddress** , hvor de enkelte sælgeres mailadresser gemmes. Denne tabel er skjult.
- I tabellen **Sales** gemmes der én række pr. ordre. Den omfatter målingen **Revenue % All Region** , der er designet til at returnere forholdet mellem indtægten for rapportbrugerens område og indtægten for alle områder.
- I tabellen **Date** gemmes der én række pr. dato, og der er mulighed for filtrering og gruppering af år og måned.
- **SalesRevenueSummary** er en beregnet tabel. Det indeholder den samlede indtægt for hver ordredato. Denne tabel er skjult.

Følgende udtryk definerer den beregnede tabel **SalesRevenueSummary** :

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> En [sammenlægningstabel](../transform-model/desktop-aggregations.md) kan opnå samme designkrav.

Følgende RLS-regel anvendes på tabellen **Salesperson** :

```dax
[EmailAddress] = USERNAME()
```

Hver af de tre modelrelationer er beskrevet i følgende tabel:

|Relation|Beskrivelse|
|---------|---------|
|![Afslutning 1 i rutediagrammet.](media/common/icon-01-red-30x30.png)|Der er en mange til mange-relation mellem tabellerne **Salesperson** og **Sales** . RLS-reglen filtrerer kolonnen **EmailAddress** for den skjulte tabel **Salesperson** ved hjælp af DAX-funktionen [USERNAME](/dax/username-function-dax). Værdien for kolonnen **Region** (for rapportbrugeren) overføres til tabellen **Sales** .|
|![Afslutning 2 i rutediagrammet.](media/common/icon-02-red-30x30.png)|Der er en en til mange-relation mellem tabellerne **Date** og **Sales** .|
|![Afslutning 3 i rutediagrammet.](media/common/icon-03-red-30x30.png)|Der er en en til mange-relation mellem tabellerne **Date** og **SalesRevenueSummary** .|

Følgende udtryk definerer målingen **Revenue % All Region** :

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> Sørg for at undgå at vise følsomme fakta. Hvis der kun er to områder i dette eksempel, ville det være muligt for en rapportbruger at beregne indtægt for det andet område.

## <a name="avoid-using-rls"></a>Undgå at bruge RLS

Undgå at bruge RLS, når det giver mening for dig. Hvis du kun har et lille antal forenklede RLS-regler, der anvender statiske filtre, kan du overveje at publicere flere datasæt i stedet for. Ingen af datasættene definerer roller, fordi hvert datasæt indeholder data for en bestemt rapportbrugermålgruppe, der har de samme datatilladelser. Opret derefter ét arbejdsområde pr. målgruppe og tildele adgangstilladelser til arbejdsområdet eller appen.

En virksomhed, der kun har to salgsområder, beslutter f. eks. at publicere et datasæt _for hvert salgsområde_ til forskellige arbejdsområder. Datasættene gennemtvinger ikke RLS. De bruger dog [forespørgselsparametre](/power-query/power-query-query-parameters) til at filtrere kildedata. På denne måde publiceres den samme model i hvert arbejdsområde – de har blot forskellige parameterværdier for datasæt. Sælgere tildeles kun adgang til ét af arbejdsområderne (eller de publicerede apps).

Der er flere fordele ved at undgå RLS:

- **Forbedret ydeevne for forespørgsler** : Det kan resultere i en forbedret ydeevne pga. færre filtre.
- **Mindre modeller:** Selvom det resulterer i flere modeller, er de mindre. Mindre modeller kan forbedre svartiden for forespørgsels- og dataopdatering, især hvis hostingkapaciteten oplever, at der er tryk på ressourcerne. Det er også nemmere at holde modelstørrelser under de størrelsesbegrænsninger, der pålægges af din kapacitet. Endelig er det nemmere at afbalancere arbejdsbelastninger på tværs af forskellige kapaciteter, da du kan oprette arbejdsområder på – eller flytte arbejdsområder til – forskellige kapaciteter.
- **Yderligere funktioner:** Power BI-funktioner, der ikke fungerer sammen med RLS, f. eks [Publicer på internettet](../collaborate-share/service-publish-to-web.md), kan bruges.

Der er dog også ulemper forbundet med at undgå RLS:

- **Flere arbejdsområder:** Der kræves ét arbejdsområde til hver enkelt rapportbrugermålgruppe. Hvis der publiceres apps, betyder det også, at der er én app pr. rapportbrugermålgruppe.
- **Duplikering af indhold:** Rapporter og dashboards skal oprettes i hvert arbejdsområde. Det kræver en yderligere indsats og tid at konfigurere og vedligeholde.
- **Brugere med rettigheder på højt niveau:** Brugere med rettigheder på højt niveau, der tilhører flere rapportbrugermålgrupper, kan ikke se en samlet visning af dataene. De skal åbne flere rapporter (fra forskellige arbejdsområder eller apps).

## <a name="troubleshoot-rls"></a>Foretag fejlfinding af RLS

Hvis RLS giver uventede resultater, skal du kontrollere, om følgende problemer er opstået:

- Der er forkerte relationer mellem modeltabeller, hvad angår kolonnetilknytninger og filterretninger.
- Egenskaben for relationen **Anvend sikkerhedsfilter i begge retninger** er ikke angivet korrekt. Du kan finde flere oplysninger i [Vejledning til tovejsrelationer](relationships-bidirectional-filtering.md).
- Tabeller indeholder ingen data.
- Der er indlæst forkerte værdier i tabeller.
- Brugeren er knyttet til flere roller.
- Modellen indeholder sammenlægningstabeller, og RLS-regler filtrerer ikke sammenlægninger og detaljer på en konsistent måde. Du kan finde flere oplysninger under [Brug sammenlægninger i Power BI Desktop (RLS til sammenlægninger)](../transform-model/desktop-aggregations.md#rls-for-aggregations).

Når en bestemt bruger ikke kan se nogen data, kan det skyldes, at den pågældendes UPN ikke er gemt, eller at den er angivet forkert. Det kan ske pludseligt, hvis brugerens konto er blevet ændret som resultat af et navneskift.

> [!TIP]
> Til testformål skal du tilføje en måling, der returnerer DAX-funktionen [USERNAME](/dax/username-function-dax). Du kan f.eks. kalde den "Hvem er jeg". Føj derefter målingen til et kortvisual i en rapport, og publicer den i Power BI.

Når en bestemt bruger kan se alle data, kan det skyldes, at den pågældende har adgang til rapporter direkte i arbejdsområdet, og den pågældende er ejeren af datasættet. RLS gennemtvinges kun, når:

- Rapporten åbnes i en app.
- Rapporten åbnes i et arbejdsområde, og brugeren knyttes til [rollen Læser](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces).

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Sikkerhed på rækkeniveau (RLS) med Power BI](../admin/service-admin-rls.md)
- [Begræns dataadgang med sikkerhed på rækkeniveau (RLS) for Power BI Desktop](../create-reports/desktop-rls.md)
- [Modelrelationer i Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
