---
title: Få adgang til Power BI-tabeller i Excel (prøveversion)
description: I Excel kan du finde data fra udvalgte tabeller i Power BI-datasæt i datatypegalleriet.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 08/04/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 95ccc80a37ad9703c60c82ce928d35b5e301947b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96407302"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Få adgang til Power BI-tabeller i Excel (prøveversion)

*Udvalgte tabeller* er en måde at sammenkæde dine data i Excel med data i Power BI på. De gør det nemmere at føje virksomhedsdata til dine Excel-ark. I datatypegalleriet i Excel finder du data fra udvalgte tabeller i Power BI-datasæt. Dette er forklaret i denne artikel.

Opretter du datasæt i Power BI? Læs, [hvordan du angiver udvalgte tabeller i Power BI Desktop](service-create-excel-featured-tables.md).

> [!NOTE]
> I Excel kan du også analysere data fra ethvert Power BI-datasæt, som du har adgang til i Power BI. Se [Andre måder at få adgang til Power BI-datasættet fra Excel på](service-analyze-in-excel.md#other-ways-to-access-power-bi-datasets-from-excel) i artiklen "Analysér i Excel til Power BI" for at få flere oplysninger.
> 

## <a name="the-excel-data-types-gallery"></a>Excel-datatypegalleriet
Udvalgte Power BI-datasæt vises som *datatyper* på båndet **Data** i Excel-galleriet **Datatyper**.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Skærmbillede af Datatypegalleri på båndet Excel-data.":::

Når det er udvidet, viser galleriet de generiske datatyper, f.eks. **Beholdninger** og **Geografi** samt de øverste 10 **organisationsdatatyper**, der er tilgængelige for dig – udvalgte tabeller fra Power BI-datasæt.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Skærmbillede af Excel-datatypegalleri.":::

## <a name="search-for-power-bi-data-in-the-data-types-gallery"></a>Søg efter Power BI-data in Datatypegalleriet

Hvis du vil søge efter data i en udvalgt Power BI-tabel, skal du vælge en celle eller et område i Excel-arket, der indeholder en værdi, som svarer til værdien i en udvalgt tabel. Vælg pilen **Mere** ud for datatypegalleriet.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-more.png" alt-text="Skærmbillede af ikonet Mere i Excel-datatypegalleri.":::

Hvis du kan se den tabel, du søger efter, kan du vælge den. Ellers skal du vælge **Mere fra din organisation**. Excel søger efter et match i alle de udvalgte tabeller, som du har adgang til.

:::image type="content" source="media/service-excel-featured-tables/excel-more-your-organization.png" alt-text="Skærmbillede af valg fra din organisation (eksempel).":::
 
Excel viser alle de mulige tabeller. I ruden **Datavælger** skal du markere afkrydsningsfeltet **Filter** for at indsnævre mulighederne. Vælg den tilsvarende tabel.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-store.png" alt-text="Skærmbillede af Excel-organisationsdata, datatypetabellen Leverandører.":::
 
Hvis Excel finder rækker, der med høj sikkerhed matcher, kædes cellerne straks sammen med disse rækker. Ikonet for det sammenkædede element angiver, at cellerne er sammenkædet med rækkerne i Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="Skærmbillede af ikonet Tilknyttet vare.":::

Hvis en celle har mere end én potentiel tilsvarende række, viser cellen et ikon med et spørgsmålstegn, og ruden **Datavælger** åbnes. I det følgende eksempel valgte vi et område fra B3: B9 og valgte derefter den udvalgte Power BI-tabel **Lager**. Alle rækkerne havde forekomster undtagen celle B9, "508 – Pasadena Lindseys". **Datavælgeren** viser to mulige forekomster, den samme værdi i to forskellige tabeller.

:::image type="content" source="media/service-excel-featured-tables/excel-question-mark-featured-table.png" alt-text="Skærmbillede af ruden Excel-datavælger.":::
 
Indstillingen Organisationsdata kan returnere rækker fra flere forskellige tabeller. Excel grupperer de potentielt matchende rækker efter den datatype, de kom fra. Excel sorter datatyperne baseret på deres mest tilsvarende række. Brug vinkelpilene til at skjule og udvide datatyperne, så de matcher rækkerne.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Skærmbillede af ruden Excel-datavælger med flere indstillinger.":::
 
For hvert forslag skal du vælge rækkenavnet i ruden **Datavælger** for at få vist flere detaljer i rækken for at hjælpe dig med at vælge den rigtige række. Når du har fundet den, skal du trykke på **Vælg** for at knytte rækken til cellen i Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="Skærmbillede af detaljer om Datavælger.":::

## <a name="explore-related-data"></a>Udforsk relaterede data

Nu, hvor du har oprettet forbindelse mellem værdierne i dit Excel-ark og dataene i den udvalgte Power BI-tabel, kan du udforske disse data. Brug dataene til at forbedre din Excel-rapportering.

### <a name="view-related-data-in-a-card"></a>Få vist relaterede data på et kort 
 
Når du vælger ikonet **Kort**, vises der et kort med data fra eventuelle felter og beregnede felter i den udvalgte tabel. Kortets titel viser værdien af feltet rækkeetiket i den valgte tabel.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Skærmbillede af detaljer om Tilknyttet vare.":::

### <a name="insert-related-data-from-power-bi"></a>Indsæt relaterede data fra Power BI 

Vælg ikonet **Indsæt data**, og vælg derefter et feltnavn på listen over felter for at føje værdien til gitteret.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Skærmbillede af Vælg et feltnavn.":::

Feltværdien eller -værdierne placeres i de tilstødende celler. Celleformlen refererer til den sammenkædede celle og feltnavnet, så du kan bruge dataene i Excel-funktioner.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Skærmbillede af Excel-celleformel.":::

### <a name="use-cell-formulas"></a>Brug celleformler

I en Excel-tabel kan du referere til kolonnen med sammenkædede tabeller og derefter tilføje datafelter ved hjælp af referencen `.` (periode).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Skærmbillede af Excel-periodereference.":::

I en celle kan du også referere til cellen og bruge referencen `.` (periode) til at hente felter.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Skærmbillede af celleperiodereference.":::

### <a name="show-a-card-change-or-convert-to-text"></a>Vis et kort, skift eller konverter til tekst

Sammenkædede celler har tilføjede indstillinger til genvejsmenuen. Højreklik på en celle. Sammen med de sædvanlige indstillinger kan du også se følgende:

- **Vis datatypekort**.
- **Datatype** > **Konverter til tekst**.
- **Datatype** > **Skift**.
- **Opdater**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Skærmbillede af højreklik, Konvertér til tekst.":::
 
**Konvertér til tekst** fjerner linket til rækken i Power BI-tabellen. Det er vigtigt, at teksten i cellen er værdien for rækkeetiketten i den sammenkædede celle. Hvis du har knyttet en celle til en række, du ikke har tænkt dig at vælge, kan du vælge **Fortryd** i Excel for at gendanne de oprindelige celleværdier.
 
## <a name="data-caching-and-refresh"></a>Data-cachelagring og -opdatering

Når Excel knytter en celle til en række i en Power BI-tabel, hentes og gemmes alle feltværdierne i Excel-filen. Alle, som du deler filen med, kan referere til et af felterne uden at anmode om data fra Power BI.  

Brug knappen **Opdater alle** på båndet **Data** for at opdatere data i sammenkædede celler. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Skærmbillede af Opdater alt.":::
 
Du kan også opdatere enkelte celler. Højreklik på cellen, og vælg **Datatyper** > **Opdater**.

## <a name="licensing"></a>Licensering

Excel-datatypegalleriet og de forbundne oplevelser til Power BI-tabeller er kun tilgængelige for Excel E5- og G5-kunder. 

## <a name="security"></a>Sikkerhed

Du kan kun se udvalgte tabeller fra datasæt, som du har tilladelse til, i Power BI. Når du opdaterer data, skal du have adgangstilladelse til datasættet i Power BI for at hente rækkerne. Du skal have tilladelsen [Build eller Skriv til datasættet](../connect-data/service-datasets-build-permissions.md) i Power BI.
 
Excel cachelagrer de data, der returneres for hele rækken. Alle, du deler Excel-filen med, kan se dataene for alle felterne i alle de sammenkædede celler.

Hvis et Power BI-datasæt har sikkerhed på rækkeniveau, eller hvis der er anvendt et navn på en Microsoft Information Protection-følsomhedsetiket, medtages de fremhævede tabeller fra det pågældende datasæt ikke i Excel-datatypegalleriet. Dette er en begrænsning af den oprindelige prøveversion.

## <a name="administrative-control"></a>Administrativ kontrol

Power BI-administratorer kan styre, hvem i organisationen der kan bruge udvalgte tabeller i Excel-datatypegalleriet. Se flere oplysninger under [Tillad forbindelser til udvalgte tabeller](../admin/service-admin-portal.md#allow-connections-to-featured-tables) i artiklen på Admin Portal. 
 
### <a name="auditing"></a>Overvågning

Overvågningslogge til administration viser disse hændelser for udvalgte tabeller:

- **AnalyzedByExternalApplication**: Giver administratorer overblik over, hvilke brugere der anvender hvilke udvalgte tabeller.
- **UpdateFeaturedTables**: Giver administratorer overblik over, hvilke brugere der udgiver og opdaterer udvalgte tabeller.

Du kan finde en komplet liste over hændelser i overvågningsloggen under [Sporing af brugeraktiviteter i Power BI](../admin/service-admin-auditing.md).

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Her er begrænsningerne for den oprindelige prøveversion:

- Integrationen er tilgængelig i Excel Insiders Builds.
- Excel-datatypegalleriet indeholder udvalgte tabeller til brugere med den relevante licens i Power BI Desktop og Power BI-tjenesten. Understøttelse af Power BI-tjenesten er muligvis ikke tilgængelig ved lanceringen af prøveversionen, men vil blive tilføjet.
- Udvalgte tabeller i Power BI-datasæt, der bruger følgende funktioner, vises ikke i Excel: 

    - Sikkerhedsdatasæt på rækkeniveau.
    - Microsoft Information Protection-aktiverede datasæt.
    - DirectQuery-datasæt.
    - Datasæt med en direkte forbindelse.

- Der vises kun data i kolonner og beregnede kolonner i den udvalgte tabel i Excel. Følgende er ikke angivet i den oprindelige prøveversion:

    - De målinger, der er defineret i funktionstabellen.
    - De målinger, der defineres for relaterede tabeller, og implicitte målinger beregnet ud fra relationer.

- Excel viser kun udvalgte tabeller (*datatyper*), der er gemt i de nye Power BI-arbejdsområder. Udvalgte tabeller, der er gemt i de klassiske arbejdsområder eller Mit arbejdsområde, vises ikke som datatyper i Excel. Du kan [opgradere klassiske arbejdsområder til de nye arbejdsområder](service-upgrade-workspaces.md) i Power BI.

Datatyperne i Excel svarer til en opslagsfunktion. Det kræver en celleværdi, der er angivet i Excel-arket, og der søges efter tilsvarende rækker i udvalgte Power BI-tabeller. Søgeoplevelsen har følgende funktionsmåder:

- Når du bruger knappen **Organisationsdata** til at søge, søger Excel kun i udvalgte tabeller i Power BI-datasæt.
- Rækkematchning er baseret på tekstkolonner i den udvalgte tabel. Den bruger den samme indeksering som Power BI Q&A-funktionen, som er optimeret til engelsksprogede søgninger. Søgning på andre sprog resulterer muligvis ikke i præcise matches. Der søges ikke efter matches i numeriske kolonner.
- Matchning er baseret på præcise og præfiksbaserede matches til individuelle søgeord. En celles værdi opdeles på baggrund af mellemrum eller andre mellemrumstegn, f.eks. faner. Derefter betragtes hvert ord som et søgeord. Værdier i en rækkes tekstfelt sammenlignes med hvert søgeord for at finde nøjagtige og præfiksbaserede forekomster. Der returneres en præfiksforekomst, hvis rækkens tekstfelt starter med søgeordet. Hvis en celle f.eks. indeholder "Orange County", så er "Orange" og "County" separate søgetermer. 

    - Rækker med tekstkolonner, hvis værdier svarer nøjagtigt til "Orange" eller "County", returneres. 
    - Rækker med tekstkolonner, hvis værdier starter med "Orange" eller "County", returneres. 
    - Det er vigtigt, at de rækker, der indeholder "Orange" eller "County", men ikke starter med dem, ikke returneres.

- Power BI returnerer maksimalt 100 rækkeforslag for hver celle.
- Indstilling eller opdatering af den udvalgte tabel understøttes ikke i XMLA-slutpunktet
- Excel-filer med en datamodel kan bruges til at publicere udvalgte tabeller. Indlæs dataene i Power BI Desktop, og udgiv derefter den udvalgte tabel.
- Ved ændring af tabelnavn, rækkeetiket eller nøglekolonne kan den udvalgte tabel påvirke Excel-brugere med sammenkædede celler til rækker i tabellen. 
- Excel viser, hvornår dataene blev hentet fra Power BI-datasættet. Dette tidspunkt er ikke nødvendigvis det tidspunkt, hvor dataene blev opdateret i Power BI, eller tidspunktet for det seneste datapunkt i et datasæt. Antag f.eks., at et datasæt i Power BI blev opdateret for en uge siden, men de underliggende kildedata var en uge gammel, da opdateringen fandt sted. De faktiske data ville være to uger gamle, men Excel viser data, der hentes, som den dato og det klokkeslæt, hvor dataene blev indlæst i Excel.

## <a name="next-steps"></a>Næste trin

- [Angiv udvalgte tabeller i Power BI Desktop](service-create-excel-featured-tables.md)
- Læs, [hvordan du bruger Excel-datatyper fra Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) i Excel-dokumentationen.
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

