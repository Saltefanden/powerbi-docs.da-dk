---
title: Rapportparametre i Power BI Report Builder
description: I dette emne beskrives den almindelige brug af rapportparametre i Power BI Report Builder, hvilke egenskaber du kan angive og meget mere.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 06/06/2019
ms.openlocfilehash: 6c0a891257ae4e768c3952398eb8303906bf2ce4
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297803"
---
# <a name="report-parameters-in-power-bi-report-builder"></a>Rapportparametre i Power BI Report Builder

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

I dette emne beskrives den almindelige brug af rapportparametre i Power BI Report Builder, hvilke egenskaber du kan angive og meget mere. Ved hjælp af rapportparametre kan du styre rapportdata, oprette forbindelse mellem relaterede rapporter og variere præsentationen af rapporter. Du kan bruge rapportparametre i sideinddelte rapporter, du opretter i Report Builder.

## <a name="common-uses-for-parameters"></a><a name="bkmk_Common_Uses_for_Parameters"></a> Almindelig brug af parametre

 Her er nogle af de mest almindelige måder at bruge parametre på.  
  
**Styr data i sideinddelte rapporter**
  
- Filtrer data i sideinddelte rapporter på datakilden ved at skrive forespørgsler i datasæt, som indeholder variabler.  
  
- Giv brugerne mulighed for at angive værdier for at tilpasse dataene i en sideinddelt rapport. Angiv f.eks. to parametre for startdato og slutdato for salgsdata.  
  
**Varier præsentationen af en rapport**
  
- Giv brugerne mulighed for at angive værdier for at hjælpe med at tilpasse udseendet af en rapport. Angiv f.eks. en boolesk parameter for at angive, om alle indlejrede rækkegrupper i en tabel skal udvides eller skjules.  
  
- Giv brugerne mulighed for at tilpasse rapportdata og udseendet ved at inkludere parametre i et udtryk.  
  
## <a name="viewing-a-report-with-parameters"></a><a name="UserInterface"></a> Visning af en rapport med parametre

Når du får vist en rapport, der indeholder parametre, viser værktøjslinjen for rapportfremviseren de enkelte parametre, så du kan angive værdier interaktivt. I illustrationen nedenfor vises parameterområdet for en rapport med parametrene @ReportMonth, @ReportYear, @EmployeeID, @ShowAll, @ExpandTableRows, @CategoryQuota og @SalesDate.  

![Vis rapporten med parametre](media/report-builder-parameters/report-builder-parameters-power-bi-service.png "Vis rapport med parametre")
  
1. **Ruden Parametre** På værktøjslinjen i rapportfremviseren vises der en prompt og en standardværdi for de enkelte parametre. Du kan tilpasse layoutet af parametre i ruden Parametre.  
  
2. **@SalesDate Parameteren** parameteren @SalesDate er datatype **DateTime**. Prompten Vælg datoen vises ud for tekstfeltet. Hvis du vil redigere datoen, skal du skrive en ny dato i tekstfeltet eller bruge kalenderkontrolelementet.  
  
3. **@ShowAll parameteren** Parameteren @ShowAll er af datatypen **Boolesk**. Brug alternativknapperne til at angive **Sand** eller **Falsk**.  
  
4. **Vis eller skjul håndtaget til parameterområde** På værktøjslinjen i rapportfremviseren skal du klikke på pilen for at vise eller skjule parameterruden.  
  
5. **@CategoryQuota parameteren** Parameteren @CategoryQuota er af datatypen **Flydende** , så den skal have en numerisk værdi.  @CategoryQuota er angivet til at tillade flere værdier.  
  
6. **Få vist rapport** Når du har angivet parameterværdier, skal du klikke på **Vis rapport** for at køre rapporten. Hvis alle parametre har standardværdier, køres rapporten automatisk ved første visning.  
  
## <a name="creating-parameters"></a><a name="bkmk_Create_Parameters"></a> Oprettelse af parametre

Du kan oprette rapportparametre på et par forskellige måder.
  
> [!NOTE]
>  Det er ikke alle datakilder, som understøtter parametre.
  
