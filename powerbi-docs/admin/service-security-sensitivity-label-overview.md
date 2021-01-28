---
title: Følsomhedsmærkater fra Microsoft Information Protection i Power BI
description: Få mere at vide om, hvordan følsomhedsmærkater fra Microsoft Information Protection fungerer i Power BI
author: paulinbar
ms.author: painbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: conceptual
ms.custom: contperf-fy21q2
ms.date: 12/20/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 52c3d5dea171f34fbbe5133eda6fd51fd471bbd4
ms.sourcegitcommit: 1872a167d1e4d731ad00cf8a6d951c31aa54bcce
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/28/2021
ms.locfileid: "98925668"
---
# <a name="sensitivity-labels-in-power-bi"></a>Følsomhedsmærkater i Power BI

I denne artikel beskrives funktionaliteten af Microsoft Information Protection-følsomhedsmærkater i Power BI.

Du kan finde oplysninger om aktivering af følsomhedsmærkater i din lejer, inklusive licenskrav og forudsætninger, under [Aktivér følsomhedsmærkater i Power BI](service-security-enable-data-sensitivity-labels.md).

Du kan finde oplysninger om, hvordan du anvender følsomhedsmærkater på Power BI-indhold og -filer i [Sådan anvendes følsomhedsmærkater i Power BI](./service-security-apply-data-sensitivity-labels.md).

>[!NOTE]
>Understøttelse af følsomhedsmærkater i Power BI Desktop er i øjeblikket en prøveversion.

## <a name="introduction"></a>Introduktion

Microsoft Information Protections følsomhedsmærkater giver brugerne en nem måde at klassificere kritisk indhold i Power BI på uden at gå på kompromis med produktiviteten eller muligheden for at samarbejde. De kan anvendes både i Power BI Desktop (prøveversion) og Power BI-tjenesten, hvilket gør det muligt at beskytte dine følsomme data fra det tidspunkt, hvor du først begynder at udvikle dit indhold, til de tilgås fra Excel via en direkte forbindelse. Følsomhedsmærkater bevares, når du flytter dit indhold frem og tilbage mellem Desktop og tjenesten i form af .pbix-filer.

I Power BI-tjenesten kan følsomhedsmærkater kun anvendes på datasæt, rapporter, dashboards og dataflow. Når data, der er forsynet med mærkater, forlader Power BI, enten via eksport til Excel, PowerPoint, PDF eller .pbix-filer eller via andre understøttede eksportscenarier, f.eks. Analysér i Excel eller pivottabeller i Excel med direkte forbindelse, anvender Power BI automatisk mærkaten på den eksporterede fil og beskytter den i henhold til indstillingerne for mærkatens filkryptering. På denne måde forbliver dine følsomme data beskyttet, selv når de forlader Power BI.

Desuden kan følsomhedsmærkater anvendes på .pbix-filer i Power BI Desktop, så dine data og dit indhold er sikre, når de deles uden for Power BI (f.eks. så det kun er brugere i din organisation, der kan åbne en fortrolig .pbix, der er blevet delt eller vedhæftet i en mail), også selvom de er blevet publiceret i Power BI-tjenesten. Du kan finde flere oplysninger under [Begræns adgang til indhold ved hjælp af følsomhedsmærkater for at anvende kryptering](/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide).

Følsomhedsmærkater, der anvendes på rapporter, dashboards, datasæt og dataflows, er synlige fra mange forskellige steder i Power BI-tjenesten. Følsomhedsmærkater på rapporter og dashboards er også synlige i Power BI iOS- og Android-mobilapps og i integrerede visualiseringer. I Desktop kan du se følsomhedsmærkater på statuslinjen.

Der er en [målepunktsrapport for beskyttelse](service-security-data-protection-metrics-report.md) i Power BI-administrationsportalen, der giver Power BI-administratorer fuld synlighed over de følsomme data i Power BI-lejeren. Derudover omfatter Power BI-overvågningsloggene oplysninger om følsomhedsmærkater for aktiviteter som f.eks. anvendelse, fjernelse og ændring af mærkater samt om aktiviteter som f.eks. visning af rapporter, dashboards, osv., der giver Power BI og sikkerhedsadministratorer synlighed over forbruget af følsomme data med det formål at overvåge og undersøge samt i forbindelse med sikkerhedsadvarsler.

## <a name="important-considerations"></a>Vigtige overvejelser

