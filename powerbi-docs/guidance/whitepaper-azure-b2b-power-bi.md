---
title: Distribuer Power BI-indhold til eksterne gæstebrugere vha. Azure Active Directory B2B
description: Whitepaper, der beskriver, hvordan du bruger Azure Active Directory B2B til at distribuere Power BI til eksterne gæstebrugere
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/07/2019
LocalizationGroup: Conceptual
ms.openlocfilehash: 9bf2d1ab3b782d0fbb201e203aa9bb2f2df4079d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416940"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribuer Power BI-indhold til eksterne gæstebrugere vha. Azure Active Directory B2B

**Oversigt:** Dette er en teknisk hvidbog, der indeholder en beskrivelse af, hvordan du distribuerer indhold til brugere uden for organisationen ved hjælp af integrationen af Azure Active Directory business-to-business (Azure AD B2B).

**Skrivere:** Lukasz Pawlowski, Kasper de Jonge

**Tekniske reviewere:** Adam Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, Maya Shenhav, Nimrod Shalit

> [!NOTE]
> Du kan gemme eller udskrive denne whitepaper ved at vælge **Udskriv** i din browser og derefter vælge **Gem som PDF**.

## <a name="introduction"></a>Introduktion

Power BI giver organisationer en 360-graders visning af deres forretning og gør det muligt for alle i disse organisationer at foretage intelligente beslutninger ved hjælp af data. Mange af disse organisationer har stærke relationer med eksterne partnere, klienter og underleverandører, der er baseret på gensidig tillid. Disse organisationer har behov for at kunne give brugerne hos disse eksterne partnere sikker adgang til Power BI-dashboards og -rapporter.

Power BI kan integreres med [Azure Active Directory Business-til-business (Azure AD B2B)](/azure/active-directory/b2b/what-is-b2b) for at tillade sikker distribution af Power BI-indhold til gæstebrugere uden for organisationen, mens du stadig bevarer kontrollen og administrerer adgangen til de interne data.

Dette whitepaper gennemgår alle de oplysninger, du har brug for til at forstå Power BI-integration med Azure Active Directory B2B. Vi gennemgår programmets mest almindelige use case, installation, licensering og sikkerhed på rækkeniveau.

> [!NOTE]
> I hele dette whitepaper refererer vi til Azure Active Directory som Azure AD og Azure Active Directory Business to Business som Azure AD B2B.

## <a name="scenarios"></a>Scenarier

Contoso er en producent inden for bilindustrien og arbejder sammen med mange forskellige leverandører, der leverer alle de komponenter, materialer og tjenester, der er nødvendige for at køre produktionen. Contoso vil gerne forenkle sin forsyningskædelogistik og planlægger at bruge Power BI til at overvåge nøgletal for forsyningskæden. Contoso vil gerne dele analyser med eksterne forsyningskædepartnere på en sikker og administrerbar måde.

Contoso kan aktivere følgende oplevelser for eksterne brugere ved hjælp af Power BI og Azure AD B2B.

### <a name="ad-hoc-per-item-sharing"></a>Ad hoc-deling pr. element

Contoso arbejder sammen med en leverandør, der bygger kølere til Contosos biler. De har ofte brug for at optimere stabiliteten af kølerne ved hjælp af data fra alle Contosos biler. En analytiker hos Contoso bruger Power BI til at dele en rapport over kølernes stabilitet med en tekniker hos leverandøren. Teknikeren modtager en mail med et link til at få vist rapporten.

Som beskrevet ovenfor udføres denne ad hoc-deling af virksomhedsbrugere efter behov. Det link, der sendes af Power BI til den eksterne bruger, er et Azure AD B2B-invitationslink. Når den eksterne bruger åbner linket, bliver vedkommende bedt om at slutte sig til Contosos Azure AD-organisation som en gæstebruger. Når invitationen er accepteret, åbnes den specifikke rapport eller dashboard, når der klikkes på linket. Azure Active Directory-administratoren uddelegerer tilladelser til at invitere eksterne brugere til organisationen og vælger, hvad disse brugere kan foretage sig, når de accepterer invitationen, som beskrevet i afsnittet Styring i dette dokument. Analytikeren hos Contoso kan kun invitere gæstebrugeren, fordi Azure AD-administratoren gav tilladelse til denne handling, og Power BI-administratoren gav brugere tilladelse til at invitere gæster til at få vist indhold i Power BI's lejerindstillinger.

