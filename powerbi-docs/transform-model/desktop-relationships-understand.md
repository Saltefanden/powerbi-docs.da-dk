---
title: Modelrelationer i Power BI Desktop
description: Introducer teori om modelrelationer i Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 472f2ecce2e28fcb7d50356ec1322f67f2395411
ms.sourcegitcommit: 701dd80661a63c76d37d1e4f159f90e3fc8c3160
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135999"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Modelrelationer i Power BI Desktop

Denne artikel er henvendt til udviklere af importdatamodeller, der arbejder med Power BI Desktop. Det er et vigtigt emne inden for modeldesign, der er afgørende for at levere intuitive, præcise og optimale modeller.

Hvis du vil have en dybere diskussion om det optimale modeldesign, herunder tabelroller og relationer, kan du se artiklen [Forstå stjerneskema og betydningen for Power BI](../guidance/star-schema.md).

## <a name="relationship-purpose"></a>Relationsformål

Power BI-relationer kan kort fortalt overføre filtre, der er anvendt på kolonnerne i modeltabeller, til andre modeltabeller. Filtre overføres så længe, der er en relationssti, der skal følges, hvilket kan involvere overførsel til flere tabeller.

Relationsstier er deterministiske, hvilket betyder, at filtre altid overføres på samme måde og uden vilkårlig variation. Relationer kan dog være deaktiveret eller have ændret filterkonteksten af modelberegninger, der anvender bestemte DAX-funktioner. Du kan finde flere oplysninger om emnet [Relevante DAX-funktioner](#relevant-dax-functions) senere i denne artikel.

> [!IMPORTANT]
> Det er vigtigt at forstå, at modelrelationer ikke gennemtvinger dataintegritet. Du kan finde flere oplysninger om emnet [Evaluering af relationer](#relationship-evaluation) senere i denne artikel. I dette emne forklares det, hvordan modelrelationer fungerer, når der er problemer med dataintegriteten i forbindelse med dine data.

Lad os se, hvordan relationer overfører filtre, med et animeret eksempel.

![Animeret eksempel på overførsel af relationsfilter](media/desktop-relationships-understand/animation-filter-propagation.gif)

I dette eksempel består modellen af fire tabeller: **Kategori**, **Produkt**, **År** og **Salg**. Tabellen **Kategori** er relateret til tabellen **Produkt**, og tabellen **Produkt** er relateret til tabellen **Salg**. Tabellen **År** er også relateret til tabellen **Salg**. Alle relationer er en til mange-relationer (som beskrives senere i denne artikel).

En forespørgsel – muligvis genereret af en Power BI-kortvisualisering – anmoder om den samlede salgsmængde for salgsordrer, der er oprettet for en enkelt kategori, **Cat-A**, og for et enkelt år, **CY2018**. Det er grunden til, at du kan se filtre anvendt på tabellerne **Kategori** og **År**. Filteret på tabellen **Kategori** overføres til tabellen **Produkt** for at isolere to produkter, der er tildelt kategorien **Cat-A**. Derefter overføres filtrene på tabellen **Produkt** til tabellen **Salg** for at isolere blot to salgsrækker for disse produkter. Disse to salgsrækker repræsenterer salg af produkter, der er tildelt kategorien **Cat-A**. De har tilsammen en mængde på 14 enheder. Samtidigt overføres filtret på tabellen **År** for yderligere at filtrere tabellen **Salg**, hvilket resulterer i kun den ene salgsrække for produkter, der er tildelt kategorien **Cat-A**, og som er bestilt i året **CY2018**. Den mængdeværdi, der returneres af forespørgslen, er 11 enheder. Bemærk, at når der anvendes flere filtre i en tabel (f.eks. tabellen **Salg** i dette eksempel), er det altid en AND-handling, som kræver, at alle betingelser er sande.

### <a name="disconnected-tables"></a>Afbrudte tabeller

Det er usædvanligt, at en modeltabel ikke er relateret til en anden modeltabel. En sådan tabel i et gyldigt modeldesign kan beskrives som en _afbrudt tabel_. En afbrudt tabel er ikke beregnet til at overføre filtre til andre modeltabeller. I stedet bruges den til at modtage "brugerinput" (muligvis med et visuelt udsnit), som gør det muligt for modelberegninger at bruge inputværdien på en meningsfuld måde. Du kan f.eks. overveje en afbrudt tabel, der indlæses med et interval af valutakursværdier. Så længe et filter er anvendt for at filtrere efter en enkelt værdi, kan værdien bruges af et målingsudtryk til at konvertere salgsværdier.

Power BI Desktop-parameteren What-if er en funktion, der opretter en tabel uden forbindelse. Du kan finde flere oplysninger i artiklen [Opret og brug What if-parametre til at visualisere variabler i Power BI Desktop](desktop-what-if.md).

## <a name="relationship-properties"></a>Relationsegenskaber

En modelrelation relaterer en kolonne i en tabel til en kolonne i en anden tabel. Der er ét særligt tilfælde, hvor dette krav ikke er sandt, og det gælder kun for relationer med flere kolonner i DirectQuery-modeller. Du kan finde flere oplysninger i artiklen om DAX-funktionen [COMBINEVALUES](/dax/combinevalues-function-dax).

> [!NOTE]
> Det er ikke muligt at knytte en kolonne til en anden kolonne _i samme tabel_. Dette forveksles undertiden med evnen til at definere en relationsdatabase med fremmed nøglebegrænsning, som er en tabel, der refererer til sig selv. Dette relationelle databasekoncept kan bruges til at gemme relationer mellem overordnet/underordnet (f.eks. er alle medarbejderposter relateret til en "rapporterer til"-medarbejder). Oprettelse af et modelhierarki, der er baseret på denne type relation, kan ikke løses ved at oprette modelrelationer. For at opnå dette skal du se artiklen [Overordnede og underordnede funktioner](/dax/parent-and-child-functions-dax).

### <a name="cardinality"></a>Kardinalitet

Alle modelrelationer skal defineres med en kardinalitetstype. Der er fire mulige kardinalitetstyper, der repræsenterer dataegenskaberne for de "fra"- og "til"-relaterede kolonner. "Et"-siden betyder, at kolonnen indeholder entydige værdier. "To"-siden betyder, at kolonnen kan indeholde dubletværdier.

> [!NOTE]
> Hvis en dataopdateringshandling forsøger at indlæse dubletværdier i en "et"-sidekolonne, kan hele dataopdateringen mislykkes.

De fire indstillinger – sammen med de korte notationer – er beskrevet i følgende punktopstilling:

- En til mange (1:\*)
- Mange til en (\*:1)
- En til en (1:1)
- Mange til mange (\*:\*)

Når du opretter en relation i Power BI Desktop, registrerer og indstiller designeren automatisk kardinalitetstypen. Designeren forespørger modellen for at finde ud af, hvilke kolonner der indeholder entydige værdier. I forbindelse med importmodeller bruges intern lagringsstatistik, og i forbindelse med DirectQuery-modeller sendes profileringsforespørgsler til datakilden. Nogle gange kan det dog blive vist forkert. Det sker, fordi der endnu ikke er indlæst data i tabellerne, eller fordi de kolonner, du forventer vil indeholde duplikerede værdier, i øjeblikket indeholder entydige værdier. I begge tilfælde kan du opdatere kardinalitetstypen, så længe alle kolonner på "en"-siden indeholder entydige værdier (eller der er endnu ikke er indlæst rækker med data i tabellen).

Kardinalitetsmulighederne **En til mange** og **Mange til en** er stort set identiske, og de er også de mest almindelige kardinalitetstyper.

Når du konfigurerer en en til mange-relation eller mange til en-relation, vælger du den, der matcher den rækkefølge, som du har knyttet kolonnerne til. Overvej, hvordan du konfigurerer relationerne fra tabellen **Produkt** til tabellen **Salg** ved hjælp af kolonnen **Produkt-id**, der findes i hver tabel. Kardinalitetstypen vil i dette tilfælde være _En til mange_, da kolonnen **Produkt-id** i tabellen **Produkt** indeholder entydige værdier. Hvis du har tilknyttet tabellerne i den modsatte retning, **Salg** til **Produkt**, er kardinaliteten _Mange til en_.

Et **En til en**-relation betyder, at begge kolonner indeholder unikke værdier. Denne kardinalitetstype er ikke almindelig, og den repræsenterer sandsynligvis et knap så optimalt modeldesign på grund af lagringen af redundante data. Du kan finde flere oplysninger om brug af denne kardinalitets type, i [Vejledning til en til en-relationer](../guidance/relationships-one-to-one.md).

En **Mange til mange**-relation betyder, at begge kolonner kan indeholde dubletværdier. Denne kardinalitetstype anvendes sjældent. Det er typisk nyttig, når du skal designe komplekse modelbehov. Du kan finde en vejledning i, hvordan du bruger denne kardinalitetstype, under [Vejledning til mange til mange-relationer](../guidance/relationships-many-to-many.md).

> [!NOTE]
> Kardinalitetstypen Mange til mange understøttes i øjeblikket ikke for modeller, der er udviklet til Microsoft Power BI-rapportserver.

> [!TIP]
> I Power BI Desktop-modelvisning kan du fortolke en relations kardinalitetstype ved at se på indikatorerne (1 eller \*) på begge sider af relationslinjen. Hvis du vil finde ud af, hvilke kolonner der er relaterede, skal du vælge – eller holde markøren over – relationslinjen for at markere kolonnerne.

### <a name="cross-filter-direction"></a>Tværgående filterretning

Alle modelrelationer skal defineres med en tværgående filterretning. Dit valg bestemmer den eller de retninger, som filtrene overføres i. De mulige indstillinger for tværgående filterretninger afhænger af kardinalitetstypen.

| Kardinalitetstype | Tværgående filtermuligheder |
| --- | --- |
| En til mange (eller Mange til en) | Enkelt<br>Begge |
| En til en | Begge |
| Mange til mange | Enkelt (Tabel1 til Tabel2)<br>Enkelt (Tabel2 til Tabel1)<br>Begge |

_Enkelt_ tværgående filterretning betyder "enkelt retning", og _Begge_ betyder "begge retninger". En relation, der filtrerer i begge retninger, beskrives som regel som _tovejs_.

I forbindelse med en til mange-relationer er den tværgående filterretning altid fra "en"-siden og eventuelt fra "mange"-siden (tovejs). I forbindelse med en til en-relationer er den tværgående filterretning altid fra begge tabeller. Endelig kan en tværgående filterretning for mange til mange-relationer enten være fra en af tabellerne eller fra begge tabeller. Bemærk, at filtre altid overføres fra den pågældende side, når kardinalitetstypen indeholder en "en"-side.

Når retningen for krydsfiltrering er angivet til **Begge**, er der en yderligere egenskab tilgængelig. Der kan anvendes tovejsfiltrering, når sikkerhed på rækkeniveau håndhæves. Du kan finde flere oplysninger om sikkerhed på rækkeniveau i artiklen [Sikkerhed på rækkeniveau med Power BI Desktop](../create-reports/desktop-rls.md).

Ændring af relationen tværgående filterretning – herunder deaktiveringen af filteroverførsel – kan også udføres ved en modelberegning. Det opnås ved at bruge DAX-funktionen [CROSSFILTER](/dax/crossfilter-function).

Tovejs relationer kan påvirke ydeevnen negativt. Når du forsøger at konfigurere en tovejs relation, kan det desuden medføre tvetydige filteroverførselsstier. I dette tilfælde vil Power BI Desktop muligvis ikke bekræfte ændringen i relationen og advare dig med en fejlmeddelelse. Nogle gange kan Power BI Desktop give dig mulighed for at definere tvetydige relationsstier mellem tabeller. Rangplaceringsregler, der påvirker registreringen af flertydighed og stiopløsningen, er beskrevet senere i denne artikel under emnet [Rangplaceringsregler](#precedence-rules).

Vi anbefaler kun at anvende tovejs filtrering, hvis der er behov for det. Du kan finde flere oplysninger i [Vejledning til tovejsrelationer](../guidance/relationships-bidirectional-filtering.md).

> [!TIP]
> I Power BI Desktops modelvisning kan du fortolke en relations tværgående filterretning ved at lægge mærke til pilespidsen/pilespidserne langs relationslinjen. En enkelt pilespids repræsenterer et filter med et enkelt retning i pilespidsens retning. En dobbelt pilespids repræsenterer en tovejs relation.

### <a name="make-this-relationship-active"></a>Aktivér denne relation

Filteret mellem to modeltabeller kan kun have én aktiv overførselssti. Det er dog muligt at introducere flere relationsstier, selvom disse relationer skal være konfigureret som _inaktive_. Inaktive relationer kan kun gøres aktive under evalueringen af en modelberegning. Det opnås ved hjælp af DAX-funktionen [USERELATIONSHIP](/dax/userelationship-function-dax).

Du kan finde flere oplysninger i [Vejledning til aktive i forhold til inaktive relationer](../guidance/relationships-active-inactive.md).

> [!TIP]
> I Power BI Desktops modelvisning kan du fortolke en relations aktive og inaktive status. En aktiv relation vises af en ubrudt linje. En inaktiv relation vises som en stiplet linje.

### <a name="assume-referential-integrity"></a>Antag referentiel integritet

Egenskaben _Antag referentiel integritet_ er kun tilgængelig for en til mange- og en til en-relationer mellem to DirectQuery-lagringstilstandstabeller, der er baseret på den samme datakilde. Når funktionen er aktiveret, vil oprindelige forespørgsler, der sendes til datakilden, sammenknytte de to tabeller ved hjælp af en indre joinforbindelse i stedet for en ydre joinforbindelse. Aktivering af denne egenskab forbedrer ydeevnen for forespørgsler generelt, selvom det er afhængigt af specifikationerne for datakilden.

Aktivér altid denne egenskab, når der findes en fremmed nøglebegrænsning for en database mellem de to tabeller. Når der ikke findes en fremmed nøglebegrænsning, kan du stadig aktivere egenskaben, så længe du er sikker på, at der findes dataintegritet.

> [!IMPORTANT]
> Hvis dataintegriteten bliver kompromitteret, eliminerer den indre joinforbindelse uoverensstemmende rækker mellem tabellerne. Du kan f.eks. overveje en **Salg**-modeltabel med en **Produkt-id**-kolonneværdi, der ikke findes i tabellen med den relaterede **Produkt**-tabel. Filteroverførsel fra tabellen **Produkt** til tabellen **Salg** eliminerer salgsrækker for ukendte produkter. Dette ville resultere i en underdrivelse af salgsresultaterne.
>
> Du kan finde flere oplysninger i artiklen [Indstillinger for antagelse af referentiel integritet i Power BI Desktop](../connect-data/desktop-assume-referential-integrity.md).

## <a name="relevant-dax-functions"></a>Relevante DAX-funktioner

Der findes adskillige DAX-funktioner, som er relevante for modelrelationer. Hver funktion er beskrevet kort i følgende punktopstilling:

- [RELATED](/dax/related-function-dax): Henter værdien fra "en"-siden.
- [RELATEDTABLE](/dax/relatedtable-function-dax): Hent en tabel med rækker fra "mange"-siden.
- [USERELATIONSHIP](/dax/userelationship-function-dax): Gennemtvinger brugen af en specifik inaktiv modelrelation.
- [CROSSFILTER](/dax/crossfilter-function): Ændrer relationens tværgående filterretning (til en eller begge) eller deaktiverer filteroverførsel (ingen).
- [COMBINEVALUES](/dax/combinevalues-function-dax): Joinforbinder to eller flere tekststrenge til én streng. Formålet med denne funktion er at understøtte relationer med flere kolonner i DirectQuery-modeller.
- [TREATAS](/dax/treatas-function): Anvender resultatet af et tabeludtryk som filtre til kolonner fra en ikke-relateret tabel.
- [Overordnede og underordnede funktioner](/dax/parent-and-child-functions-dax): En serie relaterede funktioner, der kan bruges til at generere beregnede kolonner for at naturalisere et overordnet/underordnet hierarki. Disse kolonner kan derefter bruges til at oprette et fast hierarki.

## <a name="relationship-evaluation"></a>Validering af relationer

Modelrelationer klassificeres fra et evalueringsperspektiv enten som _almindelige_ eller _begrænsede_. Det er ikke en konfigurerbar relationsegenskab. Det er faktisk afledt af kardinalitetstypen og datakilden for de to relaterede tabeller. Det er vigtigt at forstå evalueringstypen, fordi der kan opstå problemer med ydeevnen eller konsekvenser, hvis dataintegriteten kompromitteres. Disse konsekvenser og konsekvensen for integriteten er beskrevet i dette emne.

For det første kræves der modelteori for at forstå relationsevalueringer.

En import eller DirectQuery-model henter alle sine data fra enten VertiPaq-cachen eller kildedatabasen. I begge tilfælde kan Power BI afgøre, om der findes en "en"-side af en relation.

En sammensat model kan dog bestå af tabeller ved hjælp af forskellige lagringstilstande (import, DirectQuery eller dobbelt) eller flere DirectQuery-kilder. Hver kilde, herunder VertiPaq-cachen for importdata, anses for at være en _dataø_. Modelrelationer kan derefter klassificeres som _intern_ eller _på tværs_. En intern forbindelse er en, der relaterer til to tabeller inden for en dataø, mens en tværgående relation er relateret til tabeller fra forskellige dataøer. Bemærk, at relationer i import- eller DirectQuery-modeller altid er interne.

Lad os se et eksempel på en sammensat model.

![Eksempel på en sammensat model bestående af to øer](media/desktop-relationships-understand/data-island-example.png)

I dette eksempel består den sammensatte model af to øer: en VertiPaq-dataø og en DirectQuery-kildedataø. VertiPaq-dataøen indeholder tre tabeller, og DirectQuery-kildedataøen indeholder to tabeller. Der eksisterer en tværgående relation, som kan relatere en tabel i VertiPaq-dataøen til en tabel i DirectQuery-kildedataøen.

### <a name="regular-relationships"></a>Almindelige relationer

En modelrelation er _almindelig_, når forespørgselsprogrammet kan bestemme relationens "en"-side. Det har bekræftelse på, at kolonnen "en" indeholder entydige værdier. Alle en til mange-relationer mellem øer er almindelige relationer.

I det følgende eksempel er der to almindelige relationer, der begge er markeret som **S**. Relationerne omfatter en til mange-relationen inden for Vertipaq-øen og mange-relationerne inden for DirectQuery-kilden.

![Eksempel på en sammensat model bestående af to øer med almindelige relationer markeret](media/desktop-relationships-understand/data-island-example-strong.png)

I forbindelse med importmodeller, hvor alle data er gemt i VertiPaq-cachen, oprettes der en datastruktur for hver almindelig relation på dataopdateringstidspunktet. Datastrukturerne består af indekserede tilknytninger af alle kolonne til kolonne-værdier, og formålet er at fremskynde sammenkædningen af tabeller på forespørgselstidspunktet.

På forespørgselstidspunktet tillader almindelige relationer _tabeludvidelse_. Tabeludvidelse resulterer i oprettelsen af en virtuel tabel ved at medtage de oprindelige kolonner i basistabellen og derefter udvide til relaterede tabeller. I forbindelse med importtabeller udføres det i forespørgselsprogrammet. I forbindelse med DirectQuery-tabeller udføres det i den oprindelige forespørgsel, der sendes til kildedatabasen (forudsat at egenskaben **Antag referentiel integritet** ikke er aktiveret). Forespørgselsprogrammet reagerer derefter på den udvidede tabel og anvender filtre og gruppering efter værdierne i de udvidede tabelkolonner.

> [!NOTE]
> Inaktive relationer udvides også, selvom relationen ikke bruges af en beregning. Tovejs relationer har ingen indvirkning på tabeludvidelser.

For en til mange-relationer sker tabeludvidelsen fra "mange" til "en" ved hjælp af semantikken VENSTRE YDRE JOINFORBINDELSE. Når der ikke findes en tilsvarende værdi fra "mange"- til "en"-siden, føjes der en tom virtuel række til "en"-sidetabellen.

Tabeludvidelsen sker også for interne en til en-relationer, men ved hjælp af semantikken komplet ydre joinforbindelse. Det sikrer, at der tilføjes tomme virtuelle rækker på begge sider, når det er nødvendigt.

De tomme virtuelle rækker er effektivt _ukendte medlemmer_. Ukendte medlemmer repræsenterer referentielle integritetsfejl, hvor "mange"-sideværdien ikke har nogen tilsvarende "en"-sideværdi. Ideelt set skal disse tomme rækker ikke findes, og de kan fjernes ved at rense eller reparere kildedataene.

Lad os se, hvordan tabeludvidelse fungerer i et animeret eksempel.

![Animeret eksempel på tabeludvidelse](media/desktop-relationships-understand/animation-expanded-table.gif)

I dette eksempel består modellen af tre tabeller: **Kategori**, **Produkt** og **Salg**. Tabellen **Kategori** relaterer til tabellen **Produkt** med en en til mange-relation, og tabellen **Produkt** relaterer til tabellen **Salg** med en en til mange-relation. Tabellen **Kategori** indeholder to rækker, tabellen **Produkt** indeholder tre rækker, og tabellen **Salg** indeholder fem rækker. Der er tilsvarende værdier på begge sider af alle relationer, hvilket betyder, at der ikke er nogen overtrædelser af referentiel integritet. Der vises en udvidet forespørgselstidstabel. Tabellen består af kolonnerne fra alle tre tabeller. Det er effektivt et ikke-normaliseret perspektiv for dataene i de tre tabeller. Der føjes en ny række til tabellen **Salg**, og den har en produktions-id-værdi (9), som ikke har en tilsvarende værdi i tabellen **Produkt**. Det er en overtrædelse af referentiel integritet. I den udvidede tabel indeholder den nye række (tomme) værdier for tabelkolonnerne **Kategori** og **Produkt**.

### <a name="limited-relationships"></a>Begrænsede relationer

En modelrelation er _begrænset_, når der ikke er nogen garanteret "en"-side. Det kan skyldes to årsager:

- Relationen bruger en mange til mange-kardinalitetstype (selvom en eller begge kolonner indeholder entydige værdier)
- Relationen er på tværs af øen (hvilket kun kan være tilfældet for sammensatte modeller)

I det følgende eksempel er der to begrænsede relationer, der begge er markeret som **W**. De to relationer omfatter mange til mange-relationen inden for Vertipaq-øen og en til mange-relationen på tværs af øen.

![Eksempel på en sammensat model bestående af to øer med begrænsede relationer markeret](media/desktop-relationships-understand/data-island-example-weak.png)

I forbindelse med importmodeller oprettes der aldrig datastrukturer for begrænsede relationer. Det betyder, at tabellens joinforbindelser skal løses på forespørgselstidspunktet.

Der sker aldrig tabeludvidelse for begrænsede relationer. Tabel-joinforbindelser opnås ved hjælp af semantikken for indre joinforbindelse, og derfor tilføjes der ikke tomme virtuelle rækker for at kompensere for overtrædelser af referentiel integritet.

Der er yderligere begrænsninger i forbindelse med begrænsede relationer:

- Den relaterede DAX-funktion kan ikke bruges til at hente kolonneværdierne for "en"-side
- Gennemtvingning af RLS har topologibegrænsninger

> [!NOTE]
> I Power BI Desktops modelvisning er det ikke altid muligt at afgøre, om en modelrelation er almindelig eller begrænset. En mange til mange-relation er altid begrænset, da den er en en til mange-relation, når den er en tværgående relation. Hvis du vil finde ud af, om det er en tværgående relation, skal du inspicere tabellagingstilstandene og datakilderne for at nå frem til den korrekte afgørelse.

### <a name="precedence-rules"></a>Rangplaceringsregler

Tovejs relationer kan introducere flere – og derfor tvetydige – filteroverførselsstier mellem modeltabeller. Følgende liste viser rangplaceringsregler, som Power BI bruger til registrering af flertydighed og stiopløsning:

1. Mange til en- og en til en-relationer, herunder begrænsede relationer
2. Mange til mange-relationer
3. Tovejsrelationer i den omvendte retning (dvs. fra "mange"-siden)

### <a name="performance-preference"></a>Indstillinger for ydeevne

Følgende liste viser en oversigt over filtres overførselsydeevne fra den hurtigste til langsomste:

1. En til mange-relationer mellem øer
2. Mange til mange-kardinalitetsrelationer
3. Mange til mange-modelrelationer, der opnås med en mellemliggende tabel, og som omfatter mindst én tovejs relation
4. Relationer på tværs af øer

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Forstå, hvad et stjerneskema er, og hvorfor det er vigtigt for Power BI](../guidance/star-schema.md)
- [Vejledning til en til en-relationer](../guidance/relationships-one-to-one.md)
- [Vejledning til mange til mange-relation](../guidance/relationships-many-to-many.md)
- [Vejledning til aktive i forhold til inaktive relationer](../guidance/relationships-active-inactive.md)
- [Vejledning til tovejsrelationer](../guidance/relationships-bidirectional-filtering.md)
- [Vejledning til fejlfinding af relationer](../guidance/relationships-troubleshoot.md)
- Video: [Hvad du må og ikke må i forbindelse med Power BI-relationer](https://www.youtube.com/watch?v=78d6mwR8GtA)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