**Forespørgsel for datasæt eller gemt procedure med parametre**
  
 Tilføj en forespørgsel for datasæt, der indeholder variabler, eller et datasæt med en gemt procedure, som indeholder inputparametre. Der oprettes en parameter for datasæt for hver variabel eller inputparameter, og der oprettes en rapportparameter for hver datasætparameter.  
  
![Egenskaber for Report Builder-datasætparametre](media/report-builder-parameters/report-builder-parameter-dataset.png "Egenskaber for Report Builder-datasætparametre")

  
 Dette billede fra Report Builder viser:  
  
1.  Rapportparametrene i ruden Rapportdata.  
  
2.  Datasættet med parametre.  
  
3.  Ruden Parametre.  
  
4.  Parametrene angivet i dialogboksen Egenskaber for datasæt.  
  
**Opret en parameter manuelt**
  
Opret en parameter manuelt via ruden Rapportdata. Du kan konfigurere rapportparametre, så en bruger kan angive værdier interaktivt for at tilpasse indholdet eller udseendet af en rapport. Du kan også konfigurere rapportparametre, så en bruger ikke kan ændre forudkonfigurerede værdier.  
  
> [!NOTE]  
>  Da parametre administreres uafhængigt af hinanden på serveren, overskrives de eksisterende parameterindstillinger i rapporten ikke, når en hovedrapport publiceres igen med nye parameterindstillinger.  

### <a name="parameter-values"></a>Parameterværdier

 Følgende er indstillinger for at vælge parameterværdier i rapporten.  
  
- Vælg en enkelt parameterværdi på rullelisten.  
  
- Vælg flere parameterværdier på rullelisten.  
  
- Vælg en værdi på en rulleliste for én parameter, hvilket bestemmer, hvilke værdier der er tilgængelige på rullelisten for en anden parameter. Disse er overlappende parametre. Overlappende parametre giver dig mulighed for efterfølgende at filtrere parameterværdier fra tusindvis af værdier til et mere håndterbart antal. Du kan få flere oplysninger under [Anvend overlappende parametre i sideinddelte rapporter](../guidance/paginated-report-cascading-parameter.md).
  
- Kør rapporten uden først at skulle vælge en parameterværdi, fordi der er blevet oprettet en standardværdi for parameteren.  
  
## <a name="report-parameter-properties"></a><a name="bkmk_Report_Parameters"></a> Egenskaber for rapportparameter

 Du kan ændre egenskaberne for rapportparametre ved hjælp af dialogboksen Egenskaber for rapport. I følgende tabel opsummeres de egenskaber, du kan angive for hver parameter:  
  
