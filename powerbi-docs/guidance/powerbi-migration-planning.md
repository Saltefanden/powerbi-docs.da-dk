---
title: Planlæg udrulning for at migrere til Power BI
description: Vejledning i planlægning af udrulning, når der migreres til Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: f6b781d6b3f87587e7734d5f842a013fd6fb5c19
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086688"
---
# <a name="plan-deployment-to-migrate-to-power-bi"></a>Planlæg udrulning for at migrere til Power BI

I denne artikel beskrives **fase 2**, som omhandler planlægning af migrering til en enkelt Power BI-løsning.

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="Billede, der viser faserne i en migrering til Power BI. Der fokuseres på fase 2 i denne artikel.":::

> [!NOTE]
> Du kan finde en komplet forklaring af ovenstående grafik under [Oversigt over migrering til Power BI](powerbi-migration-overview.md).

Fokus i trin 2 er på definitionen af, hvordan kravene, som blev defineret i fase 1, bruges til at migrere en løsning til Power BI.

Outputtet fra fase 2 omfatter så mange specifikke beslutninger som muligt for at vejlede udrulningsprocessen.

Denne form for beslutningstagning er en iterativ og ikke-lineær proces. En del af planlægningen vil allerede være udført under [trinnene forud for migreringen](powerbi-migration-pre-migration-steps.md). Erfaringer fra POC (proof of concept), som er beskrevet i [fase 3](powerbi-migration-proof-of-concept.md), kan forekomme parallelt med planlægningen af udrulningen. Selv under oprettelsen af løsningen, som beskrevet i [fase 4](powerbi-migration-create-validate-content.md), kan der fremkomme yderligere oplysninger, som påvirker beslutningerne om udrulningen.

> [!IMPORTANT]
> Fase 1-5 repræsenterer aktiviteter, der er relateret til en bestemt løsning. Der er beslutninger og aktiviteter på organisationsniveau/lejerniveau, som påvirker processen på løsningsniveau. Nogle af disse planlægningsaktiviteter på et højere niveau er beskrevet i artiklen [Oversigt over migrering til Power BI](powerbi-migration-overview.md). Hvis det er relevant, skal beslutninger tages på organisationsniveau for at sikre effektivitet og ensartethed.

> [!TIP]
> De emner, denne artikel omhandler, gælder også for et Power BI-standardimplementeringsprojekt.

## <a name="choose-power-bi-product"></a>Vælg et Power BI-produkt

En af de første beslutninger, der skal træffes, er at vælge det rette Power BI-produkt. Det er valget mellem [Power BI-tjenesten](../fundamentals/power-bi-service-overview.md) eller [Power BI-rapportserver](../report-server/get-started.md). Når indholdet er blevet publiceret, bliver mange andre muligheder tilgængelige, f.eks. integrering, levering på mobil og mailabonnementer.

