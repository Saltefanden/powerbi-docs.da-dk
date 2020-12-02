---
title: Tip til udarbejdelse af skabelonapps i Power BI
description: Tip til udarbejdelse af forespørgsler, datamodeller, rapporter og dashboards for at skabe gode skabelonprogrammer
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
ms.openlocfilehash: bb48b92df81a49ee687376ee9f53428c10171b80
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410108"
---
# <a name="tips-for-authoring-template-apps-in-power-bi"></a>Tip til udarbejdelse af skabelonapps i Power BI

Når du [udarbejder dit skabelonprogram](service-template-apps-create.md) i Power BI, er en del af det logistikken til oprettelse af arbejdsområdet, test af det og produktion. Men en anden vigtige del er naturligvis at udarbejde rapporten og dashboardet. Vi kan opdele processen for udarbejdelse i fire primære komponenter. Når du arbejder på disse komponenter, hjælper det dig med at oprette det bedst mulige skabelonprogram:

* Med **forespørgsler** kan du [oprette forbindelse til](desktop-connect-to-data.md) og [transformere](../transform-model/desktop-query-overview.md) dataene samt definere [parametre](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/). 
* I **datamodellen** opretter du [relationer](../transform-model/desktop-create-and-manage-relationships.md), [målinger](../transform-model/desktop-measures.md) og forbedringer af Spørgsmål og svar.  
* **[Rapportsider](../create-reports/desktop-report-view.md)** indeholder visualiseringer og filtre, som kan hjælpe med at give indsigt i dine data.  
* **[Dashboards](../consumer/end-user-dashboards.md)** og [felter](../create-reports/service-dashboard-create.md) hjælper med at give et overblik over den inkluderede indsigt.
* Eksempeldata gør det nemt at finde din app umiddelbart efter installationen.

Du kender hver enkelt del som eksisterende funktioner i Power BI. Når du udarbejder et skabelonprogram, er der flere ting, du bør overveje for hver enkelt del. Du kan finde flere oplysninger under de enkelte afsnit herunder.

<a name="queries"></a>

## <a name="queries"></a>Forespørgsler
I forbindelse med skabelonprogrammer bruges forespørgsler, der er udviklet i Power BI Desktop, til at oprette forbindelse til datakilden og importere data. Disse forespørgsler kræves for at returnere et ensartet skema og understøttes i forbindelse med opdatering af Planlagte data.

### <a name="connect-to-your-api"></a>Opret forbindelse til din API
Du kommer i gang ved at oprette forbindelse til din API fra Power BI Desktop, så du kan begynde at udarbejde dine forespørgsler.

Du kan bruge de dataconnectorer, der findes i Power BI Desktop, til at oprette forbindelse til din API. Du kan bruge Web Data Connector (Hent Data -> Web) til at oprette forbindelse til din Rest API eller OData-connectoren (Hent Data -> OData-feed) for at oprette forbindelse til dit OData-feed.