|Egenskab|Beskrivelse|  
|--------------|-----------------|  
|Name|Skriv et navn på parameteren, hvor der skelnes mellem store og små bogstaver. Navnet skal begynde med et bogstav og kan indeholder bogstaver, tal og et understregningstegn (_). Navnet må ikke indeholde mellemrum. For automatisk oprettede parametre svarer navnet til parameteren i forespørgslen for datasæt. Manuelt oprettede parametre svarer som standard til ReportParameter1.|  
|Prompt|Den tekst, der vises ved siden af parameteren på værktøjslinjen i rapportfremviseren.|  
|Datatype|En rapportparameter skal være en af følgende datatyper:<br /><br /> **Boolesk**. Brugeren vælger Sand eller Falsk via en alternativknap.<br /><br /> **DateTime**. Brugeren vælger en dato via et kalenderkontrolelement.<br /><br /> **Heltal**. Brugeren skriver værdier i et tekstfelt.<br /><br /> **Flydende**. Brugeren skriver værdier i et tekstfelt.<br /><br /> **Tekst**. Brugeren skriver værdier i et tekstfelt.<br /><br /> Når der er defineret tilgængelige værdier for en parameter, vælger brugeren værdier via en rulleliste, selv når datatypen er **DateTime**.|  
|Tillad tom værdi|Vælg denne indstilling, hvis værdien af parameteren kan være en tom streng eller en tom værdi.<br /><br /> Hvis du angiver gyldige værdier for en parameter, og du vil have, at en tom værdi skal være en af de gyldige værdier, skal du inkludere den som en af de angivne værdier. Valg af denne indstilling inkluderer ikke automatisk en tom værdi for tilgængelige værdier.|  
|Tillad null-værdi|Vælg denne indstilling, hvis værdien af parameteren kan være en null-værdi.<br /><br /> Hvis du angiver gyldige værdier for en parameter, og du vil have, at en null-værdi skal være en af de gyldige værdier, skal du inkludere null som en af de angivne værdier. Valg af denne indstilling inkluderer ikke automatisk en null-værdi for tilgængelige værdier.|  
|Tillad flere værdier|Angiv tilgængelige værdier for at oprette en rulleliste, som dine brugere kan vælge fra. Dette er en god måde at sikre, at der kun indsendes gyldige værdier i forespørgslen for datasættet.<br /><br /> Vælg denne indstilling, hvis værdien for parameteren kan være flere værdier, som vises på en rulleliste. Null-værdier er ikke tilladt. Når denne indstilling er valgt, føjes der afkrydsningsfelter til listen over tilgængelige værdier på en rulleliste for parameteren. Øverst på listen er der et afkrydsningsfelt for **Vælg alle**. Brugerne kan markere de værdier, de vil have.<br /><br /> Hvis de data, der leverer værdier, ændres hurtigt, er den liste, brugeren får vist, muligvis ikke den nyeste.|  
|Synlig|Vælg denne indstilling for at vise rapportparameteren øverst i rapporten, når den køres. Denne indstilling giver brugerne mulighed for at vælge parameterværdier på kørselstidspunktet.|  
|Skjult|Vælg denne indstilling for at skjule rapportparameteren i den publicerede rapport. Værdierne for rapportparametre kan stadig angives i en URL-adresse for rapporten, i en definitionen for et abonnement eller på rapportserveren.|  
|Intern|Vælg denne indstilling for at skjule rapportparameteren. I den publicerede rapport kan rapportparameteren kun blive vist i rapportdefinitionen.|  
|Tilgængelige værdier|Hvis du har angivet tilgængelige værdier for en parameter, vises de gyldige værdier altid på en rulleliste. Hvis du f.eks. angiver tilgængelige værdier for parameteren **DateTime** , vises der en rulleliste med datoer i parameterruden i stedet for et kalenderkontrolelement.<br /><br /> Hvis du vil sikre, at en liste over værdier er ensartet mellem en rapport og underrapporter, kan du angive en indstilling på datakilden for at bruge en enkelt transaktion for alle forespørgsler i de datasæt, der er knyttet til en datakilde.<br /><br /> **Sikkerhedsbemærkning** I alle rapporter, der indeholder en parameter af datatypen **Tekst** , skal du sørge for, at du bruger en liste over tilgængelige værdier (også kendt som en liste med gyldige værdier), og sikre, at alle brugere, der kører rapporten, kun har de tilladelser, som er nødvendige for at få vist dataene i rapporten.|  
|Standardværdier|Angiv standardværdier fra en forespørgsel eller fra en statisk liste.<br /><br /> Når hver parameter har en standardværdi, køres rapporten automatisk ved første visning.|  
|Erfaren|Angiv attributten **UsedInQuery** for rapportdefinitionen, som er en værdi, der indikerer, om denne parameter direkte eller indirekte påvirker dataene i en rapport.<br /><br /> **Bestem automatisk, hvornår der skal opdateres**<br /> Vælg denne indstilling, når rapportbehandleren skal fastsætte en indstilling for denne værdi. Værdien er **Sand** , hvis rapportbehandleren registrerer en forespørgsel for datasæt med en direkte eller indirekte reference til denne parameter, eller hvis rapporten indeholder underrapporter.<br /><br /> **Opdater altid**<br /> Vælg denne indstilling, når rapportparameteren bruges direkte eller indirekte i en forespørgsel for datasæt eller et parameterudtryk. Denne indstilling angiver **UsedInQuery** til Sand.<br /><br /> **Opdater aldrig**<br /> Vælg denne indstilling, når rapportparameteren ikke bruges direkte eller indirekte i en forespørgsel for datasæt eller et parameterudtryk. Denne indstilling angiver **UsedInQuery** til Falsk.<br /><br /> **Forsigtig!** Brug **Opdater aldrig** med forsigtighed. På rapportserveren bruges **UsedInQuery** til at hjælpe med at styre cacheindstillinger for rapportdata og gengivne rapporter og parameterindstillinger for snapshotrapporter. Hvis du angiver **Opdater aldrig** forkert, kan du være skyld i, at forkerte rapportdata eller rapporter cachelagres, eller at der er uensartede data i en snapshotrapport. |  
  
