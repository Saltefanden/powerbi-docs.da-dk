---
title: Analysér i Excel til Power BI
description: Analysér Power BI-datasæt i Microsoft Excel
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: contperf-fy20q4
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 01/20/2021
LocalizationGroup: Reports
ms.openlocfilehash: e708e5001e49841d01b60cfc8712d37b990102f2
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687114"
---
# <a name="analyze-in-excel"></a>Analysér i Excel
Med **Analysér i Excel** kan du hente Power BI-datasæt til Excel og derefter få vist og interagere med dem ved hjælp af pivottabeller, diagrammer, udsnit og andre Excel-funktioner. Hvis du vil bruge **Analysér i Excel**, skal du først downloade funktionen fra Power BI, installere den og derefter vælge et eller flere datasæt, der skal bruges i Excel. 

![Analysér i Excel](media/service-analyze-in-excel/analyze-excel-00a.png)

I denne artikel kan du se, hvordan du installerer og bruger Analysér i Excel, beskriver dens begrænsninger og giver derefter nogle af de næste trin. Her er, hvad du skal lære:

* [Installere Analysér i Excel](#install-analyze-in-excel)
* [Oprette forbindelse til Power BI-data](#connect-to-power-bi-data)
* [Analysere dataene med Excel](#use-excel-to-analyze-the-data)
* [Gemme og dele din projektmappe](#saving-and-sharing-your-new-workbook)
* [Krav](#requirements)

Lad os komme i gang og få startet installationsprocessen.

## <a name="install-analyze-in-excel"></a>Installere Analysér i Excel

Du skal installere **Analysér i Excel** fra links, der er angivet i Power BI-tjenesten. Power BI registrerer den version af Excel, du har på din computer, og henter automatisk den relevante version (32-bit eller 64-bit). Du kan logge på Power BI-tjeneste ved hjælp af følgende link:

* [Log på Power BI](https://app.powerbi.com)

Når du er logget på, og Power BI-tjeneste kører i din browser, skal du vælge **flere indstillinger** (...) i øverste højre hjørne og derefter vælge **Hent > Analysér i Excel-opdateringer**. Dette menupunkt gælder for nye installationer af opdateringer til Analysér i Excel.

![Hent Analysér i Excel fra Power BI Start](media/service-analyze-in-excel/analyze-excel-02.png)

Du kan også navigere i Power BI-tjeneste til et datasæt, du vil analysere, og vælge elementet **Flere indstillinger** for et datasæt, en rapport eller et andet Power BI-element. I den menu, der vises, skal du vælge indstillingen **Analysér i Excel** som vist på følgende billede.

![Analysér i Excel fra datasæt](media/service-analyze-in-excel/analyze-excel-01.png)

Uanset hvad registrerer Power BI, om du har installeret Analysér i Excel. Hvis ikke, bliver du bedt om at downloade. 

![Nødvendige opdateringer](media/service-analyze-in-excel/analyze-excel-03.png)

Når du vælger at downloade, registrerer Power BI den version af Excel, du har installeret, og downloader den rette version af installationsprogrammet til Analysér i Excel. Du kan se status nederst i din browser eller der, hvor browseren viser overførselsstatus. 

![Download af opdateringer](media/service-analyze-in-excel/analyze-excel-04.png)

Når overførslen er fuldført, skal du køre installationsprogrammet (.msi) for at installere Analysér i Excel. Navnet på installationsprocessen er forskellig fra Analysér i Excel. Navnet vil være **Microsoft Analysis Services OLE DB-provider** som vist på følgende billede eller noget lignende.

![Opdaterer installationen af Analysis Services OLE DB Provider](media/service-analyze-in-excel/analyze-excel-05.png)

Når det er fuldført, er du klar til at vælge en rapport i Power BI-tjenesten (eller et andet Power BI-dataelement, f.eks. et datasæt) og derefter analysere det i Excel.

## <a name="connect-to-power-bi-data"></a>Opret forbindelse til Power BI-data

I Power BI-tjenesten skal du navigere til det datasæt eller den rapport, du vil analysere i Excel, og derefter skal du gøre følgende:

1. Vælg menuen **Flere indstillinger**.

1. Vælg **Analysér i Excel** fra de menupunkter, der vises.

    På følgende billede kan du se, hvordan du vælger en rapport.

    ![Opdateringer installeres](media/service-analyze-in-excel/analyze-excel-06.png)
    
    >[!NOTE]
    >Husk, at hvis du vælger Analysér i Excel fra en rapportmenu, er det rapportens underliggende datasæt, der overføres til Excel.

    Power BI-tjenesten opretter derefter en Excel-fil med det datasæt, der er designet (og struktureret) til brug med **Analysér i Excel**, og starter downloadprocessen i din browser.
    
    ![Download af Excel-filen](media/service-analyze-in-excel/analyze-in-excel-download-xlsx.png)

    Filnavnet svarer til det datasæt (eller den rapport eller anden datakilde), som det er afledt af. Så hvis rapporten hedder *Kvartalsrapport*, hedder den downloadede fil **Kvartalsrapport.xlsx**.

    >[!Note]
    >Der downloades nu en Excel-fil i stedet for en ODC-fil i Analysér i Excel. Det gør det muligt at beskytte data, som eksporteres fra Power BI. Den hentede Excel-fil arver følsomhedsmærkatet for det datasæt, der er valgt til Analysér i Excel.

3. Start Excel-filen.

    >[!NOTE]
    >Første gang, du åbner filen, kan du blive nødt til at **aktivere redigering** og derefter **aktivere indhold**, afhængigt af dine indstillinger for [Beskyttet visning](https://support.microsoft.com/en-gb/office/what-is-protected-view-d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653?ui=en-us&rs=en-gb&ad=gb) og [Dokument, der er tillid til](https://support.microsoft.com/en-us/office/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53).
    >
    >![Skærmbillede af banneret Beskyttet visning aktiverer redigering](media/service-analyze-in-excel/protected-view-enable-editing-banner.png)
    >
    >![Skærmbillede af banneret Dokument, der er tillid til, aktiverer indhold](media/service-analyze-in-excel/trusted-document-enable-content-banner.png)

Når du bruger Excel til at analysere Power BI ved hjælp af en pivottabel, udvider Power BI nedarvning af følsomhedsmærkaten til Excel. En følsomhedsmærkat, der anvendes på et Power BI-datasæt, anvendes automatisk på Excel-filen, når du opretter en pivottabel i Excel. 

Hvis mærkaten på datasættet senere ændres til at være mere restriktiv, opdateres den mærkat, der anvendes på Excel-filen, automatisk efter dataopdatering i Excel. Hvis datasættet ændres, så det bliver mindre restriktivt, sker der ingen nedarvning eller opdatering af mærkater.

Følsomhedsmærkater i Excel, der er blevet angivet manuelt, tilsidesættes ikke automatisk af datasættets mærkat. Hvis en Excel-fil har en manuelt angivet følsomhedsmærkat, vises der et politiktip med en anbefaling om at opgradere mærkaten. 

Du kan få flere oplysninger i [Se hvordan følsomhedsmærkater anvendes i Power BI](../admin/service-security-apply-data-sensitivity-labels.md).


## <a name="use-excel-to-analyze-the-data"></a>Analyser dataene med Excel

Når du har aktiveret redigering og indhold, viser Excel en tom **pivottabel** og **feltliste** fra det Power BI-datasæt, der er klar til at blive analyseret.

![Excel med data forbundet](media/service-analyze-in-excel/analyze-in-excel-connected.png)

Excel-filen indeholder en MSOLAP-forbindelsesstreng, der opretter forbindelse til dit datasæt i Power BI. Når du analyserer eller arbejder med dataene, forespørger Excel på dette datasæt i Power BI og returnerer resultaterne til Excel. Hvis dette datasæt opretter forbindelse til en direkte datakilde ved hjælp af DirectQuery, forespørger Power BI på datakilden og returnerer resultatet til Excel.

Nu, hvor der er oprettet forbindelse til dataene i Power BI, kan du oprette pivottabeller og diagrammer og analysere dette datasæt på samme måde, som du ville arbejde med et lokalt datasæt i Excel.

**Analysér i Excel** er især nyttigt i forbindelse med datasæt og rapporter, der opretter forbindelse til følgende datakilder:

* Databaserne *Analysis Services Tabular* eller *Multidimensional*
* Power BI Desktop-filer eller Excel-projektmapper med datamodeller med modelmålinger, der er oprettet ved hjælp af DAX (Data Analysis Expressions).

> [!IMPORTANT]
> Brug af **Analysér i Excel** fremviser alle data på detaljeniveau for alle brugere med tilladelse til datasættet.

Der er en række ting, du skal overveje, når du begynder at bruge Analysér i Excel, hvilket kan kræve et ekstra trin eller to for at afstemme. Disse muligheder er beskrevet i de følgende afsnit. 


### <a name="sign-in-to-power-bi"></a>Log på Power BI
Selvom du er logget på Power BI i din browser, kan du blive bedt om at logge på Power BI med din Power BI-konto, første gang du åbner en ny Excel-fil i Excel. Dette godkender forbindelsen fra Excel til Power BI.

### <a name="users-with-multiple-power-bi-accounts"></a>Brugere med flere Power BI-konti
Nogle brugere har flere Power BI-konti. Hvis det er dig, er du muligvis logget på Power BI med én konto, men din anden konto har adgang til det datasæt, der bruges i Analysér i Excel. I dette tilfælde kan du få vist fejlen **Forbudt** eller en logonfejl, når du forsøger at få adgang til et datasæt, der bruges i en projektmappe i Analysér i Excel.

Sker dette, får du mulighed for at logge på igen, og på dette tidspunkt kan du så logge på med den Power BI-konto, der har adgang til datasættet, som Analysér i Excel skal have adgang til. Du kan også vælge dit navn på det øverste bånd i Excel, som identificerer den konto, der er logget ind på i øjeblikket. Log af, og log på igen med den anden konto.


## <a name="saving-and-sharing-your-new-workbook"></a>Gem og del din nye projektmappe

Du kan **gemme** den Excel-projektmappe, du opretter med Power BI-datasættet, som alle andre projektmapper. Du kan dog ikke publicere eller indlæse projektmappen i Power BI igen, fordi du kun kan publicere eller importere projektmapper til Power BI, som har data i tabeller, eller som har en datamodel. Da den nye projektmappe blot har forbindelse til datasættet i Power BI, vil du køre i cirkler, hvis du udgiver eller importerer den i Power BI!

Når din projektmappe er gemt, kan du dele den med andre Power BI-brugere i din organisation. 

Når en bruger, som du har delt din projektmappe med, åbner den, får vedkommende vist dine pivottabeller og data, sådan som de så ud, da projektmappen sidst blev gemt, hvilket muligvis ikke er den nyeste version af dataene. For at få de nyeste data skal brugerne bruge knappen **Opdater** på båndet **Data**. Og da projektmappen er forbundet med et datasæt i Power BI, skal brugere, der forsøger at opdatere projektmappen, logge på Power BI og installere Excel-opdateringerne, første gang de forsøger at opdatere ved hjælp af denne metode.

Da brugere får brug for at opdatere datasættet, og opdatering for eksterne forbindelser ikke understøttes i Excel Online, anbefales det, at brugere åbner projektmappen i desktop-versionen af Microsoft Excel på deres egen computer.

> [!NOTE]
> Administratorer for Power BI-lejere kan bruge *Power BI-administrationsportalen* til at deaktivere brugen af **Analysér i Excel** med datasæt i det lokale miljø, der er placeret på databaser i Analysis Services (AS). Når denne indstilling er deaktiveret, er **Analysér i Excel** deaktiveret for AS-databaser, men er fortsat tilgængelige til brug sammen med andre datasæt.


## <a name="other-ways-to-access-power-bi-datasets-from-excel"></a>Andre måder at få adgang til Power BI-datasættet fra Excel på
Brugere med bestemte Office-varenumre kan også oprette forbindelse til Power BI-datasæt i Excel ved hjælp af funktionen **Hent data** i Excel. Hvis dit varenummer ikke understøtter denne funktion, vises menupunktet **Hent data** ikke.

Fra menuen **Data** på båndet skal du vælge **Hent data > Fra Power BI-datasæt** som vist på følgende billede.

![Brug af menuen Hent data](media/service-analyze-in-excel/analyze-excel-10.png)

Der vises en rude, hvor du kan gennemse datasæt, som du har adgang til, se, om datasæt er certificerede eller promoverede, og bestemme, om der er anvendt databeskyttelsesetiketter på disse datasæt. 

Du kan finde flere oplysninger om, hvordan du henter data til Excel på denne måde, under [Opret en pivottabel ud fra Power BI-datasæt](https://support.office.com/article/31444a04-9c38-4dd7-9a45-22848c666884) i dokumentationen til Excel.

Du kan også få adgang til **udvalgte tabeller** i Excel i galleriet **Datatyper**. Hvis du vil vide mere om de udvalgte tabeller, og hvordan du får adgang til dem, kan du se [Få adgang til udvalgte Power BI-tabeller i Excel (prøveversion)](service-excel-featured-tables.md).

## <a name="requirements"></a>Krav
Her er nogle krav til brug af **Analysér i Excel**:

* **Analysér i Excel** understøttes for Microsoft Excel 2010 SP1 og nyere.
* Pivottabeller i Excel understøtter ikke træk og slip-sammenlægning af numeriske felter. Dit datasæt i Power BI *skal have foruddefinerede målinger*. Læs om [oprettelse af målinger](../transform-model/desktop-measures.md).
* Nogle organisationer har muligvis gruppepolitikregler, der forhindrer installation af de krævede **Analysér i Excel**-opdateringer i Excel. Hvis du ikke kan installere opdateringerne, skal du kontakte din administrator.
* **Analysér i Excel** kræver, at datasættet er i Power BI Premium, eller at brugeren har en Power BI Pro-licens. Hvis du vil vide mere om forskellene i funktionaliteten mellem de forskellige Power BI-licenstyper, skal du se _Sammenligning af Power BI-funktioner_ i afsnittet [Power BI-priser](https://powerbi.microsoft.com/pricing/).
* Brugere kan oprette forbindelse til datasæt via Analysér i Excel, hvis de har læsetilladelse til det underliggende datasæt.  En bruger kan have denne tilladelse på nogle få måder, f. eks. at have rollen i arbejdsområdet, der indeholder datasættet eller har oprettet tilladelse til et datasæt i et arbejdsområde eller i en app, der indeholder datasættet. Læs mere om [tilladelsen Opret for datasæt](../connect-data/service-datasets-build-permissions.md).
* Gæstebrugere kan ikke bruge **Analysér i Excel** til datasæt, der sendes fra (fra) en anden lejer. 
* **Analysér i Excel** er en Power bi-tjeneste funktion, som ikke er tilgængelig i Power BI-rapportserver eller Power bi Embedded. 
* **Analysér i Excel** understøttes kun på computere, der kører Microsoft Windows.


Hvis du har brug for at fjerne funktionen **Analysér i Excel** , skal du bruge systemindstillingen **Tilføj eller fjern programmer** på computeren.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

- Sikkerhed på rækkeniveau (RLS) understøttes for Analysér i Excel. RLS gennemtvinges på datamodel niveau og anvendes altid til alle brugere, der har adgang til data i rapporten. Læs mere om [sikkerhed på rækkeniveau](../admin/service-admin-rls.md).
- Når du bruger Analysér i Excel, kan du i nogle tilfælde få et uventet resultat, eller funktionen fungerer måske ikke som forventet. Se [fejlfinding i forbindelse med Analysér i Excel](desktop-troubleshooting-analyze-in-excel.md) , hvis du har løsninger til almindelige problemer.

## <a name="next-steps"></a>Næste trin

Du vil måske også være interesseret i følgende artikler:

* [Brug tværgående detaljeadgang i rapport i Power BI Desktop](../create-reports/desktop-cross-report-drill-through.md)
* [Brug af udsnitsværktøjer i Power BI Desktop](../visuals/power-bi-visualization-slicers.md)
* [Fejlfinding af Analysér i Excel](desktop-troubleshooting-analyze-in-excel.md)
* [Få adgang til Power BI-tabeller i Excel (prøveversion)](service-excel-featured-tables.md).
* [Sådan anvendes følsomhedsmærkater i Power BI](../admin/service-security-apply-data-sensitivity-labels.md)
