---
title: Hvad er sideinddelte rapporter i Power BI Premium?
description: Sideinddelte rapporter er nu tilgængelige i Power BI-tjenesten. De har længe været standardformatet for rapporter i SQL Server Reporting Services. Disse rapporter kan udskrives eller deles. Du kan styre rapportlayoutet præcist. De viser alle data i en tabel, også selvom tabellen strækker sig over flere sider.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: jXTiYJKw1Rs
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 05/19/2020
ms.openlocfilehash: 16fcc18492b371accaaf3c447d7a88978051f8c3
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859652"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>Hvad er sideinddelte rapporter i Power BI Premium?

*Sideinddelte rapporter* er udviklet til at skulle udskrives eller deles. De kaldes *sideinddelte*, fordi de er formateret til at passe godt på en side. De viser alle data i en tabel, selvom tabellen strækker sig over flere sider. De kaldes også *perfekt pixel*, fordi du kan styre deres rapportsidelayout helt præcist. Power BI Report Builder er det separate værktøj, der bruges til oprettelse af sideinddelte rapporter. Sideinddelte rapporter er baseret på RDL-rapportteknologien, som er det lange standardrapportformat i SQL Server Reporting Services. 

Sideinddelte rapporter indeholder ofte mange sider. Denne rapport indeholder f.eks. 563 sider. Hver side viser præcis én side pr. faktura og har gentagne sidehoveder og sidefødder.