##  <a name="dataset-query"></a><a name="bkmk_Dataset_Parameters"></a> Forespørgsel for datasæt  
 Hvis du vil filtrere dataene i forespørgslen for datasættet, kan du inkludere en delsætning som begrænsning, der begrænser de hentede data ved at angive værdier for at inkludere eller udelade resultater i resultatsættet.  
  
 Brug forespørgselsdesigner til datakilden for at udarbejde en parameteriseret forespørgsel.  
  
-   I forbindelse med forespørgsler til Transact-SQL understøtter forskellige datakilder forskellig syntaks for parametre. Understøttelse spænder fra parametre, der er identificeret i forespørgslen efter placering eller efter navn. I den relationelle forespørgselsdesigner skal du vælge parameterindstillingen for et filter for at oprette en parameteriseret forespørgsel.   
  
-   For forespørgsler, der er baseret på en flerdimensionel datakilde, f.eks. Microsoft SQL Server Analysis Services, kan du angive, om du vil oprette en parameter baseret på et filter, som du angiver i forespørgselsdesigneren. 
  
##  <a name="parameter-management-for-a-published-report"></a><a name="bkmk_Manage_Parameters"></a> Administration af parameter for en publiceret rapport  
 Når du designer en rapport, gemmes rapportparametrene i rapportdefinitionen. Når du publicerer en rapport, gemmes og administreres rapportparametrene fra rapportdefinitionen.  
  
 Du kan bruge følgende for en publiceret rapport:  
  
-   **Egenskaber for rapportparameter.** Skift værdierne for rapportparametre direkte på rapportserveren uafhængigt af rapportdefinitionen.  
  
-   **Abonnementer på rapporter.** Du kan angive parameterværdierne for at filtrere data og levere rapporter via abonnementer. 
  
 Parameteregenskaberne for en publiceret rapport bevares, hvis du publicerer rapportdefinitionen igen. Hvis rapportdefinitionen publiceres igen som den samme rapport, og navnene på parametrene og datatyperne forbliver de samme, bevares dine indstillinger for egenskaber. Hvis du tilføjer eller sletter parametre i rapportdefinitionen eller ændrer datatypen eller navnet på en eksisterende parameter, skal du muligvis ændre parameteregenskaberne i den publicerede rapport.  
  
 Det er ikke alle parametre, der kan ikke ændres i alle tilfælde. Hvis en rapportparameter henter en standardværdi fra en forespørgsel for datasættet, kan denne værdi ikke redigeres for en publiceret rapport og kan ikke redigeres på rapportserveren. Den værdi, der bruges på kørselstidspunktet, bestemmes, når forespørgslen køres, eller når udtrykket evalueres for parametre baseret på udtryk.  
  
 Indstillinger for udførelse af rapporten kan påvirke den måde, parametre behandles på. En rapport, der kører som et snapshot, kan ikke bruge parametre, der er afledt fra en forespørgsel, medmindre forespørgslen indeholder standardværdier for parametrene.  
  
##  <a name="parameters-for-a-subscription"></a><a name="bkmk_Parameters_Subscription"></a> Parametre for et abonnement  
 Du kan definere et abonnement til at være efter behov eller til et snapshot og angive parameterværdier, der skal bruges under behandlingen af abonnementet.  
  
-   **Rapport on-demand.**  For en rapport af typen on-demand kan du angive en anden parameterværdi end den publicerede værdi for hver parameter, der er angivet for rapporten. Lad os f.eks. antage, at du har en Opkaldsservice-rapport, der bruger parameteren *Tidsperiode* til at returnere kundeserviceanmodninger for den aktuelle dag, uge eller måned. Hvis standardparameterværdien for rapporten er angivet til **i dag** , kan dit abonnement bruge en anden parameterværdi (f.eks. **uge** eller **måned** ) til at skabe en rapport, der indeholder ugentlige eller månedlige tal.  
  
## <a name="next-steps"></a>Næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Anvend overlappende parametre i sideinddelte rapporter](../guidance/paginated-report-cascading-parameter.md)