I Power BI-tjenesten påvirker forsyning med følsomhedsmærkater **ikke** adgangen til indhold. Adgang til indhold i tjenesten administreres kun af Power BI-tilladelser. Selvom mærkaterne er synlige, anvendes eventuelle tilknyttede krypteringsindstillinger (konfigureret enten i [Microsoft 365 Security Center](https://security.microsoft.com/) eller [Microsoft 365 Compliance Center](https://compliance.microsoft.com/)) ikke. De anvendes kun på data, der forlader tjenesten via en understøttet eksportsti, f.eks. eksportér til Excel, PowerPoint eller PDF, og download til .pbix.

I Power BI Desktop (prøveversion) påvirker følsomhedsmærkater med krypteringsindstillinger **ikke** adgangen til indhold. Hvis en bruger ikke har tilstrækkelige [tilladelser](#power-bi-desktop-preview) i henhold til krypteringsindstillingerne for følsomhedsmærkaten på .pbix-filen, kan vedkommende ikke åbne filen. Når du gemmer dit arbejde, vil alle tilføjede følsomhedsmærkater og deres tilknyttede krypteringsindstillinger desuden blive anvendt på den gemte .pbix-fil i Desktop.

Følsomhedsmærkater og filkryptering anvendes **ikke** for eksportstier, der ikke understøttes. Power BI-administratoren kan blokere eksport fra eksportstier, der ikke understøttes.

>[!NOTE]
> Brugere, der har fået adgang til en rapport, bliver tildelt adgang til hele det underliggende datasæt, medmindre [sikkerhed på rækkeniveau](./service-admin-rls.md) begrænser deres adgang. Rapportforfattere kan klassificere og navngive rapporter ved hjælp af følsomhedsmærkater. Hvis følsomhedsmærkaten har beskyttelsesindstillinger, anvender Power BI disse beskyttelsesindstillinger, når rapportdataene forlader Power BI via en understøttet eksportsti, f.eks. eksportér til Excel, PowerPoint eller PDF, eller download til .pbix, og **Gem** (Desktop). Kun autoriserede brugere kan åbne beskyttede filer.

### <a name="supported-export-paths"></a>Understøttede eksportstier
Anvendelse af følsomhedsmærkater og deres tilknyttede beskyttelse af data, der forlader Power BI-tjenesten, understøttes i øjeblikket for følgende eksportstier:
* Eksportér til Excel, PDF-filer (kun tjenesten) og PowerPoint.
* Analysér i Excel fra Power BI-tjenesten, der udløser hentning af en Excel-fil med en direkte forbindelse til et Power BI-datasæt.
* Pivottabel i Excel med en direkte forbindelse til et Power BI-datasæt for brugere med M365 E3 og nyere.
* Download til .pbix (tjenesten)

>[!NOTE]
>Hvis den downloadede rapport og dens datasæt har forskellige mærkater, vil den mest restriktive mærkat blive anvendt på .pbix-filen, når du bruger **Download .pbix** i Power BI-tjenesten. 

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Sådan fungerer følsomhedsmærkater i Power BI

Når du anvender en følsomhedsmærkat på Power BI-indhold og -filer, svarer det til at anvende et tag på den pågældende ressource, hvilket har følgende fordele:
* **Kan tilpasses** – Du kan oprette kategorier for forskellige niveauer af følsomt indhold i din organisation, f.eks. Personlig, Offentlig, Generelt, Fortrolig og Meget fortroligt.
* **Klartekst** – Da mærkater er i klartekst, er det nemt for brugerne at forstå, hvordan de skal behandle indholdet i henhold til retningslinjerne for følsomhedsmærkater.
* **Fast** – Når en følsomhedsmærkat er blevet anvendt på indhold, følger den dette indhold, når det eksporteres til Excel-, PowerPoint- og PDF-filer, når det downloades til .pbix, eller når det gemmes (i Desktop), og mærkaten bliver grundlaget for anvendelse og håndhævelse af politikker.

Her er et hurtigt eksempel på, hvordan en følsomhedsmærkat i Power BI kan fungere. På billedet nedenfor kan du se, hvordan der anvendes en følsomhedsmærkat i en rapport i Power BI-tjenesten, derefter hvordan dataene fra rapporten eksporteres til en Excel-fil, og til sidst hvordan følsomhedsmærkaten og dens beskyttelse forbliver i den eksporterede fil.

![Animeret GIF, der viser følsomhedsmærkaternes anvendelse og fastholdelse](media/service-security-sensitivity-label-overview/ApplyLabelandProtection.gif)

De følsomhedsmærkater, du anvender på indhold, bevares og flyttes sammen med indholdet, efterhånden som det bruges og deles i hele Power BI. Du kan bruge denne mærkning til at generere forbrugsrapporter og se aktivitetsdata for dit følsomme indhold.

## <a name="sensitivity-labels-in-power-bi-desktop-preview"></a>Følsomhedsmærkater i Power BI Desktop (prøveversion)

Der kan også anvendes følsomhedsmærkater i Power BI Desktop. Det gør det muligt at beskytte dine data fra det tidspunkt, hvor du først begynder at udvikle dit indhold. Når du gemmer dit arbejde i Desktop, anvendes den følsomhedsmærkat, du har anvendt, sammen med eventuelle tilknyttede krypteringsindstillinger, på den resulterende .pbix-fil. Hvis mærkaten indeholder krypteringsindstillinger, er filen derfor beskyttet, uanset hvorend den sendes. Det er kun dem, der har de [nødvendige RMS-tilladelser](#power-bi-desktop-preview), som kan åbne den.

>[!NOTE]
>* I denne prøveversion kan nogle begrænsninger være gældende. Se [Begrænsninger](#limitations).
>* Hvis du vil kunne bruge følsomhedsmærkater i Power BI Desktop, skal du først [aktivere prøveversionsfunktionen Information Protection](service-security-apply-data-sensitivity-labels.md#apply-sensitivity-labels-in-power-bi-desktop-preview) og derefter genstarte programmet. Hvis programmet går ned efter genstart, kan det skyldes, at computeren mangler den påkrævede version af Visual C++ Redistributable-runtimebiblioteket. Hvis du oplever et sådant nedbrud, kan du gå til [siden Microsoft Visual C++ 2015 Distributed Update 3 download](https://www.microsoft.com/download/details.aspx?id=53587) for at få oplysninger om, hvordan du downloader og installerer opdateringen. Når du har installeret opdateringen, kan du prøve at starte computeren igen.

Hvis du anvender en følsomhedsmærkat i Desktop, når du publicerer dit arbejde til tjenesten, eller når du uploader en .pbix-fil af det pågældende arbejde til tjenesten, følger mærkaten med dataene til tjenesten. I tjenesten anvendes mærkaten både på det datasæt og den rapport, du får med filen. Hvis datasættet og rapporten allerede indeholder følsomhedsmærkater, vil disse mærkater blive overskrevet af mærkaten, der kommer fra Desktop.
 
Hvis du uploader en .pbix-fil, som aldrig er blevet publiceret til tjenesten før, og som har samme navn som en rapport eller et datasæt, der allerede findes i tjenesten, kan uploadet kun udføres, hvis den person, der uploader, har de RMS-tilladelser, der er nødvendige for at ændre mærkaten.

Det samme gælder også i modsat retning: Når du downloader til .pbix i tjenesten og derefter indlæser .pbix-filen i Desktop, vil den mærkat, der var i tjenesten, blive anvendt på den downloadede .pbix-fil og derfra blive indlæst i Desktop. Hvis rapporten og datasættet i tjenesten har forskellige mærkater, vil den mest restriktive af de to blive anvendt på den downloadede .pbix-fil.

Når du anvender en mærkat i Desktop, vises den på statuslinjen.

![Skærmbillede af følsomhedsmærkat på statuslinjen i Desktop.](media/service-security-sensitivity-label-overview/sensitivity-label-in-desktop-status-bar.png)

[Få mere at vide om, hvordan du anvender følsomhedsmærkater på Power BI-indhold og -filer](./service-security-apply-data-sensitivity-labels.md).


## <a name="sensitivity-label-inheritance-upon-creation-of-new-content"></a>Nedarvning af følsomhedsmærkater ved oprettelse af nyt indhold

Når der oprettes nye rapporter og dashboards i Power BI-tjenesten, arver de automatisk den følsomhedsmærkat, der tidligere er anvendt på et overordnet datasæt eller en rapport. En ny rapport, der er oprettet oven på et datasæt, som har følsomhedsmærkaten "stærkt fortroligt" får f.eks. automatisk også mærkaten "stærkt fortroligt".

På følgende billede kan du se, hvordan et datasæts følsomhedsmærkat anvendes automatisk på en ny rapport, der er bygget oven på datasættet.

![Animeret GIF, der viser nedarvning af følsomhedsmærkater](media/service-security-sensitivity-label-overview/InheritanceUponCreation.gif)

>[!NOTE]
>Hvis følsomhedsmærkaten af en eller anden grund ikke kan anvendes på den nye rapport eller det nye dashboard, blokerer Power BI **ikke** oprettelsen af det nye element.

## <a name="sensitivity-labels-and-protection-on-exported-data"></a>Følsomhedsmærkater og beskyttelse af eksporterede data

Når data eksporteres fra Power BI til Excel, PDF-filer (kun tjenesten) eller PowerPoint-filer, anvender Power BI automatisk en følsomhedsmærkat på den eksporterede fil og beskytter den i henhold til indstillingerne for mærkatens filkryptering. På den måde forbliver dine følsomme data beskyttede, uanset hvor de er.

En bruger, der eksporterer en fil fra Power BI, har tilladelse til at tilgå og redigere filen i henhold til indstillingerne for følsomhedsmærkaten. De får ikke ejertilladelser til filen.

>[!NOTE]
>Hvis den downloadede rapport og dens datasæt har forskellige mærkater, vil den mest restriktive mærkat blive anvendt på .pbix-filen, når du bruger **Download .pbix** i Power BI-tjenesten. 

Følsomhedsmærkater og beskyttelse anvendes ikke, når data eksporteres til .csv-filer eller andre typer eksportstier, der ikke understøttes.

Anvendelse af en følsomhedsmærkat og beskyttelse af en eksporteret fil føjer ikke indholdsmarkeringer til filen. Men hvis mærkaten er konfigureret til at anvende indholdsmarkeringer, anvendes markeringerne automatisk af Azure Information Protection Unified-navngivningsklienten, når filen åbnes i Office Desktop-apps. Indholdsmærkaterne anvendes ikke automatisk, når du bruger indbygget navngivning til skrivebords-, mobil- eller webapps. Se [Når Office-apps anvender indholdsmarkering og kryptering](/microsoft-365/compliance/sensitivity-labels-office-apps#when-office-apps-apply-content-marking-and-encryption) for at få flere oplysninger.

Eksporten mislykkes, hvis en mærkat ikke kan anvendes, når der eksporteres data til en fil. Hvis du vil kontrollere, om eksporten mislykkedes, fordi mærkaten ikke kunne anvendes, skal du klikke på navnet på rapporten eller dashboardet i midten af titellinjen og se, om der står "Følsomhedsmærkat kan ikke indlæses" på den rulleliste, der åbnes. Dette kan ske som følge af et midlertidigt systemproblem, eller hvis den anvendte mærkat er blevet fjernet eller slettet af sikkerhedsadministratoren.

## <a name="sensitivity-label-inheritance-in-analyze-in-excel"></a>Nedarvning af følsomhedsmærkater i Analysér i Excel

Når du opretter en pivottabel i Excel med en direkte forbindelse til et Power BI-datasæt (du kan enten gøre det fra Power BI via [Analysér i Excel](../collaborate-share/service-analyze-in-excel.md) eller fra [Excel](https://support.microsoft.com/office/create-a-pivottable-from-power-bi-datasets-31444a04-9c38-4dd7-9a45-22848c666884?ui=en-US&rs=en-US&ad=US)), nedarves datasættets følsomhedsmærkat og anvendes på din Excel-fil sammen med eventuelle tilknyttede beskyttelsesforanstaltninger. Hvis mærkaten på datasættet senere ændres til et mere restriktivt, opdateres den mærkat, der anvendes på den sammenkædede Excel-fil, automatisk efter dataopdatering.

![Skærmbillede af Excel, hvor følsomhedsmærkaten er nedarvet fra datasæt via direkte forbindelse.](media/service-security-sensitivity-label-overview/live-connection-inheritance.png)
 
Følsomhedsmærkater i Excel, der blev angivet manuelt, tilsidesættes ikke automatisk af datasættets følsomhedsmærkat. I stedet vises der et banner med en besked om, at datasættet har en følsomhedsmærkat, og det anbefales, at du anvender den.

>[!NOTE]
>Hvis datasættets følsomhedsmærkat er mindre restriktiv end Excel-filens følsomhedsmærkat, sker der ingen nedarvning eller opdatering af mærkater. En Excel-fil arver aldrig en mindre restriktiv følsomhedsmærkat.

## <a name="sensitivity-label-persistence-in-embedded-reports-and-dashboards"></a>Fastholdelse af følsomhedsmærkater i integrerede rapporter og dashboards

Du kan integrere Power BI-rapporter, -dashboards og -visualiseringer i virksomhedsprogrammer som f.eks. Microsoft Teams og SharePoint eller på en organisations websted. Når du integrerer en visualisering, en rapport eller et dashboard, der har en følsomhedsmærkat, er følsomhedsmærkaten synlig i den integrerede visning, og mærkaten og beskyttelsen af den bevares, når der eksporteres data til Excel.

![Skærmbillede af rapport, der er integreret i SharePoint Online](media/service-security-sensitivity-label-overview/embedded-report-sensitivity-label.png)

Følgende integreringsscenarier understøttes:
* [Integrer til din organisation](../developer/embedded/embed-sample-for-your-organization.md)
* Microsoft 365-apps (f.eks. [Teams](../collaborate-share/service-embed-report-microsoft-teams.md) og [SharePoint](../collaborate-share/service-embed-report-spo.md))
* [Integrering af sikre URL-adresser](../collaborate-share/service-embed-secure.md) (integration fra Power BI-tjenesten) 

## <a name="sensitivity-labels-in-the-power-bi-mobile-apps"></a>Følsomhedsmærkater i Power BI-mobilapps

Følsomhedsmærkater kan vises på rapporter og dashboards i Power BI-mobilapps. Et ikon i nærheden af navnet på rapporten eller dashboardet angiver, at der er et følsomhedsmærkat, og typen af mærkat og en tilhørende beskrivelse fremgår af rapportens eller dashboardets oplysningsfelt.

![Skærmbillede af følsomhedsmærkat i mobilapp](media/service-security-sensitivity-label-overview/mobile-app-sensitivity-label2.png)

## <a name="supported-clouds"></a>Understøttede cloudmiljøer
Følsomhedsmærkater understøttes kun for lejere i globale (offentlige) cloudmiljøer, og de understøttes ikke for lejere i cloudmiljøer, f.eks. nationale cloudmiljøer.

## <a name="licensing-and-requirements"></a>Licenser og krav

Se [Licenser og krav](service-security-enable-data-sensitivity-labels.md#licensing-and-requirements).

## <a name="sensitivity-label-creation-and-management"></a>Oprettelse og administration af følsomhedsmærkater

Følsomhedsmærkater oprettes og administreres enten i [Microsoft 365 Security Center](https://security.microsoft.com/) eller [Microsoft 365 Compliance Center](https://compliance.microsoft.com/).

Hvis du vil have adgang til følsomhedsmærkater i et af disse centre, skal du navigere til **Klassificering > Følsomhedsmærkater**. Disse følsomhedsmærkater kan bruges af flere Microsoft-tjenester, f.eks. Microsoft Azure Information Protection, Office-programmer og Office 365-tjenester.

>[!Important]
> Hvis din organisation bruger følsomhedsmærkater fra Azure Information Protection, skal du [overføre](/azure/information-protection/configure-policy-migrate-labels) dem til en af de tidligere angivne tjenester, før følsomhedsmærkaterne kan bruges i Power BI.

## <a name="limitations"></a>Begrænsninger

### <a name="general"></a>Generelt

* Det anbefales ikke at gøre det muligt for brugere at anvende overordnede mærkater i Power BI (en mærkat anses kun for at være en overordnet mærkat, hvis den har undermærkater). Hvis der anvendes en overordnet mærkat til indhold, kan eksport af data fra dette indhold til en fil (Excel, PowerPoint og PDF) mislykkes. Se [Undermærkater (grupperingsmærkater)](/microsoft-365/compliance/sensitivity-labels#sublabels-grouping-labels).

* Følsomhedsmærkater for data understøttes ikke for skabelonapps. Følsomhedsmærkater, der er angivet af opretteren af skabelonprogrammet, fjernes, når programmet udtrækkes og installeres. Følsomhedsmærkater, der føjes til artefakter i et installeret skabelonprogram af programbrugeren, mistes (nulstilles til ingenting), når programmet opdateres.

* Hvis et datasæt har en mærkat, der er blevet slettet fra administration af mærkater, i Power BI-tjenesten, kan du ikke eksportere eller downloade dataene. Der vises en advarsel i Analysér i Excel, og dataene eksporteres til en .odc-fil uden nogen følsomhedsmærkat. Hvis en .pbix-fil har en sådan ugyldig mærkat i Desktop, kan du ikke gemme filen.

* Power BI understøtter ikke følsomhedsmærkater for beskyttelsestyperne [Videresend ikke](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions) og [brugerdefineret](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions) og [HYOK](/azure/information-protection/configure-adrms-restrictions). Beskyttelsestyperne Videresend ikke og brugerdefineret henviser til de mærkater, der er defineret i [Microsoft 365 Security Center](https://security.microsoft.com/) eller [Microsoft 365 Compliance Center](https://compliance.microsoft.com/).

### <a name="power-bi-service"></a>Power BI-tjenesten

* Følsomhedsmærkater kan kun anvendes på dashboards, rapporter, datasæt og dataflows. De er i øjeblikket ikke tilgængelige til [sideinddelte rapporter](../paginated-reports/report-builder-power-bi.md) og projektmapper.

* Følsomhedsmærkater på Power BI-aktiver kan kun ses på listen over arbejdsområder og linjevisninger, Favoritter, Seneste og programvisninger. Mærkater er i øjeblikket ikke synlige i visningen Delt med mig. Bemærk dog, at en mærkat, som er anvendt på et Power BI-aktiv, altid bevares for data, der eksporteres til Excel-, PowerPoint- og PDF-filer, også selvom mærkaten ikke er synlig.

### <a name="power-bi-desktop-preview"></a>Power BI Desktop (prøveversion)

* Beskyttede .pbix-filer kan kun åbnes og/eller publiceres af en bruger, som er RMS-ejeren af filen (den bruger, der oprindeligt anvendte mærkaten på filen), eller som har brugsrettighederne [**Fuld kontrol** og/eller **Eksportér** brugsrettigheder](/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide) til den relevante mærkat. RMS-ejeren har Fuld kontrol og kan aldrig låses ude. [Se flere oplysninger](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner)

* Hvis den mærkat, der anvendes på en .pbix-fil, ikke er blevet publiceret til brugeren enten i Microsoft 365 Sikkerhedscenter eller Microsoft 365 Overholdelsescenter, kan brugeren ikke gemme filen i Desktop.

* Power BI Desktop-brugere kan opleve problemer med at gemme deres arbejde, hvis de mister internetforbindelsen, f.eks. efter at være gået offline. Uden internetforbindelse kan nogle handlinger relateret til følsomhedsmærkater og administration af rettigheder muligvis ikke fuldføres korrekt. I sådanne tilfælde anbefales det, at du skifter til at være online igen og prøver at gemme igen.

* Hvis du har oprettet en stor model, og den resulterende beskyttede .pbix-fil er meget stor (over 2 GB), kan modellen gå ned, når du forsøger at gemme eller åbne den. Du kan løse dette problem ved at overveje at fjerne beskyttelsen af .pbix-filen og anvende den igen, efter filen er blevet publiceret til Power BI-tjenesten.

    Det er generelt god praksis også at bruge en anden krypteringsmetode, når du beskytter en fil med en følsomhedsmærkat, der anvender kryptering, f.eks. kryptering af sidefil, NTFS-kryptering, bitlockers, antimalware osv.

* Midlertidige filer er ikke krypteret.

* **Hent data** kan kun bruges til at uploade beskyttede filer, hvis de ikke er lokale. Beskyttede filer fra onlinetjenester, f.eks. SharePoint Online eller OneDrive for Business, kan ikke uploades. I forbindelse med en beskyttet fil kan du enten uploade den fra din lokale enhed eller starte med at fjerne filens mærkat i Power BI Desktop og derefter uploade den via en af onlinetjenesterne.

* **Eksportér til PDF** understøtter ikke følsomhedsmærkater. Hvis du eksporterer en fil, der har en følsomhedsmærkat, til PDF, modtager PDF-filen ikke mærkaten, og der anvendes ingen beskyttelse.

* Information Protection i Power BI Desktop understøtter ikke **B2B** og **scenarier med flere lejere**.

* Hvis du overskriver et mærket datasæt eller en rapport i tjenesten med en ikke-navngivet. pbix-fil, gemmes etiketterne i tjenesten.

## <a name="next-steps"></a>Næste trin

Denne artikel indeholdt en oversigt over databeskyttelse i Power BI. Følgende artikler indeholder flere oplysninger om databeskyttelse i Power BI. 

* [Aktivér følsomhedsmærkater i Power BI](service-security-enable-data-sensitivity-labels.md)
* [Sådan anvendes følsomhedsmærkater i Power BI](service-security-apply-data-sensitivity-labels.md)
* [Brug af Microsoft Cloud App Security-kontrolelementer i Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport over beskyttelsesmålepunkter](service-security-data-protection-metrics-report.md)