![Sideinddelt](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Du kan få vist et eksempel på rapporten i Report Builder og derefter publicere den i Power BI-tjenesten, app.powerbi.com. Du skal bruge en Power BI Pro-licens for at publicere en rapport i tjenesten. Du kan publicere og dele sideinddelte rapporter i Mit arbejdsområde eller i arbejdsområder, så længe arbejdsområdet er placeret i en Power BI Premium-kapacitet. En Power BI-administrator skal også aktivere sideinddelte rapporter under [afsnittet for Premium-kapaciteter](../admin/service-admin-premium-workloads.md#paginated-reports) på Power BI-administrationsportalen. 

## <a name="compare-power-bi-reports-and-paginated-reports"></a>Sammenlign Power BI-rapporter og sideinddelte rapporter

En stor fordel ved sideinddelte rapporter er muligheden for at udskrive alle dataene i en tabel, uanset hvor lang den er. Forestil dig, at du placerer en tabel i en Power BI-rapport. Du kan se nogle af dens rækker i tabellen på siden, og du har et rullepanel, hvor du kan se resten. Hvis du udskriver den pågældende side eller eksporterer den til PDF, udskrives kun de rækker, som du fik vist på siden. 

Antag nu, at du placerer den samme tabel i en sideinddelt rapport. Når du udskriver eller eksporterer den til PDF, har den sideinddelte rapport lige så mange sider, som det er nødvendigt for at udskrive alle rækker i tabellen. 

I den følgende video viser Microsoft Most Valued Professional – Data Platform Peter Myers og Principal Program Manager Chris Finlan, hvordan man udskriver en lignende tabel i de to rapportformater. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/jXTiYJKw1Rs?list=PL1N57mwBHtN1icIhpjQOaRL8r9G-wytpT" frameborder="0" allowfullscreen></iframe>

Denne video er en del af et videobaseret kursus, der består af otte moduler [Sideinddelte rapporter i Power BI på én dag](../learning-catalog/paginated-reports-online-course.md). Kurset har til formål at sætte dig i stand til at skrive rapporter med den tekniske viden, der kræves for at oprette, udgive og distribuere sideinddelte Power BI-rapporter.

## <a name="create-reports-in-power-bi-report-builder"></a>Opret rapporter i Power BI Report Builder

Sideinddelte rapporter har deres eget designværktøj, Power BI Report Builder. Det er et nyt værktøj, der deler samme fundament som de værktøjer, du tidligere har brugt til at oprette sideinddelte rapporter for Power BI-rapportserver eller SQL Server Reporting Services (SSRS). Sideinddelte rapporter, som du opretter til SSRS-2016 og -2017 eller til Power BI-rapportserveren i det lokale miljø, er faktisk kompatible med Power BI-tjenesten. Power BI-tjenesten opretholder bagudkompatibilitet, så du kan fortsat bruge tidligere oprettede rapporter, og du kan opgradere sideinddelte rapporter, der er oprettet i en tidligere version. Det er ikke alle rapportfunktioner, der er tilgængelige ved lanceringen. Se under [Begrænsninger og overvejelser](#limitations-and-considerations) i denne artikel for at få flere oplysninger.
     
## <a name="report-from-a-variety-of-data-sources"></a>Rapport fra forskellige datakilder

En enkelt sideinddelt rapport kan have en række forskellige datakilder. Til forskel fra Power BI-rapporter har den ikke en underliggende datamodel. I forbindelse med den første version af sideinddelte rapporter i Power BI-tjenesten kan du oprette integrerede datakilder og datasæt i selve rapporten. I øjeblikket kan du ikke bruge delte datakilder eller delte datasæt. Du opretter rapporter i Report Builder på din lokale computer. Hvis en rapport er forbundet med data i det lokale miljø, skal du efter upload af rapporten til Power BI-tjenesten oprette en gateway og omdirigere dataforbindelsen. Her er de datakilder, du kan oprette forbindelse til på nuværende tidspunkt:

- Azure SQL Database og Data Warehouse (via Basic og oAuth)
- Azure Analysis Services (via enkeltlogon)
- SQL Server via en gateway
- SQL Server Analysis Services via en gateway
- Power BI-datasæt
- Oracle
- Teradata

## <a name="design-your-report"></a>Design rapporten  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Opret sideinddelte rapporter med matrix-, diagram- og frihåndslayout

Tabelrapporter fungerer godt i forbindelse med kolonnebaserede data. Matrixrapporter, som f.eks. krydsklassifikation eller pivottabeller, er velegnet til opsummerede data. Diagramrapporter viser data i et grafisk format, og *listerapporter* i frihåndsformat kan præsentere næsten alt andet, f.eks. fakturaer. 
  
Du kan starte med en af guiderne i Report Builder. Guiderne Tabel, Matrix og Diagram fører dig gennem oprettelsen af den integrerede datakildeforbindelse og det integrerede datasæt. Derefter skal du trække og slippe felter for at oprette en forespørgsel til datasættet, vælge et layout og en typografi samt tilpasse din rapport.  
  
Ved hjælp af guiden Kort kan oprette du rapporter, der viser aggregerede data på en geografisk eller geometriske baggrund. Kortdata kan være afstandsdata fra en Transact-SQL-forespørgsel eller en ESRI-formfil (Environmental Systems Research Institute, Inc.). Du kan også tilføje en feltbaggrund fra Microsoft Bing Kort.  

### <a name="add-more-to-your-report"></a>Føj andet til rapporten

Rediger dine data ved at filtrere, gruppere og sortere data eller ved at tilføje formler eller udtryk. Tilføj diagrammer, målere, minidiagrammer og indikatorer for at opsummere data i et visuelt format.  Brug parametre og filtre til at filtrere data til brugerdefinerede visninger. Integrer eller henvis til billeder og andre ressourcer, herunder eksternt indhold.  

Alt i en sideinddelt rapport – fra selve rapporten til alle tekstfelter, billeder, tabeller og diagrammer – har en række egenskaber, du kan angive, for at få rapporten til at se ud præcis, som du ønsker.

## <a name="creating-a-report-definition"></a>Oprettelse af en rapportdefinition

Når du designer en sideinddelt rapport, opretter du faktisk en *rapportdefinition*. Den indeholder ikke dataene. Den angiver, hvor dataene skal hentes, hvilke data der skal hentes, og hvordan dataene skal vises. Når du kører rapporten, bruger rapportbehandleren den angivne rapportdefinition, henter dataene og kombinerer det med rapportlayoutet for at generere rapporten. Du kan uploade rapportdefinitionen til Power BI-tjenesten, `https://app.powerbi.com`, enten til Mit arbejdsområde eller til et arbejdsområde, der er delt med dine kolleger. Hvis rapportdatakilden er placeret er i det lokale miljø, skal du omdirigere datakildeforbindelsen, så den går gennem en gateway, når du har uploadet rapporten. 

## <a name="view-your-paginated-report"></a>Få vist din sideinddelte rapport
Du får vist din sideinddelte rapport i Power BI-tjenesten i en browser og i Power BI-mobilapps. I Power BI-tjenesten kan du eksportere rapporten til en række formater, f.eks. HTML, MHTML, PDF, XML, CSV, TIFF-, Word og Excel. Du kan også dele den med andre.  

## <a name="create-a-subscription-to-your-report"></a>Opret et abonnement på din rapport

Du kan nu oprette mailabonnementer på sideinddelte rapporter i Power BI-tjenesten for dig selv og andre. Generelt er processen den samme som at abonnere på rapporter og dashboards i Power BI-tjenesten. Under konfigurationen af abonnementer vælger du, hvor ofte du gerne vil modtage mails: dagligt, ugentligt eller hver time. Abonnementet indeholder en vedhæftet PDF-fil med hele outputtet for rapporten.

Du kan finde flere oplysninger i artiklen [Meld dig selv og andre til et abonnement på sideinddelte rapporter i Power BI-tjenesten](../consumer/paginated-reports-subscriptions.md). 

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Her er nogle andre funktioner, der ikke understøttes i den første version:

- Fastgørelse af rapportsider eller visualiseringer til Power BI-dashboards. Du kan stadig fastgøre visualiseringer til et Power BI-dashboard fra en sideinddelt rapport i det lokale miljø på en Power BI-rapportserver eller en Reporting Services-rapportserver. Du kan finde flere oplysninger under [Fastgør Reporting Services-elementer til Power BI-dashboards](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards).
- Dokumentoversigt.
- Rapporter for detaljeadgang.  Overvej at bruge parametre for URL-adresser med sideinddelte rapporter i forbindelse med scenarier med detaljeadgang.
- Delte datakilder og datasæt.

 
## <a name="next-steps"></a>Næste trin

- [Installér Power BI Report Builder fra Microsoft Download Center](https://aka.ms/pbireportbuilder)
- [Selvstudium: Opret en sideinddelt rapport](paginated-reports-quickstart-aw.md)
- [Onlinekursus: Sideinddelte Power BI-rapporter på én dag](../learning-catalog/paginated-reports-online-course.md)
- [Angiv data direkte i en sideinddelt rapport](paginated-reports-enter-data.md)
- [Selvstudium: Integrer sideinddelte Power BI-rapporter i et program til dine kunder](../developer/embedded/embed-paginated-reports-customers.md)