![Inviter gæster til Power BI ved hjælp af AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. Processen starter med en intern Contoso-bruger, der deler et dashboard eller en rapport med en ekstern bruger. Hvis den eksterne bruger ikke allerede er gæst i Contosos Azure AD, inviteres vedkommende. Der sendes en mail til den eksterne brugers mailadresse, der omfatter en invitation til Contosos Azure AD.
2. Modtageren accepterer invitationen til Contosos Azure AD og tilføjes som en gæstebruger i Contosos Azure AD.
3. Modtageren omdirigeres derefter til Power BI-dashboardet, rapporten eller appen, der er skrivebeskyttet for brugeren.

Processen anses for at være ad hoc, eftersom virksomhedsbrugere i Contoso udfører invitationshandlingen efter behov i forbindelse med deres forretningsmæssige formål. Hvert element, der deles, er et enkelt link, som den eksterne bruger kan benytte til at få vist indholdet.

Når den eksterne bruger er inviteret til at få adgang til Contoso-ressourcer, kan en skyggekonto oprettes for den eksterne bruger i Contoso Azure AD, og vedkommende behøver ikke at blive inviteret igen.  Første gang brugeren forsøger at få adgang til en Contoso-ressource, f.eks. et Power BI-dashboard, går vedkommende gennem en samtykkeproces, hvor invitationen accepteres.  Hvis samtykket ikke accepteres, kan brugeren ikke få adgang til noget af Contosos indhold.  Hvis brugeren har problemer med at acceptere sin invitation via det oprindelige link, der blev sendt, kan en administrator af Azure AD sende et bestemt invitationslink igen, som den eksterne bruger kan acceptere.

### <a name="planned-per-item-sharing"></a>Planlagt deling pr. element

Contoso arbejder sammen med en underleverandør om at udføre stabilitetsanalyser af kølerne. Underleverandøren har et team på 10 personer, der skal have adgang til data i Contosos Power BI-miljø. Administratoren af Contosos Azure AD er involveret i at invitere alle brugerne og i at håndtere en hvilken som helst tilføjelse/ændring, når personalet hos underleverandøren ændres. Azure AD administratoren opretter en sikkerhedsgruppe for alle medarbejdere hos underleverandøren. Ved hjælp af sikkerhedsgruppen kan Contosos medarbejdere nemt administrere adgang til rapporter og sikre, at alle de relevante medarbejdere hos underleverandøren har adgang til alle de påkrævede rapporter, dashboards og Power BI-apps. Azure AD-administratoren kan også undgå at blive involveret i invitationsprocessen helt ved at vælge at uddelegere invitationsrettigheder til en medarbejder, der er tillid til, hos Contoso eller hos underleverandøren for at sikre rettidig personaleadministration.

Nogle organisationer kræver mere kontrol over, hvornår der tilføjes eksterne brugere eller hvornår der inviteres mange brugere i en ekstern organisation eller mange eksterne organisationer. I disse tilfælde kan planlagt deling bruges til at administrere omfanget af deling, til at gennemtvinge organisationens politikker og endda til at delegere rettigheder til personer, der er tillid til, så de kan invitere og administrere eksterne brugere. Azure AD B2B understøtter, at planlagte invitationer sendes direkte [fra Azure-portalen af en it-administrator](/azure/active-directory/b2b/add-users-administrator) eller gennem [PowerShell ved hjælp af invitationsstyrings-API'en](/azure/active-directory/b2b/customize-invitation-api), hvor et sæt brugere kan inviteres via én handling. Organisationer kan ved hjælp af metoden med planlagte invitationer styre, hvem der kan invitere brugere og implementere godkendelsesprocesser. Avancerede Azure AD-funktioner som f.eks. dynamiske grupper gør det nemt at vedligeholde medlemskab af sikkerhedsgrupper automatisk.


![Kontrollér, hvilke gæster der kan få vist indhold](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. Processen starter med en IT-administrator, der inviterer gæstebrugeren enten manuelt eller via den API, der leveres af Azure Active Directory
2. Brugeren accepterer invitationen til organisationen.
3. Når brugeren har accepteret invitationen, kan en bruger i Power BI dele en rapport eller et dashboard med den eksterne bruger eller en sikkerhedsgruppe, som brugeren er i. På samme måde som med almindelig deling i Power BI modtager den eksterne bruger en mail med linket til elementet.
4. Når den eksterne bruger får adgang via linket, overføres brugerens godkendelse i vedkommendes mappe til Contosos Azure AD og bruges til at få adgang til Power BI-indhold.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad hoc- eller planlagt deling af Power BI-apps

Contoso har et sæt rapporter og dashboards, de har brug for at dele med en eller flere leverandører. For at sikre at alle relevante eksterne brugere har adgang til dette indhold, pakkes det som en Power BI-app. De eksterne brugere føjes enten direkte til appens adgangsliste eller via sikkerhedsgrupper. En person hos Contoso sender derefter URL-adressen til alle eksterne brugere, for eksempel i en mail. Når de eksterne brugere åbner linket, får de vist alt indholdet via en enkel oplevelse, der er nem at navigere i.

Brug af en Power BI-app gør det nemt for Contoso at oprette en BI-portal til sine leverandører. En enkelt adgangsliste styrer adgangen til alt påkrævet indhold, hvilket reducerer spiltid i forbindelse med kontrol og angivelse af tilladelser på elementniveau. Azure AD B2B vedligeholder sikkerhedsadgang ved hjælp af leverandørens oprindelige identitet, så brugerne ikke behøver yderligere logonoplysninger. Hvis der bruges planlagte invitationer med sikkerhedsgrupper, forenkles adgangsstyringen til appen, når personale flyttes til og fra projektet. Medlemskab i sikkerhedsgrupper foretages manuelt eller ved hjælp af [dynamiske grupper](/azure/active-directory/b2b/use-dynamic-groups), så alle eksterne brugere fra en leverandør automatisk føjes til den relevante sikkerhedsgruppe.


![Kontrollér indhold med AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. Processen startes, ved at brugeren inviteres til Contosos Azure AD-organisation via Azure Portal eller PowerShell
2. Brugeren kan føjes til en brugergruppe i Azure AD. Du kan bruge en statisk eller dynamisk brugergruppe, men dynamiske grupper er med til at reducere det manuelle arbejde.
3. De eksterne brugere får adgang til Power BI-appen via brugergruppen. URL-adressen skal sendes direkte til den eksterne bruger eller placeres på et websted, brugeren har adgang til. Power BI bestræber sig på at sende en mail med linket til appen til eksterne brugere, men hvis brugergrupper, hvis medlemskab kan blive ændret, benyttes, kan Power BI ikke sende til alle eksterne brugere, der administreres via brugergrupper.
4. Når den eksterne bruger får adgang til URL-adressen til Power BI-appen, godkendes vedkommende af Contosos Azure AD, appen installeres for brugeren, og brugeren kan få vist alle rapporter og dashboards i appen.

Apps har også en unik funktion, der gør det muligt for appforfattere at installere appen automatisk for brugeren, så den er tilgængelig, når brugeren logger på. Denne funktion installeres kun automatisk for eksterne brugere, der allerede er en del af Contosos organisation, på det tidspunkt hvor appen publiceres eller opdateres. Den fungerer derfor bedst sammen med planlagte invitationer og er afhængig af, at appen publiceres eller opdateres, efter brugerne er føjet til Contosos Azure AD. Eksterne brugere kan altid installere appen ved hjælp af applinket.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Kommentarer til og abonnement på indhold på tværs af organisationer

Eftersom Contoso fortsætter samarbejdet med sine underleverandører eller leverandører, skal de eksterne teknikere arbejde tæt sammen med Contosos analytikere. Power BI indeholder flere samarbejdsfunktioner, der hjælper brugerne med at kommunikere om indhold, som de kan forbruge. Dashboardkommentarer (og snart rapportkommentarer) giver brugerne mulighed for at diskutere de datapunkter, de kan få vist, og kommunikere med forfatterne af rapporten for at stille spørgsmål.

I øjeblikket kan eksterne gæstebrugere deltage i kommentarer ved at skrive kommentarer og læse svarene. Men i modsætning til interne brugere må gæstebrugere ikke være @mentioned og modtager ikke beskeder om, at de har modtaget en kommentar. Gæstebrugere kan i skrivende stund ikke bruge abonnementsfunktionen i Power BI. I en kommende version ophæves disse begrænsninger, og gæstebrugeren modtager en mail, når en kommentar @mentions dem, eller når et abonnement leveres til deres mail, der indeholder et link til indholdet i Power BI.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Adgang til indhold i Power BI-mobilappene

I en kommende version, når Contosos brugere deler rapporter eller dashboards med deres eksterne gæstebrugere, sender Power BI en mail, der giver gæstebrugeren besked. Når gæstebrugeren åbner linket til rapporten eller dashboardet på sin mobilenhed, åbnes indholdet i de oprindelige Power BI-mobilapps på enheden, hvis de er installeret. Gæstebrugeren kan derefter navigere mellem indhold, der deles med dem i den eksterne lejer, og tilbage til deres eget indhold fra deres private lejer.

> [!NOTE]
> Gæstebrugeren kan ikke åbne Power BI-mobilappen og straks navigere til den eksterne lejer, men skal starte med et link til et element i den eksterne lejer. Almindelige løsninger er beskrevet i afsnittet [Distribution af links til indhold i den overordnede organisations Power BI](#distributing-links-to-content-in-the-parent-organizations-power-bi) senere i dette dokument.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Redigering og administration af Power BI-indhold på tværs af organisationer

Contoso og dets leverandører og underleverandører arbejder stadig tæt sammen. En analytiker hos underleverandøren har ofte brug for at føje flere målepunkter eller datavisualiseringer til en rapport, som Contoso har delt med vedkommende. Dataene skal være placeret i Contosos Power BI-lejer, men eksterne brugere skal være i stand til at redigere dem, oprette nyt indhold og endda distribuere dataene til relevante personer.

Power BI indeholder en indstilling, der gør det muligt for **eksterne gæstebrugere at redigere og administrere indhold** i organisationen. Eksterne brugere har som standard en skrivebeskyttet forbrugsrettet oplevelse. Denne nye indstilling giver dog Power BI-administratoren mulighed for at vælge, hvilke eksterne brugere der kan redigere og administrere indhold i deres egen organisation. Når den eksterne bruger har fået tilladelse, kan vedkommende redigere rapporter og dashboards, publicere eller opdatere apps, arbejde i arbejdsområder og oprette forbindelse til de data, vedkommende har tilladelse til at bruge.

Dette scenarie er beskrevet i detaljer i afsnittet Mulighed for eksterne brugere for at redigere og administrere indhold i Power BI senere i dette dokument.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Organisatoriske relationer ved hjælp af Power BI og Azure AD B2B

Når alle brugere af Power BI er interne i organisationen, er der ingen grund til at bruge Azure AD B2B. Men når to eller flere organisationer ønsker at samarbejde om data og indsigt, sørger Power BI's understøttelse af Azure AD B2B for, at det både er nemt og omkostningseffektivt.

Nedenfor ses typiske organisationsstrukturer, der er velegnede til Azure AD B2B-baseret samarbejde på tværs af organisationer i Power BI. Azure AD B2B fungerer godt i de fleste tilfælde, men i nogle situationer er de almindelige alternative metoder, der er beskrevet i slutningen af dette dokument, værd at overveje.

### <a name="case-1-direct-collaboration-between-organizations"></a>Eksempel 1: direkte samarbejde mellem organisationer

Contosos relation til sin kølerleverandør er et eksempel på direkte samarbejde mellem organisationer. Da der er relativt få brugere hos Contoso og virksomhedens leverandør, der skal have adgang til oplysninger om kølerstabilitet, er brug af Azure AD B2B-baseret ekstern deling ideelt. Det er nemt at bruge og administrere. Dette er også et almindeligt mønster for konsulenttjenester, hvor en konsulent kan have brug for at oprette indhold til en organisation.

![Del mellem organisationer](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Denne form for deling sker typisk indledningsvist ved hjælp af ad hoc-deling pr. element. Men efterhånden som teams vokser eller relationer styrkes, bliver tilgangen med planlagt deling pr. element den foretrukne metode for at reducere omkostningerne forbundet med administration. Herudover kan ad hoc-deling eller planlagt deling af Power BI-apps, kommentering af og abonnement på indhold på tværs af organisationer, adgang til indhold i mobilapps komme på tale også samt redigering og administration af Power BI-indhold på tværs af organisationer. Det er vigtigt at bemærke, at hvis begge organisationers brugere har Power BI Pro-licenser i deres respektive virksomheder, kan de bruge disse Pro-licenser i hinandens Power BI-miljøer. Dette giver fordelagtig licensering, eftersom den organisation, der inviterer, muligvis ikke behøver at betale for en Power BI Pro-licens til de eksterne brugere. Det er beskrevet mere detaljeret i afsnittet Licensering senere i dette dokument.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Eksempel 2: overordnet og dets datterselskaber eller associerede selskaber

Nogle organisationsstrukturer er mere komplekse, herunder helt eller delvist ejede datterselskaber, associerede selskaber eller administrerede tjenesteudbyderrelationer. Disse organisationer har en overordnet organisation f.eks et holdingselskab, men de underliggende organisationer fungerer delvist selvstændigt, nogle gange under forskellige regionale krav. Dette fører til, at hver organisation har sit eget Azure AD-miljø og separate Power BI-lejere.

![Arbejde med datterselskaber](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


I denne struktur skal den overordnede organisation typisk distribuere standardiseret indsigt til dens datterselskaber. Denne deling sker typisk ved hjælp af metoden med ad hoc- eller planlagt deling af Power BI-apps, som vist på følgende billede, da den muliggør distribution af standardiseret autoritativt indhold til en bred målgruppe. I praksis bruges en kombination af alle de scenarier, der er nævnt tidligere i dette dokument.

![Kombination af scenarier](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Til dette skal du benytte følgende proces:

1. Brugere fra hvert datterselskab inviteres til Contosos Azure AD.
2. Herefter publiceres Power BI-appen for at give disse brugere adgang til de nødvendige data.
3. Til sidst åbner brugerne appen via det link, de har fået til at kunne få vist rapporterne.

Organisationer står over for flere vigtige udfordringer i forbindelse med denne struktur:

- Hvordan distribueres links til indhold i den overordnede organisations Power BI?
- Hvordan skal brugerne i datterselskaberne kunne få adgang til den datakilde, der er hostet af den overordnede organisation?

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribution af links til indhold i den overordnede organisations Power BI

Tre metoder bruges almindeligvis til at distribuere links til indhold. Den første og mest grundlæggende metode er at sende linket til appen til de relevante brugere eller at placere det på et SharePoint Online-websted, hvorfra det kan åbnes. Brugerne kan derefter forsyne linket med et bogmærke i deres browser for at få hurtigere adgang til de data, de har brug for.

Den anden metode er afhængig af funktionen til redigering og administration af Power BI-indhold på tværs af organisationer. Den overordnede organisation gør det muligt for brugerne fra datterselskaberne at få adgang til dens Power BI og styrer, hvad de kan få adgang til, via tilladelser. Dette giver adgang til Power BI Start, hvor brugeren fra datterselskabet kan få vist en omfattende liste over det indhold, der er delt med dem i den overordnede organisations lejer. Herefter gives URL-adressen til den overordnede organisations Power BI-miljø til brugerne i datterselskaberne.

Den sidste metode er at bruge en Power BI-app, der er oprettet i Power BI-lejeren for hvert datterselskab. Power BI-appen indeholder et dashboard med [felter, der er konfigureret med et eksternt link](../create-reports/service-dashboard-edit-tile.md#hyperlink). Når brugeren trykker på feltet, kommer vedkommende til den relevante rapport, det relevante dashboard eller en app i den overordnede organisations Power BI. Denne metode har den ekstra fordel, at appen kan installeres automatisk for alle brugere i datterselskabet og er tilgængelig for dem, når de logger på deres eget Power BI-miljø. En anden fordel ved denne metode er, at den fungerer godt sammen med Power BI-mobilapps, der kan åbne linket som standard. Du kan også kombinere denne metode med den anden metode for at gøre det lettere at skifte mellem Power BI-miljøer.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Sådan får brugerne i datterselskaberne adgang til den datakilde, der er hostet af den overordnede organisation

Analytikere i et datterselskab skal ofte oprette deres egne analyser ved hjælp af data, der er leveret af den overordnede organisation. I dette tilfælde bruges ofte clouddatakilder til at løse denne udfordring.

Den første metode udnytter [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) til at bygge et data warehouse til professionelt brug, der imødekommer behovet hos analytikere på tværs af den overordnet organisation og dens datterselskaber, som vist på følgende billede. Contoso kan hoste data og bruge funktioner som f.eks. sikkerhed på rækkeniveau for at sikre, at brugerne i hvert datterselskab kun kan få adgang til deres data. Analytikere i hver organisation kan få adgang til det pågældende data warehouse via Power BI Desktop og publicere de resulterende analyser i deres respektive Power BI-lejere.

![Sådan finder deling med Power BI-lejere sted](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


Den anden metode udnytter [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) til at bygge et relationelt data warehouse for at give adgang til data. Dette fungerer på samme måde som Azure Analysis Services-metoden, selvom nogle funktioner som f.eks. sikkerhed på rækkeniveau kan være sværere at implementere og vedligeholde på tværs af datterselskaber.

Der findes også mere avancerede metoder, men de ovenstående metoder er langt de mest almindelige.

### <a name="case-3-shared-environment-across-partners"></a>3. eksempel: delt miljø på tværs af partnere

Contoso indgår muligvis et partnerskab med en konkurrent for at udvikle en bil i fællesskab på et delt samlebånd, men distribuerer køretøjet under forskellige mærker eller i forskellige områder. Dette kræver omfattende samarbejde og medejerskab af data, intelligence og analyser på tværs af organisationerne. Denne struktur er også almindelig i konsulentbranchen, hvor et team af konsulenter kan foretage projektbaserede analyser for en klient.

![Delt miljø på tværs af partnere](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



I praksis er disse strukturer komplekse, som vist på følgende billede, og kræver vedligeholdelse af medarbejderne. Strukturens effektivitet afhænger af funktionen til redigering og administration af Power BI-indhold på tværs af organisationer, da det giver organisationer mulighed for at genbruge Power BI Pro-licenser, der er købt til deres respektive Power BI-lejere.

![Licenser og delt organisationsindhold](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Hvis du vil oprette en delt Power BI-lejer, skal du oprette et Azure Active Directory og købe mindst én Power BI Pro-brugerkonto til en bruger i det pågældende active directory. Denne bruger inviterer de relevante brugere til den delte organisation. I dette scenarie behandles Contosos brugere som eksterne brugere, når de arbejder i den delte organisations Power BI.

Processen er, som følger:

1. Den delte organisation oprettes som et nyt Azure Active Directory, og mindst én brugerkonto oprettes i den nye organisation. Brugeren skal have en Power BI Pro-licens tildelt.
2. Denne bruger opretter derefter en Power BI-lejer og inviterer de relevante brugere fra Contoso og partnerorganisationen. Brugeren opretter også alle delte dataaktiver, f.eks. Azure Analysis Services. Contoso og partnerens brugere kan få adgang til den delte organisations Power BI som gæstebrugere. Hvis de eksterne brugere får tilladelse til at redigere og administrere indhold i Power BI, kan de bruge Power BI-startsiden, bruge arbejdsområder, uploade eller redigere indhold og dele rapporter. Alle delte aktiver er typisk gemt og åbnes fra den delte organisation.
3. Afhængigt af hvordan parterne aftaler at samarbejde, er det muligt for hver organisation at udvikle deres egne privatejede data og analyser ved hjælp af delte data warehouse-aktiver. De kan distribuere dem til deres respektive interne brugere ved hjælp af deres interne Power BI-lejere.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Eksempel 4: distribution til hundredvis eller tusindvis af eksterne partnere

Contoso oprettede en stabilitetsrapport for kølere fra én leverandør og vil nu gerne oprette et sæt standardiserede rapporter for hundredvis af leverandører. På den måde kan Contoso sikre, at alle leverandører har den analyse, de har brug for til at foretage forbedringer eller rette defekter i produktionen.

![Distribution til mange partnere](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Når en organisation har brug for at distribuere standardiserede data og indsigt til så mange eksterne brugere/organisationer, kan de bruge scenariet med ad hoc- eller planlagt deling af Power BI-apps til at udvikle en BI-portal hurtigt og uden omfattende udviklingsomkostninger. Processen til oprettelse af en sådan Portal ved hjælp af en Power BI app er omfattet af casestudiet: oprettelse af en BI-Portal ved hjælp af Power BI + Azure AD B2B – trinvise instruktioner senere i dette dokument.

En almindelig variant af denne case er, når en organisation forsøger at dele indsigt med forbrugere, især når de ønsker at bruge Azure B2C sammen med Power BI. Power BI understøtter ikke Azure B2C som standard. Hvis du evaluerer muligheder for denne case, bør du overveje at benytte den anden alternative metode i afsnittet Almindelige alternative metoder senere i dette dokument.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Casestudie: oprettelse af en BI-Portal ved hjælp af Power BI + Azure AD B2B – trinvise instruktioner

Power BI-integration med Azure AD B2B giver Contoso en problemfri og nem måde at give gæstebrugere sikker adgang til sin BI-portal på. Contoso kan konfigurere dette med tre trin:

![Oprettelse af en portal](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Opret BI-portal i Power BI

    Den første opgave for Contoso er at oprette BI-portalen i Power BI. Contosos BI-portal består af en samling specialbyggede dashboards og rapporter, der vil blive gjort tilgængelige for mange interne brugere og gæster. Den anbefalede måde at gøre dette i Power BI på er ved at oprette en Power BI-app. Få mere at vide om [apps in Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- Contosos BI-team opretter et arbejdsområde i Power BI

    ![arbejdsområde](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Andre forfattere føjes til arbejdsområdet

    ![Tilføj forfattere](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- Indhold oprettes i arbejdsområdet

    ![Opret indhold i arbejdsområdet](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Nu, hvor indholdet er oprettet i et arbejdsområde, er contoso klar til at invitere gæstebrugere i partnerorganisationer til at bruge dette indhold.

2. Inviter gæstebrugere

    Der er to måder for Contoso at invitere gæstebrugere til dens BI-portal på i Power BI:

    * Planlagte invitationer
    * Ad hoc-invitationer

    **Planlagte invitationer**

    Når denne metode benyttes, inviterer Contoso gæstebrugere til deres Azure AD på forhånd og distribuerer derefter Power BI-indhold til dem. Contoso kan invitere gæstebrugere fra Azure-portalen eller ved hjælp af PowerShell. Her er trinnene til at invitere gæstebrugere fra Azure-portalen:

    - Contosos Azure AD-administrator navigerer til **Azure Portal > Azure Active Directory > Brugere og grupper > Alle brugere > Ny gæstebruger**.

    ![Gæstebruger](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Tilføj en invitationsmeddelelse til gæstebrugerne, og klik på Inviter.

    ![Tilføj invitation](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Hvis du vil invitere gæstebrugere fra Azure-portalen, skal du være administrator af Azure Active Directory for din lejer.

    Hvis Contoso vil invitere mange gæstebrugere, kan de gøre det ved hjælp af PowerShell. Contosos Azure AD-administrator gemmer alle mailadresserne for gæstebrugerne i en CSV-fil. Du kan få flere oplysninger i [Azure Active Directory B2B-samarbejdskode og PowerShell-eksempler](/azure/active-directory/b2b/code-samples) samt instruktioner.

    Efter invitationen modtager gæstebrugerne en mail med invitationslinket.

    ![Invitationslink](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Når gæste brugerne klikker på linket, kan de få adgang til indhold i contoso Azure AD-lejeren.

    > [!NOTE]
    > Det er muligt at ændre layoutet for invitationsmailen ved hjælp af brandingfunktionen i Azure AD, som beskrevet [her](/azure/active-directory/active-directory-b2b-invitation-email).


    **Ad hoc-invitationer**

    Hvad nu hvis Contoso ikke kender alle de gæstebrugere, det skal inviteres på forhånd? Eller hvad nu hvis analytikeren i Contoso, der oprettede BI-portalen, gerne selv vil distribuere indhold til gæstebrugerne? Vi understøtter også dette scenarie i Power BI med ad hoc-invitationer.

    Analytikeren kan bare tilføje de eksterne brugere på adgangslisten til appen, når de udgiver dem. Gæste brugerne modtager en invitation, og når de har accepteret den, bliver de automatisk omdirigeret til Power BI indhold.

    ![Tilføj ekstern bruger](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Invitationer kræves kun første gang, en ekstern bruger inviteres til din organisation.


3. Distribuer indhold

    Nu, hvor Contosos BI-team har oprettet BI-portalen og inviteret gæstebrugere, kan de distribuere deres portal til deres slutbrugere ved at give gæstebrugerne adgang til appen og publicere den. Power BI fuldfører automatisk navnene på de gæstebrugere, der tidligere er blevet føjet til Contoso-lejeren. Ad hoc-invitationer til andre gæstebrugere kan også tilføjes på dette tidspunkt.

    > [!NOTE]
    > Hvis der bruges sikkerhedsgrupper til at administrere adgang til appen for eksterne brugere, kan du bruge metoden med planlagte invitationer og dele applinket direkte med alle eksterne brugere, der skal have adgang til appen. I modsat fald kan den eksterne bruger muligvis ikke installere eller få vist indhold fra appen.

    Gæstebrugere får en mail med et link til appen.

    ![Invitationslink via mail](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Når gæstebrugerne klikker på dette link, bliver de bedt om at godkende med deres eget organisations-id.

    ![Logonside](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Når de er blevet godkendt, omdirigeres de til Contosos BI-app.

    ![Få vist delt indhold](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Gæstebrugerne kan derefter få adgang til Contosos app ved at klikke på linket i mailen eller forsyne linket med et bogmærke. Contoso kan også gøre det nemmere for gæstebrugere ved at føje dette link til en eksisterende ekstranetportal, der allerede benyttes af gæstebrugerne.

4. Næste trin

    Contoso var ved hjælp af en Power BI-app og Azure AD B2B i stand til hurtigt at oprette en BI-portal til sine leverandører på en måde, der ikke krævede nogen kode. Dette gør det markant lettere at distribuere standardiserede analyser til alle de leverandører, der har brug for det.

    Eksemplet viste, hvordan en enkelt almindelig rapport kan distribueres blandt leverandører, men der er mange flere muligheder i Power BI. Det er muligt at føje sikkerhed på rækkeniveau til rapporten og datamodellen for at sikre, at hver partner kun får vist de data, der er relevante for dem. I afsnittet Datasikkerhed for eksterne partnere senere i dette dokument beskrives denne proces i detaljer.

    Individuelle rapporter og dashboards skal ofte integreres i en eksisterende portal. Dette kan også gøres ved at genbruge mange af de teknikker, der er vist i eksemplet. I disse situationer kan det dog være lettere at integrere rapporter eller dashboards direkte fra et arbejdsområde. Processen til at invitere og tildele sikkerhedstilladelse til de relevante brugere forbliver uændret.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Under liggende: Hvordan er Lucy fra Supplier1 i stand til at få adgang til Power BI indhold fra Contosos lejer?

Nu, hvor vi har set, hvordan Contoso er i stand til at distribuere Power BI-indhold til gæstebrugere i partnerorganisationer uden problemer, skal vi se på, hvordan det fungerer under hjelmen.

Når contoso inviteres [lucy@supplier1.com](mailto:lucy@supplier1.com) til sin adresse, opretter Azure ad et link mellem [Lucy@supplier1.com](mailto:Lucy@supplier1.com) og CONTOSO Azure ad-lejeren. Dette link giver Azure AD besked om, at Lucy@supplier1.com kan få adgang til indhold i Contoso-lejeren.

Når Lucy prøver at få adgang til Contosos Power BI-app, kontrollerer Azure AD, at Lucy kan få adgang til Contoso-lejeren og giver derefter Power BI et token, der angiver, at Lucy er godkendt til at få adgang til indholdet i Contoso-lejeren. Power BI bruger dette token til godkendelse og til at sikre, at Lucy har adgang til Contosos Power BI-app.

![Bekræftelse og godkendelse](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Power BI's integration med Azure AD B2B fungerer sammen med alle mailadresser i virksomheden. Hvis brugeren ikke har en Azure AD-identitet, kan de blive bedt om at oprette en. På følgende billede vises forløbet i detaljer:

![Diagram over integrationsforløb](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


Det er vigtigt at registrere, at Azure AD-kontoen vil blive brugt eller oprettet i den eksterne parts Azure AD. Dette gør det muligt for Lucy at bruge deres eget Brugernavn og adgangskode, og deres legitimationsoplysninger stopper automatisk med at arbejde på andre lejere, når Lucy forlader virksomheden, når deres organisation også bruger Azure AD.

## <a name="licensing"></a>Licensering

Contoso kan vælge en af de tre metoder for at give gæstebrugere fra virksomhedens leverandører og partnerorganisationer licens til at få adgang til Power BI-indhold.

> [!NOTE]
> _Azure ad B2B's Free-niveauet er nok til at bruge Power bi med Azure ad B2B. Nogle avancerede Azure AD B2B-funktioner som dynamiske grupper kræver yderligere licenser. Du kan finde flere oplysninger i dokumentationen til Azure AD B2B:_[_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Tilgang 1: Contoso bruger Power BI Premium

Med denne metode køber Contoso Power BI Premium-kapacitet og tildeler indholdet i sin BI-portal til denne kapacitet. Det gør det muligt for gæstebrugere fra partnerorganisationer at få adgang til Contosos Power BI-app uden nogen Power BI-licens.

Eksterne brugere kan også kun forbruge indhold på samme måde som brugere med en "gratis" licens i Power BI, når de forbruger indhold i Power BI Premium.

Contoso kan også drage fordel af andre Power BI Premium-funktioner for sine apps, som f. eks. øgede opdaterings priser, kapacitet og store model størrelser.

![Yderligere funktioner](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Tilgang 2: contoso tildeler Power BI Pro licenser til gæstebrugere

Med denne metode tildeler Contoso Pro-licenser til gæstebrugere fra partnerorganisationer – dette kan gøres fra Contosos Microsoft 365 Administration. Det gør det muligt for gæstebrugere fra partnerorganisationer at få adgang til Contosos Power BI-app uden selv at købe en licens. Det kan være relevant i forbindelse med deling med eksterne brugere, hvis organisation endnu ikke bruger Power BI.

> [!NOTE]
> Contosos Pro-licens gælder kun for gæstebrugere, når de får adgang til indhold i Contoso-lejeren. Pro-licenser giver adgang til indhold, der ikke er i en Power BI Premium-kapacitet. Eksterne brugere med en Pro-licens er dog som standard begrænset til kun at forbruge. Dette kan ændres ved at bruge den fremgangsmåde, der er beskrevet i afsnittet _Aktivering af eksterne brugere til at redigere og administrere indhold i Power bi_ afsnit senere i dette dokument.

![Licensoplysninger](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Tilgang 3: gæstebrugere henter deres egen Power BI Pro-licens

Med denne metode tildeler Leverandør1 en Power BI Pro-licens til Lucy. De kan derefter få adgang til Contosos Power BI-app med denne licens. Da Lucy kan bruge deres Pro-licens fra deres egen organisation, når der opnås adgang til et eksternt Power BI miljø, kaldes denne tilgang nogle gange for at tage _din egen licens_ (BYOL). Hvis begge organisationer bruger Power BI, er dette den mest fordelagtige licenseringsmetode for den overordnede analyseløsning og minimerer den tid, der bruges på at tildele licenser til eksterne brugere.

> [!NOTE]
> Den Pro-licens, der tildeles til Lucy af Leverandør1, gælder for alle Power BI-lejere, hvor Lucy er en gæstebruger. Pro-licenser giver adgang til indhold, der ikke er i en Power BI Premium-kapacitet. Eksterne brugere med en Pro-licens er dog som standard begrænset til kun at forbruge. Dette kan ændres ved at bruge den fremgangsmåde, der er beskrevet i afsnittet _Aktivering af eksterne brugere til at redigere og administrere indhold i Power bi_ afsnit senere i dette dokument.

![Pro-licenskrav](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Datasikkerhed for eksterne partnere

Ofte, når Contoso arbejder med flere eksterne leverandører, er der brug for at sikre, at hver enkelt leverandør kun får vist data om sine egne produkter. Brugerbaseret sikkerhed og dynamisk sikkerhed på rækkeniveau gør det nemt at opnå dette i Power BI.

### <a name="user-based-security"></a>Brugerbaseret sikkerhed

En af de mest effektive funktioner i Power BI er sikkerhed på rækkeniveau. Denne funktion gør det muligt for Contoso at oprette en enkelt rapport og et enkelt datasæt, men stadig anvende forskellige sikkerhedsregler for hver bruger. Du kan finde en detaljeret forklaring i [Sikkerhed på rækkeniveau (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

Power BI-integration med Azure AD B2B gør det muligt for Contoso at tildele regler for sikkerhed på rækkeniveau til gæstebrugere, så snart de inviteres til Contoso-lejeren. Som vi har set før, kan Contoso tilføje gæstebrugere via enten planlagte invitationer eller ad hoc-invitationer. Hvis Contoso vil gennemtvinge sikkerhed på rækkeniveau, anbefales det at bruge planlagte invitationer til at tilføje gæstebrugerne på forhånd og tildele dem til sikkerhedsrollerne, før du deler indholdet. Hvis Contoso i stedet bruger ad hoc-invitationer, kan der være en kort periode, hvor gæstebrugerne ikke kan få vist nogen data.

> [!NOTE]
> Denne forsinkelse i at få adgang til data, der er beskyttet af RLS, når ad hoc-invitationer benyttes, kan resultere i supportanmodninger til dit it-team, fordi brugerne får vist rapporter/dashboards, der synes tomme eller ødelagte, når de åbner et link til deling i den mail, som de modtager. Det anbefales derfor at bruge planlagte invitationer i dette scenarie.**

Lad os gennemgå dette med et eksempel.

Som nævnt tidligere har Contoso leverandører i hele verden, og de vil være sikker på, at brugerne fra deres leverandørorganisationer får indsigt fra data for lige netop deres område.  Men brugere fra Contoso kan få adgang til alle data. I stedet for at oprette flere forskellige rapporter opretter Contoso en enkelt rapport og filtrerer dataene, på baggrund af den bruger der får dem vist.

![Delt indhold](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

For at sikre at Contoso kan filtrere data, der er baseret på den person, der opretter forbindelse, oprettes der to roller i Power BI Desktop. En til at filtrere alle dataene fra salgsområdet "Europa" og en anden for "Nordamerika".

![Administration af roller](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Når roller defineres i rapporten, skal en bruger tildeles til en bestemt rolle for at få adgang til data. Tildelingen af roller sker i Power BI-tjenesten (**Datasæt > Sikkerhed**).

![Angivelse af sikkerhed](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Dette åbner en side, hvor Contosos BI-team kan få vist de to roller, de har oprettet.  Nu kan Contosos BI-team tildele brugere til rollerne.

![Sikkerhed på rækkeniveau](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

I eksemplet contoso tilføjer vi en bruger i en partnerorganisation med mailadresse " [adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com) " til Europa-rollen:

![Sikkerhedsindstillinger på rækkeniveau](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Når dette løses af Azure AD, får Contoso vist navnet i vinduet, der nu er parat til at blive tilføjet:

![Vis roller](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Når denne bruger åbner den app, der er delt med dem, vises der nu kun en rapport med data fra Europa:

![Få vist indhold](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Dynamisk sikkerhed på rækkeniveau

Et andet interessant emne er at se, hvordan dynamisk sikkerhed på rækkeniveau (RLS) fungerer sammen med Azure AD B2B.

Dynamisk sikkerhed på rækkeniveau fungerer ved at filtrere dataene i modellen ud fra brugernavnet for den person, der opretter forbindelse til Power BI. I stedet for at tilføje flere forskellige roller for grupper af brugere, definerer du brugerne i modellen. Vi beskriver ikke mønsteret i detaljer her. Kasper de Jong har lavet en detaljeret beskrivelse af alle typer sikkerhed på rækkeniveau i [Snydeark til dynamisk sikkerhed i Power BI Desktop](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/) og i [dette whitepaper](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

Lad os se på et lille eksempel – Contoso har en enkel rapport om salg efter grupper:

![Eksempelindhold](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Nu skal denne rapport deles med to gæstebrugere og en intern bruger – den interne bruger kan få vist alt, men gæstebrugerne kan kun få vist de grupper, de har adgang til. Det betyder, at vi kun skal filtrere dataene for gæstebrugerne. Contoso bruger mønsteret for dynamisk sikkerhed på rækkeniveau som beskrevet i dette whitepaper og blogposten til at filtrere dataene korrekt. Det betyder, at Contoso selv føjer brugernavnene til dataene:

![Føj RLS-brugere til dataene selv](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Herefter opretter Contoso derefter den rette datamodel, der filtrerer dataene korrekt med de rette relationer:

![De relevante data vises](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Contoso skal for at filtrere dataene automatisk, afhængigt af hvem der er logget på, oprette en rolle, der giver adgang til den bruger, der opretter forbindelse. I dette tilfælde opretter Contoso to roller – den første er "securityrole", der filtrerer tabellen med brugere med det aktuelle brugernavn for den bruger, der er logget på Power BI (det fungerer selv for gæstebrugere i Azure AD B2B).

![Administrer roller](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso opretter også en anden "AllRole" for sine interne brugere, der kan få vist alt – denne rolle har ikke noget sikkerhedsprædikat.

Efter at have uploadet Power BI Desktop-filen til tjenesten kan Contoso tildele gæstebrugere til "SecurityRole" og interne brugere til "AllRole".

Når gæste brugerne åbner rapporten, kan de kun se salg fra gruppe A:

![Kun fra gruppe A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

Du kan se resultatet af funktionen USERNAME() og USERPRINCIPALNAME(), der begge returnerer gæstebrugernes mailadresser, i matrixen til højre.

Nu kan den interne bruger få vist alle dataene:

![Alle data vises](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Som du kan se, fungerer dynamisk sikkerhed på rækkeniveau sammen med både interne brugere og gæstebrugere.

> [!NOTE]
> Dette scenarie fungerer også, når du bruger en model i Azure Analysis Services. Azure Analysis Service er normalt forbundet med det samme Azure AD som Power BI – hvis det er tilfældet, kender Azure Analysis Services også de gæstebrugere, der er inviteret gennem Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>Oprettelse af forbindelse til data i det lokale miljø

Power BI giver Contoso mulighed for at udnytte datakilder i det lokale miljø som [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) eller [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) direkte takket være [datagatewayen i det lokale miljø](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). Det er også muligt at logge på disse datakilder med de samme legitimationsoplysninger, som bruges sammen med Power BI.

> [!NOTE]
> Når du installerer en gateway til at oprette forbindelse til din Power BI-lejer, skal du benytte en bruger, der er oprettet i din lejer. Eksterne brugere kan ikke installere en gateway og forbinde den med din lejer.

For eksterne brugere kan det være mere kompliceret, da de eksterne brugere som regel ikke er kendt af AD'et i det lokale miljø. Power BI tilbyder en løsning på dette ved at tillade Contoso-administratorer at knytte de eksterne brugernavne til interne brugernavne, som beskrevet i [Administrer din datakilde – Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Det kan f. eks. [lucy@supplier1.com](mailto:lucy@supplier1.com) være knyttet til [Lucy \_ supplier1 \_ com # EXT@contoso.com ](mailto:lucy_supplier1_com).

![Tilknytning af brugernavne](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Denne metode er fin, hvis Contoso kun har en håndfuld brugere, eller hvis Contoso kan knytte alle eksterne brugere til en enkelt intern konto. Til mere komplekse scenarier, hvor de enkelte brugere skal bruge deres egne legitimationsoplysninger, er der en mere avanceret metode, der benytter [brugerdefinerede attributter for AD](/previous-versions/windows/it-pro/windows-2000-server/cc961737(v=technet.10)) til at foretage tilknytningen, som beskrevet i [Administrer din datakilde – Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Dette gør det muligt for Contoso-administratoren at definere en tilknytning for alle brugere i dit Azure AD (også eksterne B2B-brugere).  Disse attributter kan angives via AD-objektmodellen ved hjælp af scripts eller kode, så Contoso fuldt ud kan automatisere tilknytningen på invitationer eller efter en planlagt kadence.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Mulighed for eksterne brugere for at redigere og administrere indhold i Power BI

Contoso kan gøre det muligt for eksterne brugere at bidrage med indhold i organisationen som beskrevet tidligere i afsnittet om redigering og administration af indhold i Power BI på tværs af organisationer.

> [!NOTE]
> Hvis brugeren skal kunne redigere og administrere indhold i din organisations Power BI, skal vedkommende have en Power BI Pro-licens i et andet arbejdsområde end Mit arbejdsområde. Brugerne kan få Pro-licenser, som det er beskrevet i _licens_ afsnittet for dette dokument.

Portalen Power BI Administration indeholder indstillingen **Tillad eksterne gæstebrugere at redigere og administrere indhold i organisationen** i lejerindstillingerne. Indstillingen er som standard deaktiveret, hvilket betyder, at eksterne brugere får en begrænset skrivebeskyttet adgang til indholdet som standard. Indstillingen gælder for de brugere, hvis UserType er angivet til Gæst i Azure AD. I nedenstående tabel beskrives de funktionsmåder, brugerne oplever, afhængigt af deres UserType og hvordan indstillingerne er konfigureret.

| **Brugertype i Azure AD** | **Indstillingen Tillad, at eksterne brugere kan redigere og administrere indhold** | **Adfærd** |
| --- | --- | --- |
| Gæst | Deaktiveret for brugeren (standard) | Forbrug pr. element, kun visning. Giver skrivebeskyttet adgang til rapporter, dashboards og apps, når de vises via en URL-adresse, der er blevet sendt til gæstebrugeren. Power BI-mobilapps giver en skrivebeskyttet visning til gæstebrugeren. |
| Gæst | Aktiveret for brugeren | Den eksterne bruger får adgang til den fulde oplevelse med Power BI, selvom visse funktioner ikke er tilgængelige for dem. Den eksterne bruger skal logge på Power BI ved hjælp af URL-adressen til Power BI-tjenesten med de lejeroplysninger, der er inkluderet. Brugeren får startoplevelsen og et Mit arbejdsområde og kan, afhængigt af tilladelserne, gennemse, få vist og oprette indhold. </br></br> Power BI-mobilapps giver en skrivebeskyttet visning til gæstebrugeren. |

> [!NOTE]
> Eksterne brugere i Azure AD kan også angives til UserType-medlem. Dette understøttes i øjeblikket ikke i Power BI.

Indstillingen i portalen Power BI Administration er vist på følgende billede.

![Administratorindstillinger](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Gæstebrugere får adgang til den skrivebeskyttede standardoplevelse og kan redigere og administrere indhold. Standardindstillingen er deaktiveret, hvilket betyder, at alle gæstebrugere får skrivebeskyttet adgang. Power BI-administratoren kan enten aktivere indstillingen for alle gæstebrugere i organisationen eller for bestemte sikkerhedsgrupper, der er defineret i Azure AD. På følgende billede har Contoso Power BI-administratoren oprettet en sikkerhedsgruppe i Azure AD for at administrere, hvilke eksterne brugere der kan redigere og administrere indhold i Contoso-lejeren.

Du kan hjælpe disse brugere med at logge på Power BI ved at give dem lejerens URL-adresse. Du kan finde lejerens URL-adresse ved at følge disse trin.

1. I den øverste menu i Power BI skal du vælge Hjælp ( **?** ) og derefter **Om Power BI**.
2. Se efter værdien ud for  **lejerens URL-adresse**. Dette er den URL-adresse for lejeren, som du kan dele med dine gæstebrugere.

    ![Lejerens URL-adresse](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Når du bruger funktionen Tillad, at eksterne gæstebrugere kan redigere og administrere indhold i organisationen, får de angivne gæstebrugere adgang til din organisations Power BI og kan få vist det indhold, som de har tilladelse til. De kan få adgang til startsiden, gennemse arbejdsområder, installere de apps, der er på adgangslisten, og bidrage med indhold til arbejdsområder. De kan oprette eller være administrator af arbejdsområder, der bruger den nye oplevelse i arbejdsområdet.

> [!NOTE]
> Når du bruger denne indstilling, skal du sørge for at gennemse afsnittet om Styring i dette dokument, da Azure AD-standardindstillingerne forhindrer gæstebrugerne i at bruge visse funktioner, f.eks. personvælgere, hvilket kan give en mindre god oplevelse.* *

De gæstebrugere, der har fået adgang via lejerindstillingen Tillad, at eksterne gæstebrugere kan redigere og administrere indhold i organisationen, har ikke adgang til alle funktioner. Hvis gæstebrugerne skal opdatere eller publicere rapporter, skal de bruge Power BI-tjenestens webgrænseflade, herunder Hent data, for at overføre Power BI Desktop-filer. Følgende funktioner understøttes ikke:

- Direkte publicering fra Power BI Desktop til Power BI-tjenesten.
- Gæstebrugere kan ikke bruge Power BI Desktop til at oprette forbindelse til tjenestedatasæt i Power BI-tjenesten.
- Klassiske arbejdsområder, der er knyttet til Microsoft 365 grupper: gæstebrugere kan ikke oprette eller være administratorer af disse arbejdsområder. De kan være medlemmer.
- Afsendelse af ad hoc-invitationer understøttes ikke for adgangslister for arbejdsområder.
- Power BI Publisher til Excel understøttes ikke for gæstebrugere.
- Gæstebrugere kan ikke installere en Power BI Gateway og forbinde den med din organisation.
- Gæstebrugere kan ikke installere apps, der publiceres til hele organisationen.
- Gæstebrugere kan ikke bruge, oprette, opdatere eller installere organisationsindholdspakker.
- Gæstebrugere kan ikke anvende Analysér i Excel.
- Gæstebrugere må ikke være @mentioned i kommentarer (denne funktionalitet tilføjes i en kommende version).
- Gæstebrugere må ikke benytte abonnementer (denne funktionalitet tilføjes i en kommende version).
- Gæstebrugere, der bruger denne funktion, skal have en arbejds- eller skolekonto. De gæstebrugere, der bruger personlige konti, har flere begrænsninger på grund af logonbegrænsninger.



## <a name="governance"></a>Styring

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Yderligere Azure AD-indstillinger, der påvirker oplevelser i Power BI, der er relateret til Azure AD B2B

Når du bruger Azure AD B2B-deling, styrer Azure Active Directory-administratoren aspekter af den eksterne brugeroplevelse. Dette administreres på siden med indstillinger for eksternt samarbejde i Azure Active Directory-indstillingerne for din lejer.

Du kan få flere oplysninger om indstillingerne her:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Indstillingen Tilladelserne for gæstebrugere er begrænsede er som standard angivet til Ja, og gæstebrugere i Power BI har derfor adgang til begrænsede funktioner især i forbindelse med deling, hvor personvælger-UI'er ikke fungerer for disse brugere. Det er vigtigt at samarbejde med din Azure AD-administrator for at angive indstillingen til Nej, som vist nedenfor, for at sikre en god oplevelse.* *

![Indstillinger for eksternt samarbejde](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Styring af invitationer til gæster

Power BI-administratorer kan administrere ekstern deling kun for Power BI ved at besøge Power BI Administration. Men administratorer kan også styre ekstern deling med forskellige Azure AD-politikker.  Disse politikker giver administratorer mulighed for at:

- Deaktiver invitationer til slutbrugere.
- Kun administratorer og brugere, der har rollen til at invitere gæster, kan invitere.
- Administratorer, brugere, der har rollen til at invitere gæster, og medlemmer kan invitere.
- Alle brugere, herunder gæster, kan invitere.

Du kan læse mere om disse politikker i [Deleger invitationer til Azure Active Directory B2B-samarbejde](/azure/active-directory/active-directory-b2b-delegate-invitations).

Alle handlinger i Power BI af eksterne brugere [overvåges i vores overvågningsportal](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).

### <a name="conditional-access-policies-for-guest-users"></a>Politikker for betinget adgang for gæstebrugere

Contoso kan håndhæve politikker for betinget adgang for gæstebrugere, der har adgang til indhold fra Contoso lejeren. Du kan finde detaljerede instruktioner i [Betinget adgang for B2B-samarbejdsbrugere](/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Almindelige alternative metoder

Selvom Azure AD B2B gør det nemt at dele data og rapporter på tværs af organisationer, er der flere andre fremgangsmåder, som ofte bruges, og som i visse tilfælde kan være bedre.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Alternativ mulighed 1: Opret identiske identiteter for partner brugere

Med denne indstilling skal Contoso oprette duplikerede id'er for hver partnerbruger i Contoso-lejeren, som vist på følgende billede. Contoso kan derefter i Power BI dele de relevante rapporter, dashboards eller apps med de tildelte identiteter.

![Angivelse af relevante tilknytninger og navne](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Årsager til at vælge denne mulighed:

- Eftersom brugerens identitet styres af din organisation, er eventuelle relaterede tjenester, f.eks mail, SharePoint, osv., også inden for din organisations kontrol. Dine it-administratorer kan nulstille adgangskoder, deaktivere adgang til konti eller overvåge aktiviteter i disse tjenester.
- De brugere, der benytter personlige konti til deres arbejde, kan ofte ikke få adgang til bestemte tjenester og har derfor muligvis brug for en organisationskonto.
- Nogle tjenester fungerer kun via din organisations brugere. Brug af Intune til at administrere indhold på personlige enheder/mobilenheder for eksterne brugere ved hjælp af Azure B2B er muligvis ikke muligt.

Årsager til, at denne mulighed ikke børe vælges:

- Brugere fra partnerorganisationer skal huske to sæt legitimationsoplysninger – ét for at få adgang til indhold fra deres egen organisation og det andet for at få adgang til indhold fra Contoso. Det er besværligt for disse gæstebrugere, og mange gæstebrugere bliver forvirrede over denne oplevelse.
- Contoso skal købe og tildele licenser pr. bruger til disse brugere. Hvis en bruger skal kunne modtage mail eller bruge Office-programmer, har vedkommende brug for de relevante licenser, herunder Power BI Pro for at redigere og dele indhold i Power BI.
- Contoso vil måske gennemtvinge strengere godkendelse og styringspolitikker for eksterne brugere sammenlignet med interne brugere. Contoso skal for at opnå dette oprette en intern terminologi for eksterne brugere, og alle Contoso-brugere skal være uddannet i denne terminologi.
- Når brugeren forlader organisationen, har vedkommende fortsat adgang til Contosos ressourcer, indtil Contoso-administratoren sletter vedkommendes konto manuelt.
- Contoso-administratorer skal administrere gæstens identitet, herunder oprettelse, nulstilling af adgangskoder osv.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Alternativ mulighed 2: Opret et brugerdefineret Power BI Embedded program ved hjælp af brugerdefineret godkendelse

En anden mulighed for Contoso er at oprette sit eget brugerdefinerede integrerede Power BI-program med brugerdefineret godkendelse (["Appen ejer data"](../developer/embedded/embed-sample-for-customers.md)). Selvom mange organisationer ikke har tid eller ressourcer til at oprette et brugerdefineret program til at distribuere Power BI-indhold til deres eksterne partnere, er dette den bedste metode for nogle organisationer og bør overvejes.

Organisationer har ofte eksisterende partnerportaler, der centraliserer adgang til alle organisationens ressourcer for partnere, som er isoleret fra interne organisatoriske ressourcer, hvilket giver partnerne en strømlinet oplevelse, da de understøtter mange partnere og deres individuelle brugere.

![Mange partnerportaler](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

I eksemplet ovenfor logger brugere fra hver enkelt leverandør på Contosos partnerportal, der bruger AAD som identitetsudbyder. Man kunne også bruge AAD B2B, Azure B2C, oprindelige identiteter eller slutte sig sammen med et vilkårligt antal andre identitetsudbydere. Brugeren skulle så logge på og få adgang til et partnerportalbuild ved hjælp af Azure Web App eller en lignende infrastruktur.

I webappen er Power BI-rapporter integreret fra en Power BI Embedded-udrulning. Webappen ville strømline adgangen til rapporterne og relaterede tjenester i en sammenhængende oplevelse med det formål at gør det nemt for leverandører at interagere med Contoso. Dette portalmiljø bør være isoleret fra Contosos interne AAD og Contosos interne Power BI-miljø for at sikre, at leverandører ikke kan få adgang til disse ressourcer. Data ville typisk være gemt i et separat partner-data warehouse for at sikre, at dataene isoleres. Denne isolation har fordele, da det begrænser antallet af eksterne brugere med direkte adgang til din organisations data, begrænser, hvilke data der potentielt kan være tilgængelige for den eksterne bruger, og begrænser, at data deles utilsigtet med eksterne brugere.

Hvis man bruger Power BI Embedded, kan man med portalen udnytte fordelagtige licenser og benytte det apptoken eller den overordnede bruger samt Premium-kapacitet, der blev købt i Azure-modellen, hvilket forenkler tildelingen af licenser til slutbrugerne og også kan skaleres op/ned, afhængigt af det forventede forbrug. Portalen kan tilbyde en samlet højere kvalitet og ensartet oplevelse, da partnerne har adgang til en enkelt portal, der er udviklet med en partners behov for øje. Desuden er Power BI Embedded-baserede løsninger typisk designet til at være med flere lejere, hvilket gør det lettere at sikre isolation mellem partnerorganisationer.

Årsager til at vælge denne mulighed:

- Det er nemmere at administrere, i takt med at antallet af partnerorganisationer vokser. Eftersom partnere føjes til en separat mappe, der er isoleret fra Contosos interne AAD-mappe, forenkles it-afdelingens opgaver med styring, og man undgår utilsigtet deling af interne data med eksterne brugere.
- Partnerportaler er typisk en brandet oplevelse med ensartede oplevelser på tværs af partnere, der er strømlinede for at opfylde behovene hos de typiske partnere. Contoso kan derfor tilbyde en bedre overordnet oplevelse til sine partnere ved at integrere alle de nødvendige tjenester i en enkelt portal.
- Licensomkostninger til avancerede scenarier som f.eks. redigering af indhold i Power BI Embedded er omfattet af den Power BI Premium, der er købt i Azure, og kræver ikke tildeling af Power BI Pro-licenser til disse brugere.
- Giver bedre isolation på tværs af partnere, hvis portalen er udviklet som en løsning med flere lejere.
- Partnerportalen indeholder ofte andre værktøjer til partnerne ud over Power BI-rapporter, dashboards og apps.

Årsager til, at denne mulighed ikke børe vælges:

- Der kræves en betydelig indsats for at bygge, drive og vedligeholde en sådan portal og derfor en betydelig investering i ressourcer og tid.
- Det kræver længere tid at implementere løsningen end at bruge B2B-deling, eftersom nøje planlægning og udførelse på tværs af flere arbejdsprocesser er påkrævet.
- Hvis der kun er et mindre antal partnere, kan den indsats, der kræves til dette alternativ, sandsynligvis ikke forsvares.
- Samarbejde med ad hoc-deling er det primære scenarie for din organisation.
- Rapporterne og dashboardene er forskellige fra partner til partner. Dette alternativ kræver megen administration i forhold til blot at dele direkte med partnerne.



## <a name="faq"></a>Ofte stillede spørgsmål

**Kan contoso sende en invitation, der automatisk indløses, så brugeren kun er "klar til at gå i gang"? Eller skal brugeren altid klikke dig igennem til indløsnings-URL-adressen?**

Slutbrugeren skal altid klikke sig videre til samtykkeerklæringen, før vedkommende kan få adgang til indhold.

Hvis du inviterer mange gæstebrugere, anbefaler vi, at du uddelegerer dette fra dine administrative Azure AD-kerneopgaver ved [at føje en bruger til rollen, så vedkommende kan invitere gæster i ressourceorganisationen](/azure/active-directory/active-directory-b2b-add-guest-to-role). Denne bruger kan invitere andre brugere i partnerorganisationen ved at bruge logon-UI'en, PowerShell-scripts eller API'er. Dette reducerer dine administrative Azure AD-opgaver med at invitere eller sende invitationer til brugere i partnerorganisationen.

**Kan Contoso gennemtvinge multifaktorgodkendelse for gæstebrugere, hvis partnerne ikke har multifaktorgodkendelse?**

Ja. Du kan finde flere oplysninger i [Betinget adgang for B2B-samarbejdsbrugere](/azure/active-directory/active-directory-b2b-mfa-instructions).

**Hvordan fungerer B2B-samarbejdet, når den inviterede partner bruger et federeret netværk til at tilføje sin egen godkendelse i det lokale miljø?**

Hvis partneren har en Azure AD-lejer, der er forbundet med godkendelsesinfrastrukturen i det lokale miljø, opnås enkeltlogon automatisk. Hvis partneren ikke har en Azure AD-lejer, kan der oprettes en Azure AD-konto for nye brugere.

**Kan jeg invitere gæstebrugere med forbrugermailkonti?**

Power BI understøtter invitation af gæstebrugere med forbrugermailkonti. Dette omfatter domæner som f.eks. hotmail.com, outlook.com og gmail.com. Disse brugere kan dog opleve begrænsninger, som brugere med arbejds- eller skolekonti ikke oplever.