> [!NOTE]
> Skabelonapps understøtter i øjeblikket ikke brugerdefinerede connectorer. Det anbefales, at du undersøger det ved at bruge Odatafeed Auth 2.0 som en hjælp til nogle forbindelses-use cases eller indsender din connector til certificering. Du kan finde flere oplysninger om, hvordan du udvikler en connector og certificerer den, i [dokumentationen til dataconnectorer](https://aka.ms/DataConnectors).

### <a name="consider-the-source"></a>Tag højde for kilden
Forespørgsler definerer de data, der inkluderes i datamodellen. Afhængigt af størrelsen af dit system bør disse forespørgsler også inkludere filtre for at sikre, at dine kunder arbejder med en håndterbar størrelse, der passer til dit forretningsscenarie.

Power BI-skabelonprogrammer kan udføre flere forespørgsler parallelt og for flere brugere samtidigt.  Planlæg din strategi for begrænsning og samtidighed, og spørg os, hvordan du kan gøre dit skabelonprogram fejltolerant.

### <a name="schema-enforcement"></a>Håndhævelse af skema
Kontrollér, at dine forespørgsler er robuste i forhold til ændringer i systemet. Ændringer i skemaer ved opdatering kan ødelægge modellen. Hvis kilden kunne returnere resultatet null eller mangler skema for nogle forespørgsler, bør du overveje at returnere en tom tabel eller en meningsfuld brugerdefineret fejlmeddelelse.

### <a name="parameters"></a>Parametre
[Parametre](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) i Power BI Desktop giver brugerne mulighed for at angive inputværdier, der tilpasser de data, som brugeren har hentet. Overvej parametrene fra starten, så du undgår at skulle lave tingene om, efter du har brugt tid på at oprette detaljerede forespørgsler eller rapporter.

> [!NOTE]
> Skabelonprogrammer understøtter alle parametre, undtagen Any og Binary.
>

### <a name="additional-query-tips"></a>Flere tip til forespørgsler

* Kontrollér, at alle kolonner er skrevet korrekt.
* Kolonner har informative navne (se [Spørgsmål og svar](#qa)).  
* Overvej at bruge funktioner eller forespørgsler til delt logik.  
* Niveauer for beskyttelse af personlige oplysninger understøttes i øjeblikket ikke i tjenesten. Hvis du får vist en prompt om niveauer for beskyttelse af personlige oplysninger, skal du muligvis omskrive forespørgslen til at bruge relative stier.  

## <a name="data-models"></a>Datamodeller

En veldefineret datamodel sikrer, at dine kunder nemt og intuitivt kan interagere med skabelonprogrammet. Opret datamodellen i Power BI Desktop.

> [!NOTE]
> Du bør udføre meget af den grundlæggende udformning (indtastning, kolonnenavne) i [forespørgslerne](#queries).

### <a name="qa"></a>Spørgsmål og svar
Udformningen har også indflydelse på, i hvor høj grad Spørgsmål og svar kan levere resultater til dine kunder. Sørg for at føje synonymer til ofte anvendte kolonner, og at du har navngivet dine kolonner korrekt i [forespørgslerne](#queries).

### <a name="additional-data-model-tips"></a>Flere tip til datamodeller

Sørg for, at du har gjort følgende:

* Anvendt formatering på alle værdikolonner. Anvendt typer i forespørgslen.  
* Anvendt formatering på alle målinger.
* Angivet standardopsummering. Specielt "Opsummer ikke", når det er relevant (f.eks. til entydige værdier).  
* Angivet datakategori, når det er relevant.  
* Angivet relationer efter behov.  

## <a name="reports"></a>Rapporter
Med rapportsider får du yderligere indsigt i de data, der er inkluderet i dit skabelonprogram. Brug siderne i rapporterne til at besvare de vigtigste forretningsspørgsmål, som dit skabelonprogram prøver at håndtere. Opret rapporten ved hjælp af Power BI Desktop.


### <a name="additional-report-tips"></a>Flere tip til rapporter

* Brug mere end én visualisering pr. side, så du kan bruge krydsfiltrering.  
* Juster visualiseringerne omhyggeligt (ingen overlapning).  
* Siden er angivet til tilstanden "4:3" eller "16:9" for layout.  
* Alle de viste sammenlægninger giver mening numerisk (gennemsnit, entydige værdier).  
* Udsnit giver rationelle resultater.  
* Logo findes som minimum øverst i rapporten.  
* Elementer er i videst muligt omfang holdt i klientens farveskema.  

<a name="dashboard"></a>

## <a name="dashboards"></a>Dashboards
Dine kunder bruger primært dashboardet til at interagere med dit skabelonprogram. Den bør indeholde en oversigt over det indhold, der er inkluderet, specielt vigtige målepunkter til dit forretningsscenarie.

Når du vil oprette et dashboard for dit skabelonprogram, skal du blot uploade din PBIX via Hent data > Filer eller udgive direkte fra Power BI Desktop.


### <a name="additional-dashboard-tips"></a>Flere tip til dashboard

* Bevar det samme tema, når du fastgør, så felterne på dashboardet er ensartede.  
* Fastgør et logo til temaet, så brugerne ved, hvor pakken er fra.  
* Det anbefalede layout, når du arbejder med de fleste skærmopløsninger, er en bredde på 5-6 små felter.  
* Alle dashboardfelter skal have relevante titler/undertitler.  
* Overvej at anvende grupperinger på dashboardet til forskellige scenarier enten lodret eller vandret.  

## <a name="sample-data"></a>Eksempeldata
Skabelonapps, som bruges i fasen til oprettelse af apps, ombryder de cachelagrede data i arbejdsområdet som en del af appen:

* Det gør det muligt for installationsprogrammet at forstå funktionaliteten i og formålet med appen, før der oprettes forbindelse til data.
* Skaber en oplevelse, der får installationsprogrammet til at udforske appfunktioner yderligere, hvilket medfører oprettelse af forbindelse til appdatasættet.

Det anbefales, at du har gode eksempeldata, før du opretter appen. Sørg for, at din apprapport og dine dashboards er udfyldt med data.

## <a name="publishing-on-appsource"></a>Publicering på AppSource
Skabelonapps kan publiceres på AppSource. Følg disse retningslinjer, før du sender din app til AppSource:

* Sørg for at oprette en skabelonapp med engagerende eksempeldata, som kan hjælpe den person, der installerer appen, med at forstå, hvad appen kan gøre (en tom rapport og et tomt dashboard godkendes ikke).
Skabelonapps understøtter eksempeldata kun for apps. Husk at markere afkrydsningsfeltet for den statiske app. [Få mere at vide](./service-template-apps-create.md#define-the-properties-of-the-template-app)
* Få en vejledning, som valideringsteamet skal følge, der omfatter legitimationsoplysninger og parametre, som kræves for at oprette forbindelse til data.
* Programmet skal inkludere et appikon i Power BI og på dit CPP-tilbud. [Få mere at vide](./service-template-apps-create.md#define-the-properties-of-the-template-app)
* Konfigureret landingsside. [Få mere at vide](./service-template-apps-create.md#define-the-properties-of-the-template-app)
* Sørg for at følge dokumentationen på [Partnercenter -> Tilbud om Power BI-program](/azure/marketplace/partner-center-portal/create-power-bi-app-offer).
* Hvis et dashboard er en del af din app, skal du sørge for, at det ikke er tomt.
* Installér appen ved hjælp af linket til appen, før du udgiver den, og kontrollér, at du kan oprette forbindelse til datasættet, og at appoplevelsen er, som du forventer.
* Før du uploader pbix til arbejdsområdet for skabelonen, skal du huske at fjerne alle unødvendige forbindelser.
* Følg [Bedste praksis for design af rapporter og visuals](../visuals/power-bi-report-visualizations.md) for Power BI for at opnå maksimal indflydelse på dine brugere og blive godkendt til distribution.
<!--- * In general, only application with valuable functionality can be approved for general use on AppSource. Application with sample data content only must have either a guidance or statistical value.) -->

## <a name="create-a-download-link-for-the-app"></a>Opret et downloadlink til appen

Når du har publiceret skabelonappen på AppSource, kan du overveje at oprette et downloadlink fra dit websted til enten:
* AppSource-downloadside – kan ses offentligt, få linket fra din AppSource-side.
* Power BI – kan ses af en Power BI-bruger.

Hvis du vil omdirigere en bruger til appens downloadlink i Power BI, skal du se følgende kodeeksempel: [GitHub-lager](https://github.com/microsoft/Template-apps-examples).

[![Downloadlink til app](media/service-template-apps-tips/service-template-apps-tips-download.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)

## <a name="next-steps"></a>Næste trin

[Hvad er Power BI-skabelonapps?](service-template-apps-overview.md)
