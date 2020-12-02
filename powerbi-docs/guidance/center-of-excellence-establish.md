---
title: Etabler et Center of Excellence
description: Få mere at vide om, hvordan et Center of Excellence hjalp Microsoft med at oprette en standardiseret analyse- og dataplatform til at give adgang til indsigt med den rigtige driftsmodel, engagement af interessenter samt delte og dedikerede investeringer.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: 90de33f85c0ede28b14e651414c311e4986a2172
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394560"
---
# <a name="establish-a-center-of-excellence"></a>Etabler et Center of Excellence

Denne artikel er rettet mod it-medarbejdere og it-ledere. Du får mere at vide om, hvordan du konfigurerer et COE (Center of Excellence) i din organisation, og hvordan Microsoft har konfigureret sit center.

Nogle har den fejlagtige antagelse, at et COE blot er en helpdesk – det er dog langt fra virkeligheden.

Generelt er et BI- og analyse-COE et team af medarbejdere, der er ansvarlige for at oprette og vedligeholde en BI-platform. De er også ansvarlige for at skabe en enkelt kilde til sandheden og definere et sæt ensartede målepunkter, der gælder hele virksomheden, for at låse op for og give hurtigere adgang til indsigt. Et COE er dog et bredt begreb. Det kan derfor implementeres og administreres på forskellige måder, og dets struktur og omfang kan variere fra organisation til organisation. Et COE er dog altid en robust platform, der leverer de rette data og den rette indsigt til de rette personer på det rette tidspunkt. Ideelt set skal det også være med til at fremme udbredelsen af centeret samt uddannelse og support. Hos Microsoft beskrives det som _[disciplin centralt](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)_ , og det leveres som vores BI-platform og vores enkelte kilde til sandheden.

I større organisationer kan du finde flere COE'er, hvor det centrale COE er blevet _udvidet_ med satellit-COE'er – ofte på afdelingsniveau. På denne måde er et satellit-COE en gruppe eksperter, der kender taksonomier og definitioner, og som ved, hvordan kernedata transformeres til noget, der giver mening _for deres afdeling_. Afdelingsanalytikere tildeles tilladelser til kernedata, og de har tillid til disse data og bruger dem i deres egne rapporter. De bygger løsninger, der er baseret på omhyggeligt forberedte kernedimensioner, -fakta og -forretningslogik. De kan til tider også udvide COE'et med mindre afdelingsspecifikke datasæt og forretningslogik. Det er vigtigt at bemærke, at satellit-COE'er aldrig fungerer uden forbindelse eller isoleret. Hos Microsoft fremmer satellit-COE'er _[fleksibiliteten hele vejen rundt](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ .

Hvis afdelinger vil have succes med dette udvidede scenarie, er de dog nødt til at _betale for at være med_. Afdelingerne skal med andre ord investere økonomisk i det centrale COE. På den måde er der ingen risiko for, at de ikke får den andel, de har krav på, eller at deres krav nedprioriteres.

Et centralt COE skal kunne skaleres for at opfylde afdelingens behov. Når flere datasæt er blevet onboardet, åbner det op for stordriftsfordele. Hos Microsoft blev det hurtigt tydeligt, at det er mere økonomisk at arbejde centralt, og det giver resultater hurtigere. Efterhånden som hvert nyt emneområde blev onboardet, oplevede vi endnu flere stordriftsfordele, der gjorde det muligt at udnytte og bidrage på tværs af hele platformen, hvilket styrkede den underliggende datakultur.

Tag følgende et eksempel: Vores BI-platform leverer kernedimensioner, -fakta og -forretningslogik i forbindelse med økonomi, salg og marketing. Den definerer også hundredvis af KPI'er (nøgletalsindikatorer). Nu har en analytiker i Power Platform-virksomheden brug for at forberede et dashboard til ledelsen. Nogle af KPI'erne, f.eks. indtægter og pipelines, stammer direkte fra BI-platformen. Der er dog andre, der er baseret på mere detaljerede behov i virksomheden. Et sådant behov er f.eks. en KPI om indførelsen af en bestemt Power BI-funktion hos brugerne: dataflows. Analytikeren producerer derfor en [sammensat model](composite-model-guidance.md) i Power BI for at integrere kernedata i BI-platformen med afdelingsdata. Derefter tilføjer vedkommende forretningslogik for at definere afdelings-KPI'er. Til sidst udarbejdes et ledelsesdashboard baseret på den nye model, som udnytter COE-ressourcerne fra hele virksomheden, som er forstærket med lokal viden og lokale data.

En opdeling af ansvarsområder mellem det centrale COE og satellit-COE'er giver afdelingsanalytikere mulighed for at fokusere på at skabe banebrydende resultater, frem for at skulle administrere en dataplatform. Nogle gange kan der også være en gensidig fordelagtig relation mellem satellit-COE'erne og det centrale COE. Et satellit-COE kan f.eks. definere nye målepunkter, der har vist sig at være nyttige for deres afdeling, men som også er fordelagtige for hele virksomheden, og som er tilgængelige fra – og understøttes af – det centrale COE.

## <a name="bi-platform"></a>BI-platform

I din organisation har COE'et måske et andet navn, f.eks. BI-teamet eller -gruppen. Det er ikke navnet, men resultaterne der tæller. Hvis du ikke har et formelt team, anbefaler vi, at du opretter et team bestående af jeres dygtigste BI-eksperter til at etablere BI-platformen.

