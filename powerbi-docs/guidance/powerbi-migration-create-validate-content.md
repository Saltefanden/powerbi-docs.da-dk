---
title: Opret indhold for at migrere til Power BI
description: Vejledning til, hvordan du opretter og validerer indhold, når du migrerer til Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: f74b2ea56dd4399dd87c7d21b461b3e6bd23bbd9
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088068"
---
# <a name="create-content-to-migrate-to-power-bi"></a>Opret indhold for at migrere til Power BI

Denne artikel indeholder en beskrivelse af **fase 4**, som omhandler oprettelse og validering af indhold, når der migreres til Power BI.

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="Billede, der viser faserne i en migrering til Power BI. Der fokuseres på fase 4 i denne artikel.":::

> [!NOTE]
> Du kan finde en komplet forklaring af ovenstående grafik under [Oversigt over migrering til Power BI](powerbi-migration-overview.md).

I fase 4 er der fokus på udførelse af selve arbejdet med at konvertere proof of concept (POC) til en løsning, der er klar til produktion.

Outputtet fra denne fase er en Power BI-løsning, der er blevet valideret i et udviklingsarbejdsområde, og som er klar til udrulning til produktion.

> [!TIP]
> De fleste af de emner, denne artikel omhandler, gælder også for et Power BI-standardimplementeringsprojekt.

## <a name="create-the-production-solution"></a>Opret produktionsløsningen

På dette kritiske tidspunkt kan den samme person, som udførte POC, fortsætte med at producere Power BI-løsningen, der er klar til produktion. Eller en anden kan være involveret. Hvis tidslinjen ikke bringes i fare, er det godt at få de folk, der skal være ansvarlige for Power BI-udvikling i fremtiden, til at involvere sig. På den måde kan de aktivt lære det.

> [!IMPORTANT]
> Genbrug så meget af arbejdet fra denne POC som muligt.

### <a name="develop-new-import-dataset"></a>Opret et nyt Import-datasæt

Du kan vælge at oprette et nyt Import-datasæt, når der ikke allerede findes et eksisterende Power BI-datasæt, som opfylder dine behov, eller hvis det ikke kan forbedres, så det opfylder dine behov.

Ideelt set skal du helt fra starten overveje at separere udviklingsarbejdet for data og rapporter. [Separation af data og rapporter](report-separate-from-model.md) faciliterer adskillelsen af arbejdet og tilladelser, når forskellige personer er ansvarlige for dataudformning og rapporter. Det giver en mere skalerbar tilgang og opfordrer til genbrug af data.

De vigtigste aktiviteter vedrørende udvikling af et Import-datasæt omfatter:

- [Hent data](../connect-data/desktop-quickstart-connect-to-data.md) fra én eller flere datakilder (hvilket kan være et Power BI-dataflow).
- [Tilpas, kombiner og forbered](../connect-data/desktop-shape-and-combine-data.md) data.
- Opret [modellen for datasættet](../transform-model/desktop-modeling-view.md), herunder [datotabeller](../transform-model/desktop-date-tables.md).
- Opret og bekræft [modelrelationer](../transform-model/desktop-create-and-manage-relationships.md).
- Definer [målinger](../transform-model/desktop-measures.md).
- Konfigurer [sikkerhed på rækkeniveau](../admin/service-admin-rls.md), om nødvendigt.
- Konfigurer synonymer, og [optimer Spørgsmål og svar](../natural-language/q-and-a-best-practices.md).
- Planlæg i forhold til skalerbarhed, ydeevne og samtidighed, hvilket kan påvirke dine beslutninger om tilstande for datalagring, f.eks. brug af en [sammensat model](../transform-model/desktop-composite-models.md) eller [sammenlægninger](../transform-model/desktop-aggregations.md).

> [!TIP]
> Hvis du har forskellige udviklings-/produktionsmiljøer, kan du overveje at [parametisere](/power-query/power-query-query-parameters) datakilder. Det gør udrulningen markant lettere, som beskrevet i [fase 5](powerbi-migration-deploy-support-monitor.md).

### <a name="develop-new-reports-and-dashboards"></a>Udrul nye rapporter og dashboards

De vigtigste aktiviteter, der er relateret til udvikling af en Power BI- rapport eller et Power BI-dashboard, omfatter:

- Beslut, om du vil bruge en direkte forbindelse til en eksisterende datamodel eller oprette en ny datamodel
- Når du opretter en ny datamodel, skal du bestemme [tilstanden af datalagring](../transform-model/desktop-storage-mode.md) for modeltabeller (Import, DirectQuery eller Sammensat).
- Bestem det bedste værktøj til datavisualisering for at opfylde kravene: Power BI Desktop, Paginated Report Builder eller Excel.
- Fastlæg de [bedste visualiseringer](../consumer/end-user-visual-type.md) til at fortælle den historie, som rapporten skal fortælle, og til at håndtere de spørgsmål, som rapporten skal besvare.
- Sørg for, at alle visualiseringer præsenterer tydelig, kortfattet terminologi, der passer til virksomheden.
- Håndter krav til interaktivitet.
- Når du bruger en direkte forbindelse, kan du tilføje [målinger på rapportniveau](../transform-model/desktop-tutorial-create-measures.md).
- Opret et [dashboard](../create-reports/service-dashboards.md) i Power BI-tjenesten, især når forbrugerne gerne vil have en nem måde at overvåge vigtige metrikværdier på.

> [!NOTE]
> Mange af disse beslutninger vil være truffet i tidligere faser af planlægningen eller i den tekniske POC.

## <a name="validate-the-solution"></a>Valider løsningen

Der er fire primære aspekter i valideringen af en Power BI-løsning:

1. Datanøjagtighed
2. Sikkerhed
3. Funktionalitet
4. Ydeevne

### <a name="validate-data-accuracy"></a>Valider datanøjagtighed

Som en engangsindsats i forbindelse med migreringen skal du sikre, at dataene i den nye rapport stemmer overens med det, der vises i den tidligere rapport. Eller at du kan forklare hvorfor, hvis der er en forskel. Det er mere almindeligt, end man tror, at finde en fejl i den tidligere løsning, som bliver løst i den nye løsning.

Som en del af den igangværende indsats for datavalidering skal den nye rapport typisk krydstjekkes i forhold til det oprindelige kildesystem. Ideelt set forekommer denne validering gentagne gange, hver gang du publicerer en rapportændring.

### <a name="validate-security"></a>Valider sikkerhed

Når du validerer sikkerhed, er der to primære aspekter, du skal overveje:

- Datatilladelser
- Adgang til datasæt, rapporter og dashboards

I et Import-datasæt anvendes datasæt ved at definere [sikkerhed på rækkeniveau](../admin/service-admin-rls.md). Det er også muligt, at datatilladelser håndhæves af kildesystemet, når lagringstilstanden DirectQuery bruges (muligvis med [enkeltlogon](../connect-data/service-gateway-sso-overview.md)).

De primære måder at tildele adgang til Power BI-indhold er:

- [Arbejdsområderoller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) (til editorer og seere af indhold).
- [Apptilladelser](../collaborate-share/service-create-distribute-apps.md#publish-your-app), der anvendes på et pakket sæt af indholdet i arbejdsområdet (til seere).
- [Deling](../collaborate-share/service-share-dashboards.md) af en separat rapport eller et separat dashboard (til seere).

> [!TIP]
> Vi anbefaler, at indholdsforfattere oplæres i, hvordan sikkerhed administreres på en effektiv måde. Det er også vigtigt at have robust test, overvågning og revision på plads.

### <a name="validate-functionality"></a>Valider funktionalitet

Det er tid til at dobbelttjekke oplysninger om datasæt, f.eks. feltnavne, formatering, sortering og standardfunktionsmåden for opsummering. Interaktive rapportfunktioner, f.eks. [udsnit](../visuals/power-bi-visualization-slicers.md), [zoom ind på detaljeniveauet](../consumer/end-user-drill.md), [detaljeadgang](../create-reports/desktop-drillthrough.md), [udtryk](../create-reports/desktop-conditional-format-visual-titles.md), [knapper](../create-reports/desktop-buttons.md) eller [bogmærker](../create-reports/desktop-bookmarks.md), skal også bekræftes.

I løbet af udviklingsprocessen skal Power BI-løsningen regelmæssigt publiceres til et udviklingsarbejdsområde i Power BI-tjenesten. Bekræft, at al funktionalitet fungerer som forventet i tjenesten, f.eks. gengivelse af brugerdefinerede visualiseringer. Det er også et godt tidspunkt at foretage yderligere test på. Test [planlagt opdatering](../connect-data/refresh-scheduled-refresh.md), [Spørgsmål og svar](../consumer/end-user-q-and-a.md), og hvordan rapporter og dashboards ser ud på en [mobilenhed](../consumer/mobile/mobile-apps-for-mobile-devices.md).

### <a name="validate-performance"></a>Valider ydeevne

Ydeevnen af Power BI-løsningen er vigtig for forbrugernes oplevelse. De fleste rapporter bør præsentere visualiseringer på under 10 sekunder. Hvis du har rapporter, der tager længere tid at indlæse, skal du sætte handlingen på pause og overveje, hvad der kan bidrage til forsinkelser. Rapportens ydeevne bør vurderes regelmæssigt i Power BI-tjenesten ud over Power BI Desktop.

Der opstår mange problemer med ydeevnen pga. [DAX (Data Analysis Expressions)](../transform-model/desktop-quickstart-learn-dax-basics.md), der er under standard, et dårligt design af datasættet eller et rapportdesign, der er under det optimale (f.eks. forsøg på at gengive for mange visualiseringer på en enkelt side). Problemer med tekniske miljøer, f.eks. netværket, en overbelastet datagateway, eller hvordan en Premium-kapacitet er konfigureret, kan også bidrage til problemer med ydeevnen. Du kan finde flere oplysninger i [Optimeringsvejledning til Power BI](power-bi-optimization.md) og [Fejlfinding af rapportens ydeevne i Power BI](report-performance-troubleshoot.md).

## <a name="document-the-solution"></a>Dokumentér løsningen

Der findes to primære typer dokumentation, der er nyttige til en Power BI-løsning:

- Dokumentation til datasæt
- Dokumentation til rapporter

Dokumentation kan gemmes der, hvor målgruppen nemmest kan få adgang til den. Almindelige muligheder omfatter:

- **På et SharePoint-websted:** Der findes måske et SharePoint-websted til dit Center of Excellence eller et internt Power BI-communitywebsted.
- **I en app:** URL-adresser kan konfigureres, når du publicerer en Power BI-app for at dirigere forbrugeren til flere oplysninger.
- **I separate Power BI Desktop-filer:** Modelelementer, f.eks. tabeller og kolonner, kan definere en beskrivelse. Disse beskrivelser vises som værktøjstip i ruden **Felter**, når rapporterne forfattes.

> [!TIP]
> Hvis du opretter et websted, der fungerer som en hub til Power BI-relateret dokumentation, skal du overveje at [tilpasse menuen Få hjælp](../admin/service-admin-portal.md#publish-get-help-information) med URL-adressen til dets placering.

### <a name="create-dataset-documentation"></a>Opret dokumentation til datasæt

Dokumentation til datasæt henvender sig til brugere, som skal administrere datasættet fremover. Det er nyttigt at inkludere:

- Trufne designbeslutninger og baggrunden til dem.
- Hvem der ejer, vedligeholder og certificerer datasæt.
- Krav til opdatering af data.
- Brugerdefinerede forretningsregler, der er defineret i datasæt.
- Specifikke krav til beskyttelse af datasæt eller beskyttelse af personlige oplysninger.
- Fremtidige vedligeholdelsesbehov.
- Kendte åbne problemer eller udskudte elementer i ordrebeholdningen.

Du kan også vælge at oprette en ændringslog, hvor de vigtigste ændringer, der er udført over tid, opsummeres.

### <a name="create-report-documentation"></a>Opret dokumentation til rapporter

Dokumentation til rapporter, der typisk er struktureret som en gennemgang, og som er målrettet til rapportforbrugere, kan hjælpe forbrugerne med at få mere værdi ud af dine rapporter og dashboards. Et kort selvstudium i en video fungerer ofte godt.

Du kan også vælge at inkludere yderligere dokumentation til rapporten på en skjult side i rapporten. Det kan omfatte designbeslutninger og en ændringslog.

## <a name="next-steps"></a>Næste trin

I den [næste artikel i denne serie om migrering til Power BI](powerbi-migration-deploy-support-monitor.md) kan du få mere at vide om fase 5, der omhandler udrulning, understøttelse og overvågning af indhold, når der migreres til Power BI.

Andre nyttige ressourcer omfatter:

- [Microsofts BI-transformation](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Whitepaper om planlægning af en udrulning af Power BI i en virksomhed](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

Der findes erfarne Power BI-partnere, som kan hjælpe din organisation med at gennemføre migreringsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).
