---
title: Udfør almindelige forespørgselsopgaver i Power BI Desktop
description: Udfør almindelige forespørgselsopgaver i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/09/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 931c500cd2c2dbbf750eb3699ac5290a2977c21b
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/29/2020
ms.locfileid: "91526254"
---
# <a name="perform-common-query-tasks-in-power-bi-desktop"></a>Udfør almindelige forespørgselsopgaver i Power BI Desktop

I vinduet Power Query-editor i Power BI Desktop er der nogle få opgaver, der udføres jævnligt. Denne artikel beskriver disse opgaver og indeholder links til flere oplysninger.

Følgende almindelige forespørgselsopgaver vises her:

* Opret forbindelse til data
* Form og kombiner data
* Gruppér rækker
* Pivoter kolonner
* Opret brugerdefinerede kolonner
* Forespørgselsformler

Vi vil bruge dataforbindelser til at udføre disse opgaver. Du kan hente eller oprette forbindelse til disse data, hvis du vil gennemgå opgaverne selv.

Den første dataforbindelse er en [Excel-projektmappe](https://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx), som du kan downloade og gemme lokalt. Den anden er en webressource, der også bruges i andre Power BI Desktop-artikler:

<https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/>

De almindelige forespørgselsopgaver begynder med de trin, der er nødvendige for at oprette forbindelse til begge disse datakilder.

## <a name="connect-to-data"></a>Opret forbindelse til data

Hvis du vil oprette forbindelse til data i Power BI Desktop, skal du vælge **Hjem** og derefter **Hent data**. Der vises en menu med de mest almindelige datakilder i Power BI Desktop. Vælg knappen **Mere** nederst i menuen for at få vist en komplet liste over de datakilder, der kan oprettes forbindelse til i Power BI Desktop. Du kan finde flere oplysninger i [Datakilder i Power BI Desktop](../connect-data/desktop-data-sources.md).

![Menuen med de mest almindelige datatyper, knappen Hent data i Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

Du kommer i gang ved at vælge **Excel**, angive den Excel-projektmappe, der er nævnt tidligere, og derefter vælge **Åbn**. Projektmappen undersøges, og derefter vises de data, der blev fundet, i dialogboksen **Navigator**, efter at du har valgt en tabel.

![Excel-datakilde, dialogboksen Navigator, Hent data, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

Du kan vælge **Transformér data** for at redigere, justere eller *forme* dataene, før du indlæser dem i Power BI Desktop. Redigering er især nyttig, når du arbejder med store datasæt, som du vil reducere før indlæsning.

Det er lige så nemt at oprette forbindelse til andre datatyper. Du vil også gerne oprette forbindelse til en webressource. Vælg **Hent data** > **Mere**, og vælg derefter **Andet** > **Web** > **Opret forbindelse**.

![Webdatakilde, dialogboksen Hent data, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

Dialogboksen **Fra web** vises, hvor du kan indtaste URL-adressen til websiden.

![Dialogboksen Fra web, webdatakilde, Hent data, Power BI Desktop](media/desktop-common-query-tasks/datasources_fromwebbox.png)

Vælg **OK**. På samme måde som tidligere undersøger Power BI Desktop websidedataene og viser indstillinger for eksempelvisning i dialogboksen **Navigator**. Når du vælger en tabel, vises der et eksempel på dataene.

Det samme gælder for andre dataforbindelser. Hvis godkendelse er nødvendig for at oprette en dataforbindelse, bliver du bedt om at angive de relevante legitimationsoplysninger i Power BI Desktop.

Hvis du vil have en trinvis vejledning til, hvordan du opretter forbindelse til data i Power BI Desktop, skal du se [Opret forbindelse til data i Power BI Desktop](../connect-data/desktop-connect-to-data.md).

## <a name="shape-and-combine-data"></a>Form og kombiner data

Du kan nemt forme og kombinere data ved hjælp af Power Query-editor. Dette afsnit indeholder nogle eksempler på, hvordan du kan forme data. Hvis du vil have en mere komplet demonstration af, hvordan du former og kombinerer data, skal du se [Form og kombiner data med Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md).

I det forrige afsnit tilsluttede vi to datasæt – en Excel-projektmappe og en webressource. Når dataene er indlæst i Power Query-editor, skal du vælge websideforespørgslen blandt de tilgængelige forespørgsler i ruden **Forespørgsler**, som vist her:

![Ruden Forespørgsler, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

Når du former data, konverterer du en datakilde til den form og det format, der opfylder dine behov.

I Power Query-editor kan du finde mange af kommandoerne på båndet og i en kontekstafhængig genvejsmenu. Når du f.eks. højreklikker på en kolonne, kan du bruge den viste menu til at fjerne kolonnen. Du kan også markere kolonnen og derefter vælge knappen **Fjern kolonner** på fanen **Hjem** på båndet.

![Kommandoen Fjern kolonner, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

Du kan forme dataene på mange andre måder i denne forespørgsel. Du kan fjerne et vilkårligt antal rækker fra toppen eller bunden. Du kan også tilføje kolonner, dele kolonner, erstatte værdier og udføre andre formningsopgaver. Med disse funktioner kan du få Power Query-editor til at hente data, på den måde du ønsker det.

## <a name="group-rows"></a>Gruppér rækker

Du kan gruppere værdierne fra flere rækker i én enkelt værdi i Power Query-editor. Denne funktion kan være nyttig, når du opsummerer det antal produkter, der tilbydes, det samlede salg eller antallet af studerende.

I dette eksempel grupperer du rækker i et datasæt med uddannelsestilmeldinger. Dataene er fra Excel-projektmappen. De er blevet formet i Power Query-editor, så du kan få vist de kolonner, du har brug for, omdøbe tabellen og foretage nogle andre transformeringer.

Lad os finde ud af, hvor mange organisationer hver stat har. (Institutioner kan omfatte skoledistrikter, andre uddannelsesinstitutioner, f.eks. regionale distrikter) og meget mere. Vælg kolonnen **Agency ID - NCES Assigned \[District\] Latest available year**, og vælg derefter knappen **Gruppér efter** på fanen **Transformér** eller fanen **Hjem** på båndet. (**Gruppér efter** er tilgængelig på begge faner).

![Skærmbillede, der viser, hvordan rækker skal grupperes i en tabel.](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

Dialogboksen **Gruppér efter** vises. Når rækker grupperes i Power Query-editor, oprettes der en ny kolonne, som resultaterne fra **Gruppér efter** placeres i. Du kan justere handlingen **Gruppér efter** på følgende måder:

1. Den ikke-navngivne rulleliste angiver den kolonne, der skal grupperes. Power Query-editor gør den valgte kolonne til standardværdien, men du kan ændre den til en hvilken som helst kolonne i tabellen.
2. **Nyt kolonnenavn**: Power Query-editor foreslår et navn til den nye kolonne, der er baseret på den handling, som anvendes på den kolonne, der grupperes. Du kan dog også selv vælge et navn til den nye kolonne.
3. **Handling**: Du kan vælge den handling, som Power Query-editor anvender, f.eks. **Sum**, **Median** eller **Antal entydige rækker**. Standardværdien er **Antal rækker**.
4. **Tilføj gruppering** og **Tilføj sammenlægning**: Disse knapper er kun tilgængelige, hvis du vælger indstillingen **Avanceret**. I en enkelt handling kan du foretage grupperingshandlinger (**Gruppér efter**) på mange kolonner og oprette flere aggregeringer ved hjælp af disse knapper. Der oprettes en ny kolonne i Power Query-editor (ud fra dine valg i dette vindue), som er baseret på flere kolonner.

Vælg **Tilføj gruppering** eller **Tilføj aggregering** for at føje flere grupperinger eller aggregeringer til en handling af typen **Gruppér efter**. Hvis du vil fjerne en gruppering eller aggregering, skal du vælge ellipseikonet ( **...** ) til højre for rækken og derefter **Slet**. Prøv handlingen **Gruppér efter** ved hjælp af standardværdierne for at se, hvad der sker.

![Skærmbillede, der viser dialogboksen Gruppér efter med Tilføj gruppering og Tilføj sammenlægning vist.](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

Når du vælger **OK**, udføres handlingen **Gruppér efter**, og resultaterne returneres. Vi kan se, at Ohio, Texas, Illinois og Californien hver især har over 1.000 institutioner.

![Kolonnen Antal, handlingen Gruppér efter, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

Og med Power Query-editor kan du altid fjerne den seneste formningshandling. Vælg **X** under **Anvendte trin** i ruden **Forespørgselsindstillinger** ud for det trin, der er fuldført for nylig. Du kan prøve at eksperimentere. Hvis du ikke kan lide resultatet, kan du fortryde trinnet, indtil dataene vises, som du vil have det, i Power Query-editor.

## <a name="pivot-columns"></a>Pivoter kolonner

Du kan pivotere kolonner, og du kan også oprette en tabel med de aggregerede værdier for hver entydig værdi i en kolonne. Hvis du f.eks. vil vide, hvor mange forskellige produkter du har i hver produktkategori, kan du hurtigt oprette en tabel, som gør netop det.

Lad os se på et eksempel. Tabellen **Products_by_Categories** nedenfor er blevet formet, så et produkt kun vises én gang (efter navn), og hvilken kategori det tilhører. Hvis du vil oprette en ny tabel, som viser antallet af produkter i hver kategori (baseret på kolonnen **CategoryName**), skal du markere kolonnen og derefter vælge **Transformér** > **Pivotkolonne**.

![Kommandoen Pivotkolonne, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

Dialogboksen **Pivotkolonne** vises, så du kan se, hvilken kolonnes værdier der vil blive brugt til at oprette nye kolonner (1). Hvis det ønskede kolonnenavn for **CategoryName** ikke vises, skal du vælge det på rullelisten. Når du udvider **Avancerede indstillinger** (2), kan du vælge den funktion, der skal anvendes på de aggregerede værdier (3).

![Dialogboksen Pivotkolonne, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

Når du vælger **OK**, vises tabellen i Power Query-editor ifølge de indstillinger, du har angivet i dialogboksen **Pivotkolonne**.

![Resultat i pivotkolonne, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>Opret brugerdefinerede kolonner

I Power Query-editor kan du oprette brugerdefinerede formler, der fungerer på flere kolonner i tabellen. Derefter kan du placere resultaterne af disse formler i en ny (brugerdefineret) kolonne. Power Query-editor gør det nemt at oprette brugerdefinerede kolonner.

Med Excel-projektmappedataene i Power Query-editor skal du gå til fanen **Tilføj kolonne** på båndet og derefter vælge **Brugerdefineret kolonne**.

![Kommandoen Tilføj brugerdefineret kolonne, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

Følgende dialogboks vises. I dette eksempel opretter vi en brugerdefineret kolonne med navnet *Percent ELL*, som beregner procentdelen af alle de studerende, der er ELL (English Language Learners).

![Dialogboksen Brugerdefineret kolonne, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

Som med alle andre anvendte trin i Power Query-editor kan du slette trinnet, hvis den nye brugerdefinerede kolonne ikke indeholder de data, du søger efter. Vælg **X** ud for trinnet **Anvendt brugerdefineret** under **Anvendte trin** i ruden **Forespørgselsindstillinger** ud for det trin, der er fuldført for nylig.

![Anvendte trin, ruden Forespørgselsindstillinger, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>Forespørgselsformler

Du kan redigere de trin, som oprettes i Power Query-editor. Du kan også oprette brugerdefinerede formler, som giver dig mulighed for at oprette forbindelse til og forme dine data mere præcist. Når der udføres en handling på data i Power Query-editor, vises den formel, der er tilknyttet handlingen, på formellinjen. Du kan få vist formellinjen ved at vælge **Formellinje** på fanen **Vis** på båndet.

![Indstillingen Formellinje, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_formulabar.png)

Alle anvendte trin for hver forespørgsel bevares som tekst i Power Query-editor, så du kan se eller redigere dem. Du kan få vist eller redigere teksten for en hvilken som helst forespørgsel ved hjælp af **Avanceret editor**. Du skal blot vælge **Vis** og derefter **Avanceret editor**.

![Kommandoen Avanceret editor, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

Her kan du se, hvordan **Avanceret editor** ser ud med de forespørgselstrin, der er tilknyttet den viste forespørgsel **USA\_StudentEnrollment**. Disse trin oprettes på det formelsprog i Power-forespørgsel, som ofte kaldes *M*. Du kan finde flere oplysninger i [Få mere at vide om formler i Power Query](https://support.office.com/article/learn-about-power-query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f). Hvis du vil se selve sprogspecifikationen, skal du downloade [sprogspecifikationen for Power Query M](/powerquery-m/power-query-m-language-specification).

![Dialogboksen Avanceret editor, Power Query-editor, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

Der findes en lang række formelkategorier i Power BI Desktop. Du kan finde flere oplysninger og en komplet liste over alle formler i Power Query-editor ved at gå til [Reference til M-funktionen i Power Query-editor](/powerquery-m/power-query-m-function-reference).

## <a name="next-steps"></a>Næste trin

Du kan gøre mange forskellige ting med Power BI Desktop. Du kan finde flere oplysninger om funktionerne i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Datakilder i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Opret forbindelse til data i Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Udform og kombiner data med Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