Hos Microsoft kaldes COE'et for BI-platformen. Det har mange interessentgrupper, der repræsenterer forskellige afdelinger i virksomheden, f.eks. økonomi, salg og marketing. Det er organiseret til at køre [delte egenskaber](#shared-capabilities) og [dedikerede leveringer](#dedicated-deliveries).

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="I diagrammet vises de delte egenskaber og dedikerede leveringer, som beskrives i følgende afsnit.":::

### <a name="shared-capabilities"></a>Delte egenskaber

Delte egenskaber er nødvendige for at oprette og administrere BI-platformen. De understøtter alle de interessentgrupper, der finansierer platformen. De omfatter følgende teams:

- **Den grundlæggende udvikling af platformen:** Vi udviklede BI-platformen med en teknisk indgangsvinkel. Det er i virkeligheden et sæt strukturer, der understøtter dataindtagelse, behandling for at forbedre dataene og levering af disse data i semantiske BI-modeller til analyseforbrug. Teknikerne er ansvarlige for det tekniske design og implementering af BI-platformens kernefunktioner. De designer og implementerer f.eks. datapipelines.
- **Infrastruktur og hosting:** It-teknikere er ansvarlige for klargøring og administration af alle Azure-tjenester.
- **Support og drift:** Dette team holder platformen kørende. Support varetager brugernes behov for f.eks. datatilladelser. Driftsteamet holder platformen kørende, så serviceaftalerne (SLA'er) er opfyldt, og der kan kommunikeres uden forsinkelser eller fejl.
- **Udgivelsesadministration:** Tekniske programadministratorer udgiver ændringer. Ændringer kan være alt lige fra opdateringer af platformsstrukturen til ændringsanmodninger, der foretages for semantiske BI-modeller. De er den sidste forsvarslinje, der skal sikre, at ændringer ikke ødelægger noget.

### <a name="dedicated-deliveries"></a>Dedikerede leveringer

Der er et dedikeret leveringsteam for hver gruppe interessenter. Det består typisk af en datatekniker, en analysetekniker og en teknisk programadministrator – der finansieres af deres gruppe af interessenter.

## <a name="bi-team-roles"></a>BI-teamroller

Hos Microsoft drives vores BI-platform af skalerbare teams bestående af medarbejdere. Disse teams justeres i forhold til dedikerede og delte ressourcer. I dag har vi følgende roller:

- **Programadministratorer:** Programadministratorer er en dedikeret ressource. De fungerer som den primære kontakt mellem BI-teams og interessenter. Det er deres job at oversætte interessenternes forretningskrav til en teknisk specifikation. De administrerer desuden prioriteringen af interessenternes leveringer.
- **Databaseansvarlige:** De er en dedikeret ressource, der er ansvarlig for at onboarde nye datasæt i det centrale data warehouse. Onboarding af et datasæt kan omfatte konfiguration af kompatible dimensioner, tilføjelse af forretningslogik og brugerdefinerede attributter samt standardnavne og formatering.
- **Analyseansvarlige:** De er en dedikeret ressource, der er ansvarlige for design og udvikling af semantiske BI-modeller. De bestræber sig på at anvende en konsistent arkitektur ved hjælp af standardnavngivning og -formatering. Optimering af ydeevnen er en vigtig del af deres rolle.
- **Drift og infrastruktur:** De er en delt ressource, der er ansvarlig for administration af job og datapipelines. De er også ansvarlige for administration af Azure-abonnementer, Power BI-kapaciteter, virtuelle maskiner og datagateways.
- **Support:** De er en delt ressource, der er ansvarlige for at skrive dokumentation, organisere træning, kommunikere ændringer af semantiske BI-modeller og besvare brugernes spørgsmål.

## <a name="governance-and-compliance"></a>Styring og overholdelse af angivne standarder

For hver interessentgruppe varetager programadministratorer styring og oversigt på tværs af programmerne. Det overordnede mål er at sikre, at investeringer i it-afdelingen genererer forretningsmæssig værdi og mindsker risici. Styringsudvalgsmøder afholdes jævnligt for at følge op på fremskridt og godkende vigtige initiativer.

## <a name="grow-your-own-community"></a>Skab vækst i dit eget community

Etabler et community, og skab vækst i det, i din organisation ved at gøre følgende:

- Afhold regelmæssigt begivenheder af typen "Tid på kontoret", hvor der afsættes tid med BI-teamet, så folk kan stille spørgsmål, komme med forslag, dele idéer og tilmed afgive klager.
- Opret en Teams-kanal for at yde support og opfordre alle til at stille og besvare spørgsmål.
- Kør og fremhæv uformelle brugergrupper, og anspor medarbejderne til at præsentere eller deltage.
- Kør mere formelle træningsbegivenheder for specifikke produkter og selve BI-platformen. Overvej at levere [Power BI-dashboard på en dag](https://powerbi.microsoft.com/diad/), der er tilgængelig som en gratis kursuspakke, hvilket er en fantastisk måde at introducere medarbejderne til Power BI på for første gang.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [BI-løsningsarkitektur i COE'et](center-of-excellence-business-intelligence-solution-architecture.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

I den [næste artikel i denne serie](center-of-excellence-business-intelligence-solution-architecture.md) kan du finde flere oplysninger om BI-løsningsarkitekturen i COE og de forskellige udrullede teknologier.

### <a name="professional-services"></a>Professionelle tjenester

Der findes certificerede Power BI-partnere, som kan hjælpe din organisation med at lykkes, når du konfigurerer et COE. De kan give dig omkostningseffektiv træning eller overvågning af dine data. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).

Du kan også interagere med erfarne konsulentpartnere. De kan hjælpe dig med at [vurdere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [evaluere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) eller [implementere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI.
