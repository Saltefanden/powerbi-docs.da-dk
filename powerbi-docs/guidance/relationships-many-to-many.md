---
title: Vejledning til mange-til-mange-relation
description: Vejledning til udvikling af modeller med mange til mange-relationer.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 3c94c25f5f1ba717f68a0c2a5ec661be10f70135
ms.sourcegitcommit: 7e99e8af9caf9340958c4607a94728d43e8c3811
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/02/2020
ms.locfileid: "91668522"
---
# <a name="many-to-many-relationship-guidance"></a>Vejledning til mange-til-mange-relation

Denne artikel henvender sig til designere af datamodeller, der arbejder med Power BI Desktop. Den indeholder en beskrivelse af tre forskellige scenarier med udformning af mange til mange-relationer. Den indeholder også en vejledning i, hvordan du skaber vellykkede design med dem i dine modeller.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

Faktisk er der tre mange til mange-scenarier. De kan forekomme, når du skal:

- [Relatere to tabeller af dimensionstypen](#relate-many-to-many-dimensions)
- [Relatere to tabeller af faktatypen](#relate-many-to-many-facts)
- [Relatere tabeller med fakta på højere detaljeringsniveau](#relate-higher-grain-facts), når tabeller af faktatypen gemmer rækker på højere detaljeringsniveau end rækkerne i tabellen af dimensionstypen

## <a name="relate-many-to-many-dimensions"></a>Relater mange til mange-dimensioner

Lad os kigge på den første type med et mange til mange-scenarie ved hjælp af et eksempel. I det klassiske scenarie relateres to enheder: bankkunder og bankkonti. Tænk på, at kunderne kan have flere konti, og at konti kan have flere kunder. Når en konto har flere kunder, kaldes de ofte _indehavere af fælles konto_.

Udformning af disse enheder er ligetil. I en tabel af dimensionstypen gemmes konti, og i en anden tabel af dimensionstypen gemmes kunder. Som det er karakteristisk for tabeller af dimensionstypen, er der en id-kolonne i hver tabel. Der kræves en tredje tabel for at udforme relationen mellem de to tabeller. Denne tabel kaldes ofte for en _mellemtabel_. I dette eksempel er dets formål at gemme én række for hver kunde-konto-tilknytning. Når denne tabel kun indeholder id-kolonner, kaldes den sjovt nok for en [_faktatabel uden fakta_](star-schema.md#factless-fact-tables).

Her er et forenklet modeldiagram over de tre tabeller.

![Diagram, der viser en model, som indeholder tre tabeller. Designet er beskrevet i følgende afsnit.](media/relationships-many-to-many/bank-account-customer-model-example.png)

Den første tabel kaldes for **Konto** og indeholder to kolonner: **Konto-id** og **Konto**. Den anden tabel kaldes for **KontoKunde** og indeholder to kolonner: **Konto-id** og **Kunde-id**. Den tredje tabel kaldes for **Kunde** og indeholder to kolonner: **Kunde-id** og **Kunde**. Der findes ingen relationer mellem nogen af tabellerne.

Der tilføjes to én til mange-relationer for at relatere tabellerne. Her er et opdateret modeldiagram over de relaterede tabeller. En tabel af faktatypen med navnet **Transaktion** er blevet tilføjet. Den registrerer kontotransaktioner. Mellemtabellen og alle id-kolonner er blevet skjult.

![Et diagram, der viser, at modellen nu indeholder fire tabeller. En til mange-relationer blev tilføjet for at relatere alle tabeller.](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

For at hjælpe med at beskrive, hvordan filteroverførslen af relationen fungerer, er modeldiagrammet blevet redigeret for at vise tabelrækkerne.

> [!NOTE]
> Det er ikke muligt at vise tabelrækkerne i Power BI Desktop-modeldiagrammet. Det gøres i denne artikel for at understøtte diskussionen med tydeligere eksempler.

![Diagram, hvor det ses, at tabelrækkerne nu vises i modellen. Rækkedetaljerne for de fire tabeller er beskrevet i følgende afsnit.](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

Rækkedetaljerne for de fire tabeller er beskrevet i følgende punktopstilling:

- Tabellen **Konto** indeholder to rækker:
  - **Konto-id** 1 er for Konto-01
  - **Konto-id** 2 er for Konto-02
- Tabellen **Kunde** indeholder to rækker:
  - **Kunde-id** 91 er for Kunde-91
  - **Kunde-id** 92 er for Kunde-92
- Tabellen **KontoKunde** indeholder tre rækker:
  - **Konto-id** 1 er knyttet til **Kunde-id** 91
  - **Konto-id** 1 er knyttet til **Kunde-id** 92
  - **Konto-id** 2 er knyttet til **Kunde-id** 92
- Tabellen **Transaktion** indeholder tre rækker:
  - **Dato** 1. januar 2019, **Konto-id** 1, **Beløb** 100
  - **Dato** 2. februar 2019, **Konto-id** 2, **Beløb** 200
  - **Dato** 3. marts 2019, **Konto-id** 1, **Beløb** -25

Lad os se, hvad der sker, når der sendes en forespørgsel til modellen.

Herunder er to visualiseringer, hvor kolonnen **Beløb** fra tabellen **Transaktion** opsummeres. Den første visualisering grupperes efter konto, så summen af kolonnerne **Beløb** repræsenterer _kontosaldoen_. Den anden visualisering grupperes efter kunde, så summen af kolonnerne **Beløb** repræsenterer _kundesaldoen_.

![Diagram, der viser to rapportvisualiseringer side om side. Visualiseringerne er beskrevet i følgende afsnit.](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

Den første visualisering kaldes for **Kontosaldo** og indeholder to kolonner: **Konto** og **Beløb**. Følgende resultat vises:

- Konto-01 saldobeløbet er 75
- Konto-02 saldobeløbet er 200
- Totalen er 275

Den anden visualisering kaldes for **Kundesaldo** og indeholder to kolonner: **Kunde** og **Beløb**. Følgende resultat vises:

- Kunde-91 saldobeløbet er 275
- Kunde-92 saldobeløbet er 275
- Totalen er 275

Et hurtigt overblik over tabelrækkerne og visualiseringen **Kontosaldo** viser, at resultatet er korrekt for hver konto og det samlede beløb. Det skyldes, at hver kontogruppering resulterer i en filteroverførsel til tabellen **Transaktion** for den pågældende konto.

Noget ser dog ikke korrekt ud i visualiseringen **Kundesaldo**. Hver kunde i visualiseringen **Kundesaldo** har den samme saldo som den samlede saldo. Dette resultat kan kun være korrekt, hvis hver kunde var indehaver af en fælles konto for hver konto. Det er ikke tilfældet i dette eksempel. Problemet er relateret til filteroverførsel. Det overføres ikke helt til tabellen **Transaktion**.

Følg filterretninger for relationen fra tabellen **Kunde** til tabellen **Transaktion**. Det bør være tydeligt, at relationen mellem tabellen **Konto** og **KontoKunde** overføres i den forkerte retning. Filterretningen for denne relation skal være angivet til **Begge**.

![Diagram, der viser, at modellen er opdateret. Der filtreres nu i begge retninger.](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![Diagram, der viser de samme to rapportvisualiseringer side om side. Det første visuelle element er ikke ændret, mens det andet visuelle element er.](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

Som forventet er der ingen ændring af visualiseringen **Kontosaldo**.

Følgende resultat vises nu i visualiseringen **Kundesaldo**:

- Kunde-91 saldobeløbet er 75
- Kunde-92 saldobeløbet er 275
- Totalen er 275

Det korrekte resultat vises nu i visualiseringen **Kundesaldo**. Følg selv filterretningerne, og se, hvordan kundesaldiene blev beregnet. Forstå også, at visualiseringens total betyder _alle kunder_.

En person, der ikke er bekendt med modelrelationer, ville måske konkludere, at resultatet er forkert. De spørger måske: _Hvorfor er totalen for **Kunde-91** og **Kunde-92** ikke lig med 350 (75 + 275)?_

Svaret på spørgsmålet ligger i forståelsen af mange til mange-relationen. Hver kundesaldo kan repræsentere tilføjelsen af flere kontosaldi, så kundesaldiene er _ikke additiv_.

### <a name="relate-many-to-many-dimensions-guidance"></a>Vejledning til relatering af mange til mange-dimensioner

Når du har mange til mange-relationer mellem tabeller af dimensionstypen, giver vi følgende vejledning:

- Tilføj hver mange til mange-relaterede enhed som en model, og kontrollér, at hver indeholder en unik identifikatorkolonne (id)
- Tilføj en mellemtabel for at gemme tilknyttede enheder
- Opret én til mange-relationer mellem de tre tabeller
- Konfigurer **én** tovejsrelation, så filteroverførsel kan fortsætte til tabeller af faktatypen
- Når det ikke er passende at have manglende id-værdier, skal du angive egenskaben **Er nullable** for id-kolonnerne til FALSK. Hvis der refereres til manglende værdier, vil dataopdateringen mislykkes
- Skjul mellemtabellen (medmindre den indeholder yderligere kolonner eller målinger, der kræves til rapportering)
- Skjul alle id-kolonner, der ikke er egnet til rapportering (f.eks. når id'erne er surrogatnøgler)
- Hvis det giver mening, at lade en id-kolonne være synlig, skal du sikre, at den er på "én"-siden af relationen – skjul altid "mange"-siden af kolonnen. Det resulterer i den bedste filterfunktion.
- Hvis du vil undgå forvirring eller misforståelser, kan du videregive forklaringer til dine rapportbrugere. Du kan tilføje beskrivelser med tekstfelter eller [værktøjstip til visuelle overskrifter](report-page-tooltips.md)

Vi anbefaler ikke, at du relaterer tabeller af dimensionstypen med mange til mange-relationer direkte. Denne designmetode kræver konfiguration af en relation med mange til mange-kardinalitet. Det kan opnås konceptuelt, men det forudsætter, at de relaterede kolonner indeholder dubletværdier. Det er dog en velaccepteret designpraksis, at tabeller af dimensionstypen indeholder en id-kolonne. Tabeller af dimensionstypen skal altid bruge id-kolonnen som "én"-siden af en relation.

## <a name="relate-many-to-many-facts"></a>Relater fakta med mange til mange-relation

Det andet mange til mange-scenarie omfatter relatering af to tabeller af faktatypen. To tabeller af faktatypen kan relateres direkte. Denne designteknik kan være nyttig til hurtig og nem udforskning af data. Men generelt anbefaler vi dog ikke denne designmetode. Vi forklarer hvorfor senere i dette afsnit.

Lad os se på et eksempel, der omfatter to tabeller af faktatypen: **Ordre** og **Opfyldelse**. Tabellen **Ordre** indeholder én række pr. ordrelinje, og tabellen **Opfyldelse** kan indeholde ingen eller flere rækker pr. ordrelinje. Rækkerne i tabellen **Ordre** repræsenterer salgsordrer. Rækker i tabellen **Opfyldelse** repræsenterer ordreelementer, der er blevet sendt. I en mange til mange-relation relateres de to kolonner **Ordre-id** kun ved hjælp af filteroverførsel fra tabellen **Ordre** (**Ordre** filtrerer **Opfyldelse**).

![Diagram, der viser en model, som indeholder to tabeller: Ordre og Opfyldelse.](media/relationships-many-to-many/order-fulfillment-model-example.png)

Relationskardinaliteten er angivet til mange-til-mange for at understøtte lagring af dubletværdier i **Ordre-id** i begge tabeller. I tabellen **Ordre** kan der findes dubletværdier i **Ordre-id**, da en ordre kan have flere linjer. I tabellen **Opfyldelse** kan der findes dubletværdier i **Ordre-id**, da ordrer kan have flere linjer, og ordrelinjer kan opfyldes af flere forsendelser.

Lad os nu se på tabelrækkerne. I tabellen **Opfyldelse** vil du bemærke, at ordrelinjer kan opfyldes af flere forsendelser. (Manglen på en ordrelinje betyder, at ordren endnu ikke er opfyldt.)

![Diagram, hvor det ses, at tabelrækkerne nu vises i modellen. Rækkedetaljerne for de to tabeller er beskrevet i følgende afsnit.](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

Rækkedetaljerne for de to tabeller er beskrevet i følgende punktopstilling:

- Tabellen **Ordre** indeholder fem rækker:
  - **Ordredato** 1. januar 2019, **Ordre-id** 1, **Ordrelinje** 1, **Produkt-id** Prod-A, **Ordreantal** 5, **Salg** 50
  - **Ordredato** 1. januar 2019, **Ordre-id** 1, **Ordrelinje** 2, **Produkt-id** Prod-B, **Ordreantal** 10, **Salg** 80
  - **Ordredato** 2. februar 2019, **Ordre-id** 2, **Ordrelinje** 1, **Produkt-id** Prod-B, **Ordreantal** 5, **Salg** 40
  - **Ordredato** 2. februar 2019, **Ordre-id** 2, **Ordrelinje** 2, **Produkt-id** Prod-C, **Ordreantal** 1, **Salg** 20
  - **Ordredato** 3. marts 2019, **Ordre-id** 3, **Ordrelinje** 1, **Produkt-id** Prod-C, **Ordreantal** 5, **Salg** 100
- Tabellen **Opfyldelse** indeholder fire rækker:
  - **Opfyldelsesdato** 1. januar 2019, **Opfyldelses-id** 50, **Ordre-id** 1, **Ordrelinje** 1, **Opfyldelsesantal** 2
  - **Opfyldelsesdato** 2. februar 2019, **Opfyldelses-id** 51, **Ordre-id** 2, **Ordrelinje** 1, **Opfyldelsesantal** 5
  - **Opfyldelsesdato** 2. februar 2019, **Opfyldelses-id** 52, **Ordre-id** 1, **Ordrelinje** 1, **Opfyldelsesantal** 3
  - **Opfyldelsesdato** 1. januar 2019, **Opfyldelses-id** 53, **Ordre-id** 1, **Ordrelinje** 2, **Opfyldelsesantal** 10

Lad os se, hvad der sker, når der sendes en forespørgsel til modellen. Her er en tabelvisualisering, hvor ordre- og opfyldelsesantal sammenlignes efter tabellen **Ordre** og kolonnen **Ordre-id**.

![Diagram, der viser en tabelvisualisering med tre kolonner: Ordre-id, Ordreantal og Opfyldelsesantal.](media/relationships-many-to-many/order-fulfillment-model-queried.png)

Der præsenteres et nøjagtigt resultat i visualiseringen. Modellens anvendelighed er dog begrænset. Du kan kun filtrere eller gruppere efter tabellen **Ordre** og kolonnen **Ordre-id**.

### <a name="relate-many-to-many-facts-guidance"></a>Vejledning til relatering af fakta med mange til mange-relation

Generelt anbefaler vi ikke, at du relaterer to tabeller af faktatypen direkte ved hjælp af mange til mange-kardinalitet. Den primære årsag er, at modellen ikke giver fleksibilitet i den måde, som rapportvisualiseringerne filtrerer eller grupperer på. I eksemplet er det kun muligt for visualiseringer at filtrere eller gruppere efter tabellen **Ordre** og kolonnen **Ordre-id**. En yderligere årsag vedrører kvaliteten af dine data. Hvis der er integritetsproblemer med dine data, udelades nogle rækker muligvis under forespørgsler på grund af den _begrænsede relation_. Du kan finde flere oplysninger i [Modelrelationer i Power BI Desktop (Evaluering af relationer)](../transform-model/desktop-relationships-understand.md#relationship-evaluation).

I stedet for at relatere tabeller af faktatypen direkte, anbefaler vi, at du indfører principper for design af et [stjerneskema](star-schema.md). Det gør du ved at tilføje tabeller af dimensionstypen. Tabeller af dimensionstypen relateres derefter til tabeller af faktatypen ved hjælp af én til mange-relationer. Denne designmetode er robust, da den giver fleksible rapporteringsmuligheder. Den giver dig mulighed for at filtrere eller gruppere ved hjælp af en hvilken som helst af kolonnerne i dimensionstypen og opsummere en hvilken som helst tabel af faktatypen.

Lad os se på en bedre løsning.

![Diagram, der viser en model, som indeholder seks tabeller: Ordrelinje, Ordredato, Ordre, Opfyldelse, Produkt og Opfyldelsesdato.](media/relationships-many-to-many/order-fulfillment-model-improved.png)

Bemærk følgende designændringer:

- Modellen indeholder nu fire ekstra tabeller: **Ordrelinje**, **Ordredato**, **Produkt**og **Opfyldelsesdato**
- De fire ekstra tabeller er tabeller af dimensionstypen, og disse tabeller er relateret til tabeller af faktatypen ved hjælp af én til mange-relationer
- Tabellen **Ordrelinje** indeholder kolonnen **Ordrelinje-id**, der repræsenterer værdien **Ordre-id** ganget med 100 samt værdien **Ordrelinje** – et entydigt id for hver ordrelinje
- Tabellerne **Ordre** og **Opfyldelse** indeholder nu kolonnen **Ordrelinje-id**, og de indeholder ikke længere kolonnerne **Ordre-id** og **Ordrelinje**
- Tabellen **Opfyldelse** indeholder nu kolonnerne **Ordredato** og **Produkt-id**
- Tabellen **Opfyldelsesdato** er kun relateret til tabellen **Opfyldelse**
- Alle kolonner med entydige id'er er skjulte

Hvis du tager dig tid til at anvende principper for design af et stjerneskema, får du følgende fordele:

- Dine rapportvisualiseringer kan _filtrere eller gruppere_ efter en hvilken som helst synlig kolonne fra tabeller af dimensionstypen
- Dine rapportvisualiseringer kan _opsummere_ en hvilken som helst synlig kolonne fra tabeller af faktatypen
- Filtre, der er anvendt på tabellerne **Ordrelinje**, **Ordredato** eller **Produkt**, overføres til begge tabeller af faktatypen
- Alle relationer er én til mange-relationer, og hver relation er en _almindelig relation_. Problemer med dataintegritet maskeres ikke. Du kan finde flere oplysninger i [Modelrelationer i Power BI Desktop (Evaluering af relationer)](../transform-model/desktop-relationships-understand.md#relationship-evaluation).

## <a name="relate-higher-grain-facts"></a>Relater fakta på højere detaljeringsniveau

Dette mange til mange-scenarie er meget anderledes end de to, der allerede er beskrevet i denne artikel.

Lad os kigge på et eksempel med fire tabeller: **Dato**, **Salg**, **Produkt** og **Mål**. **Dato** og **Produkt** er tabeller af dimensionstypen, og ved hjælp af én til mange-relationer relateres hver til tabellen **Salg**, som er af faktatypen. Indtil videre repræsenterer det et godt design for et stjerneskema. Tabellen **Mål** er dog endnu ikke relateret til de andre tabeller.

![Diagram, der viser en model, som indeholder fire tabeller: Dato, Salg, Produkt og Mål.](media/relationships-many-to-many/sales-targets-model-example.png)

Tabellen **Mål** indeholder tre kolonner: **Kategori**, **Målantal**og **Målår**. Tabelrækkerne viser en granularitet på år og produktkategori. Det vil sige, at mål, der bruges til at måle salgspræstation, angives hvert år for hver produktkategori.

![Diagram, der viser, at tabellen Mål har tre kolonner: Målår, Kategori og Målantal.](media/relationships-many-to-many/sales-targets-model-target-rows.png)

Da data gemmes på et højere niveau i tabellen **Mål** end tabeller af dimensionstypen, kan der ikke oprettes en én til mange-relation. Det gælder i hvert fald for én af relationerne. Lad os se på, hvordan tabellen **Mål** kan relateres til tabellerne af dimensionstypen.

### <a name="relate-higher-grain-time-periods"></a>Relater tidsperioder på højere detaljeringsniveau

En relation mellem tabellerne **Dato** og **Mål** skal være en én til mange-relation. Det skyldes, at kolonneværdierne for **Målår** er datoer. I dette eksempel er hver kolonneværdi af typen **Målår** den første dato i målåret.

> [!TIP]
> Når du gemmer fakta med en højere tidsgranularitet end dag, skal du angive datatypen for kolonnen til **Dato** (eller **Heltal**, hvis du bruger datonøgler). I kolonnen skal du gemme en værdi, der repræsenterer den første dag i tidsperioden. I en periode på et år registreres 1. januar for eksempel, og i en periode på en måned registreres den første dag i måneden.

Du skal dog være omhyggelig med at sikre, at filtre på måneds- eller datoniveau giver et meningsfyldt resultat. Uden nogen speciel beregningslogik kan den første dag i hvert år bogstaveligt talt blive rapporteret som måldatoer i rapportvisualiseringer. Alle andre dage – og alle måneder undtagen januar – vil opsummere målantallet som TOMT.

I følgende matrixvisualisering kan du se, hvad der sker, når rapportbrugeren zoomer ind fra et år til dets måneder. Kolonnen **Målantal** opsummeres i visualiseringen. (Indstillingen [Vis elementer uden data](../create-reports/desktop-show-items-no-data.md) er aktiveret for matrixrækker.)

![Diagram, der viser en matrixvisualisering, der afslører, at målet for året 2020 er 270.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

For at undgå denne funktionsmåde anbefaler vi, at du styrer opsummeringen af faktadataene ved hjælp af målinger. En måde at styre opsummeringen på er ved at returnere TOM, når der forespørges om tidsperioder på lavere niveauer. En anden måde, som defineres ved hjælp af nogle avancerede DAX-metoder, er at fordele værdier på tværs af tidsperioder på lavere niveauer.

Overvej følgende målingsdefinition, hvor DAX-funktionen [ISFILTERED](/dax/isfiltered-function-dax) bruges. Der returneres kun en værdi, når kolonnerne **Dato** eller **Måned** ikke er filtreret.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

Målingen **Målantal** bruges nu i følgende matrixvisualisering. Alle månedlige målantal vises som TOMME.

![Diagram, der viser en matrixvisualisering, som afslører, at målet for året 2020 er 270 med tomme månedlige værdier.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>Relater højere detaljeringsniveau (ikke dato)

Der kræves en anden designmetode, når en kolonne, der ikke er en dato, skal relateres fra en tabel af dimensionstypen til en tabel af faktatypen (og den er på et højere detaljeringsniveau end tabellen af dimensionstypen).

Kolonnerne **Kategori** (både fra tabellen **Produkt** og **Mål**) indeholder dubletværdier. Det betyder, at der ikke er nogen "én" til en én til mange-relation. I dette tilfælde skal du oprette en mange til mange-relation. Relationen skal overføre filtre i en enkelt retning – fra tabellen af dimensionstypen til tabellen af faktatypen.

![Diagram, der viser en model af tabellerne Mål og Produkt. De to tabeller relateres i en mange til mange-relation.](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

Lad os nu se på tabelrækkerne.

![Diagram, der viser en model, som indeholder to tabeller: Mål og Produkt. De to kolonner Kategori relateres i en mange til mange-relation.](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

I tabellen **Mål** er der fire rækker: to rækker for hvert målår (2019 og 2020) og to kategorier (Beklædning og Tilbehør). I tabellen **Produkt** er der tre produkter. To tilhører kategorien Beklædning, og én tilhører kategorien Tilbehør. En af farverne for Beklædning er grøn, og de resterende to er blå.

En gruppering af tabelvisualiseringen efter kolonnen **Kategori** fra tabellen **Produkt** giver følgende resultat.

![Diagram, der viser en tabelvisualisering med to kolonner: Kategori og Målantal. Tilbehør er 60, Beklædning er 40, og totalen er 100.](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

Denne visualisering indeholder det rigtige resultat. Lad os se på, hvad der sker, når kolonnen **Farve** fra tabellen **Produkt** bruges til at gruppere målantallet.

![Diagram, der viser en tabelvisualisering med to kolonner: Farve og Målantal. Blå er 100, Grøn er 40, og totalen er 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

Der sker en forkert fremstilling af dataene i visualiseringen. Hvorfor sker det?

Et filter på kolonnen **Farve** fra tabellen **Produkt** resulterer i to rækker. En af rækkerne er for kategorien Beklædning, og den anden er for kategorien Tilbehør. Disse to kategoriværdier overføres som filtre til tabellen **Mål**. Med andre ord, da farven blå bruges af produkter fra to kategorier, bruges _disse kategorier_ til at filtrere målene.

For at undgå denne funktionsmåde anbefaler vi, at du styrer opsummeringen af faktadataene ved hjælp af målinger, som beskrevet tidligere.

Se følgende målingsdefinition. Bemærk, at alle kolonner i tabellen **Produkt**, der er under kategoriniveauet, er testet for filtre.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

Målingen **Målantal** bruges nu i følgende tabelvisualisering. Alle farver for målantal vises som TOMME.

![Diagram, der viser en tabelvisualisering med to kolonner: Farve og Målantal. Blå er TOM, Grøn er TOM, og totalen er 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

Det endelige modeldesign ser ud som følger.

![Diagram, der viser en model med tabellerne Dato og Mål er relateret ved hjælp af en én til mange-relation.](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>Vejledning til relatering af fakta på højere detaljeringsniveau

Når du har brug for at relatere en tabel af dimensionstypen til en tabel af faktatypen, og tabellen af faktatypen gemmer rækker på et højere detaljeringsniveau end rækkerne i tabellen af dimensionstypen, giver vi følgende vejledning:

- For datoer med fakta på højere detaljeringsniveau:
  - I tabellen af faktatypen skal du gemme den første dato i tidsperioden
  - Opret en én til mange-relation mellem tabellen Dato og tabellen af faktatypen
- For fakta på højere detaljeringsniveau:
  - Opret en mange til mange-relation mellem tabellen af dimensionstypen og tabellen af faktatypen
- For begge typer:
  - Styr opsummering ved hjælp af målingslogik. Returner TOM, når kolonnerne af dimensionstypen på et lavere niveau bruges til at filtrere eller gruppere
  - Skjul opsummerede kolonner i tabeller af faktatypen. På denne måde er det kun målinger, der kan bruges til at opsummere tabeller af faktatypen

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Modelrelationer i Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [Forstå, hvad et stjerneskema er, og hvorfor det er vigtigt for Power BI](star-schema.md)
- [Vejledning til fejlfinding af relationer](relationships-troubleshoot.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