Du kan finde flere oplysninger om arkitekturovervejelser i **afsnit 3** af [Whitepaper om planlægning af en udrulning af Power BI i en virksomhed](https://aka.ms/PBIEnterpriseDeploymentWP).

> [!CAUTION]
> Hvis du er fristet til at sætte din lid til at bruge Power BI Desktop-filer, der er gemt i et filsystem, skal du være opmærksom på, at det ikke er den optimale tilgang. Brug af Power BI-tjenesten (eller Power BI-rapportserver) har betydelige fordele i forbindelse med sikkerhed, indholdsdistribution og samarbejde. Det er også muligt at overvåge aktiviteter ved hjælp af Power BI-tjenesten.

## <a name="decide-on-workspace-management-approach"></a>Beslut dig for en tilgang til administration af arbejdsområder

[Arbejdsområder](../collaborate-share/service-new-workspaces.md) er et kernekoncept i Power BI-tjenesten, hvilket gør administration af arbejdsområder til en vigtig del af planlægningen. Spørgsmål, der skal stilles, omfatter:

- Er der behov for et nyt arbejdsområde til denne nye løsning?
- Er der behov for særskilte arbejdsområder for at imødekomme udvikling, test og produktion?
- Skal der bruges særskilte arbejdsområder til data og rapporter, eller er et enkelt arbejdsområde tilstrækkeligt? Der er adskillige fordele ved særskilte arbejdsområder, især i forbindelse med sikring af datasæt. Når det er nødvendigt, kan de administreres separat fra de brugere, der publicerer rapporter.
- Hvad er sikkerhedskravene til arbejdsområdet? Det påvirker planlægningen af [arbejdsområderoller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). Hvis en app bruges af forbrugere af indhold, administreres [tilladelser til appen](../collaborate-share/service-create-distribute-apps.md#publish-your-app) separat fra arbejdsområdet. Særskilte tilladelser for appseere muliggør yderligere fleksibilitet i forbindelse med sikkerhedskrav til skrivebeskyttede forbrugere af rapporter eller dashboards.
- Kan eksisterende grupper bruges til at sikre det nye indhold? Både Azure Active Directory og Microsoft 365-grupper understøttes. Når grupper er justeret i forhold til eksisterende processer, gør brug af grupper det nemmere at administrere tilladelser i stedet for at tildele dem til enkelte brugere.
- Er der nogen sikkerhedsovervejelser i forbindelse med eksterne gæstebrugere? Det kan være nødvendigt at arbejde sammen med din Azure Active Directory-administrator og din Power BI-administrator for at konfigurere [adgang for gæstebrugere](../admin/service-admin-azure-ad-b2b.md).

> [!TIP]
> Overvej at oprette et arbejdsområde for en bestemt forretningsaktivitet eller et bestemt projekt. Du kan blive fristet til at begynde at omstrukturere arbejdsområder baseret på din organisationsstruktur (f.eks. et arbejdsområde pr. afdeling), men denne tilgang ender ofte med at være for bred.

## <a name="determine-how-content-will-be-consumed"></a>Fastlæg, hvordan indhold forbruges

Det er nyttigt at forstå, hvordan forbrugere af en løsning foretrækker at få vist rapporter og dashboards. Spørgsmål, der skal stilles, omfatter:

- Vil en [Power BI-app](../consumer/end-user-apps.md) (som består af rapporter og dashboards fra et enkelt arbejdsområde) være den bedste måde at levere indhold til forbrugere på, eller vil direkte adgang til et arbejdsområde være tilstrækkeligt til seere af indhold?
- Vil visse rapporter og dashboards være integreret et andet sted, f.eks. i [Teams](../collaborate-share/service-embed-report-microsoft-teams.md), [SharePoint Online](../collaborate-share/service-embed-report-spo.md) eller på en [sikker portal eller et sikkert websted](../collaborate-share/service-embed-secure.md)?
- Vil forbrugerne få adgang til indhold på [mobilenheder](../consumer/mobile/mobile-apps-for-mobile-devices.md)? Krav om levering af rapporter på små formfaktorenheder vil påvirke nogle [beslutninger om rapportdesignet](../create-reports/desktop-create-phone-report.md).

## <a name="decide-if-other-content-may-be-created"></a>Beslut, om der skal oprettes andet indhold

Der er flere vigtige beslutninger, som skal træffes, for at give forbrugere tilladelse til at oprette nyt indhold, f.eks.:

- Har forbrugere tilladelse til at oprette nye rapporter fra det publicerede datasæt? Denne funktionalitet kan aktiveres ved at give en bruger [tilladelse til at oprette](../connect-data/service-datasets-build-permissions.md) datasæt.
- Hvis forbrugerne vil tilpasse en rapport, kan de så [gemme en kopi](../connect-data/service-datasets-copy-reports.md) af den og tilpasse den, så den imødekommer deres behov?

> [!CAUTION]
> Selvom funktionaliteten _Gem en kopi_ er en god funktion, skal den bruges varsomt, når rapporten indeholder bestemt grafik eller meddelelser i sidehovedet/sidefoden. Da logoer, ikoner og tekstmeddelelser ofte er relateret til krav til branding eller overholdelse af lovmæssige krav, er det vigtigt, at du omhyggeligt kontrollerer, hvordan de leveres og distribueres. Hvis _Gem en kopi_ bruges, men den oprindelige grafik eller meddelelserne i sidehovedet/sidefoden forbliver uændret af den nye forfatter, kan det resultere i forvirring om, hvem der rent faktisk producerede rapporten. Det kan også reducere meningsfuldheden af brandingen.

## <a name="evaluate-needs-for-premium-capacity"></a>Evaluer behovet for Premium-kapacitet

Der findes yderligere funktionalitet, når et arbejdsområde gemmes i en [Premium-kapacitet](../admin/service-premium-what-is.md). Her er flere årsager til, hvorfor arbejdsområder i en Premium-kapacitet kan være fordelagtige:

- Forbrugere, som ikke har en Power BI Pro-licens, får adgang til indhold.
- Understøttelse af store datasæt.
- Understøttelse af hyppigere opdateringer af data.
- Understøttelse af brug af det fulde sæt af funktioner til dataflow.
- Virksomhedsfunktioner, herunder udrulningspipelines og XMLA-slutpunktet.
- Understøttelse af sideinddelte rapporter (når arbejdsbelastningen er aktiveret).

## <a name="determine-data-acquisition-method"></a>Fastlæg metode til anskaffelse af data

De data, der kræves af en rapport, kan påvirke flere beslutninger. Spørgsmål, der skal stilles, omfatter:

- Kan et eksisterende [delt datasæt](../connect-data/service-datasets-share.md) i Power BI bruges, eller skal der oprettes et nyt Power BI-datasæt til denne løsning?
- Skal et eksisterende delt datasæt forstærkes med nye data eller målinger for at imødekomme yderligere behov?
- Hvilken [lagringstilstand for data](../transform-model/desktop-storage-mode.md) passer bedst? Mulighederne omfatter Import, DirectQuery, sammensat eller direkte forbindelse.
- Skal der bruges [sammenlægninger](../transform-model/desktop-aggregations.md) for at forbedre forespørgslens ydeevne?
- Vil det være nyttigt at oprette et [dataflow](../transform-model/dataflows/dataflows-introduction-self-service.md), og kan det fungere som en kilde til flere datasæt?
- Skal der registreres en ny [datakilde for gatewayen](../connect-data/service-gateway-data-sources.md)?

## <a name="decide-where-original-content-will-be-stored"></a>Beslut, hvor oprindeligt indhold skal gemmes

Ud over at planlægge destinationen for udrulningen er det også vigtigt at planlægge, hvor det oprindelige indhold – eller kilden – skal gemmes:

- Angiv en godkendt placering til lagring af de oprindelige Power BI Desktop-filer (.pbix). Ideelt set er denne placering kun tilgængelig for personer, der redigerer indholdet. Den skal passe sammen med den måde, som sikkerheden er konfigureret på i Power BI-tjenesten.
- Brug en placering til de oprindelige Power BI Desktop-filer, som omfatter historik for versionsstyring eller kildekontrol. Versionsstyring giver indholdsforfatteren mulighed for at omdanne en fil til en tidligere version, hvis det er nødvendigt. OneDrive for Business eller SharePoint fungerer godt til dette formål.
- Angiv en godkendt placering til lagring af ikke-centraliserede kildedata, f.eks. flade filer eller Excel-filer. Det skal være en sti, som alle forfattere af datasæt kan nå uden fejl, og som sikkerhedskopieres regelmæssigt.
- Angiv en godkendt placering for indhold, der eksporteres fra Power BI-tjenesten. Målet er at sørge for, at den sikkerhed, der er defineret i Power BI-tjenesten, ikke omgås ved et uheld.

> [!IMPORTANT]
> Det er især vigtigt at angive en beskyttet placering for oprindelige Power BI Desktop-filer, når de indeholder importerede data.

## <a name="assess-the-level-of-effort"></a>Vurder indsatsniveauet

Når der er tilstrækkelige oplysninger til rådighed fra kravene (som blev beskrevet i [fase 1](powerbi-migration-requirements.md)) og planlægningen af udrulningsprocessen for løsningen, er det nu muligt at vurdere indsatsniveauet. Derefter kan du formulere en projektplan med opgaver, tidslinje og ansvar.

> [!TIP]
> Arbejdsomkostninger, f.eks. lønninger, er normalt blandt de største udgifter i de fleste organisationer. Selvom det kan være vanskeligt at beregne nøjagtigt, er der et fremragende investeringsafkast på forbedringer af produktiviteten.

## <a name="next-steps"></a>Næste trin

I den [næste artikel i denne serie om migrering til Power BI](powerbi-migration-proof-of-concept.md) kan du få mere at vide om fase 3, som omhandler udførelse af POC (proof of concept) for at afhjælpe risici og håndtere ukendte hindringer så tidligt som muligt, når der migreres til Power BI.

Andre nyttige ressourcer omfatter:

- [Microsofts BI-transformation](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Whitepaper om planlægning af en udrulning af Power BI i en virksomhed](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

Der findes erfarne Power BI-partnere, som kan hjælpe din organisation med at gennemføre migreringsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).