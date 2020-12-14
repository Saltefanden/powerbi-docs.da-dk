---
title: Angiv udvalgte tabeller i Power BI Desktop
description: Opret udvalgte tabeller i Power BI Desktop, så de vises i Excel-datatypegalleriet for organisationen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906882"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>Angiv udvalgte tabeller i Power BI Desktop, som skal vises i Excel-datatypegalleriet for organisationen

I datatypegalleriet i Excel kan dine brugere finde data fra *fremhævede tabeller* i dine Power BI-datasæt. I denne artikel får du mere at vide om, hvordan du angiver tabeller som *fremhævede* i dine datasæt. Disse tags gør det nemmere for dine brugere at føje virksomhedsdata til deres Excel-ark. Her er de grundlæggende trin, du skal udføre for at indstille og dele fremhævede tabeller.

1. Du identificerer fremhævede tabeller i dine datasæt i Power BI Desktop (denne artikel)
1. Du gemmer disse datasæt med fremhævede tabeller på et af de nye arbejdsområder. Rapportoprettere kan oprette rapporter med disse fremhævede tabeller. 
1. Resten af organisationen kan oprette forbindelse til disse fremhævede tabeller, der kaldes *datatyper* i Excel, for relevante data, der kan opdateres. Artiklen [Få adgang til udvalgte Power BI-tabeller i Excel](service-excel-featured-tables.md) indeholder en beskrivelse af, hvordan disse udvalgte tabeller bruges i Excel.

> [!NOTE]
> Du kan [fremhæve eller certificere datasæt i Power BI](../collaborate-share/service-endorse-content.md). Det kaldes *godkendelse*. Excel prioriterer tabeller i godkendte datasæt i Datatypegalleriet. Excel viser først udvalgte tabeller i certificerede datasæt og derefter tabeller i promoverede datasæt. Derefter viser Excel udvalgte tabeller i ikke-godkendte datasæt. 

> [!NOTE]
> Fra og med december 2020-versionen af Power BI Desktop er oprettelse af udvalgte tabeller tilgængelig som standard. Hvis du bruger en tidligere version, kan du opgradere Power BI Desktop eller aktivere funktionaliteten **Udvalgte tabeller** via **Filer** > **Indstillinger** > **Indstillinger** > **Prøveversionsfunktioner**.

## <a name="select-a-table"></a>Vælg en tabel

1. Gå til Modelvisning i Power BI Desktop.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Modelvisning":::
 
2. Vælg en tabel, og sæt **Er en fremhævet tabel** til **Ja**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Sæt Er en fremhævet tabel til Ja":::

4. I **Konfigurer denne tabel** skal du udfylde de påkrævede felter:

    - En **beskrivelse**. 
        > [!TIP]
        > Start beskrivelsen med "Fremhævet tabel" for at hjælpe forfattere af Power BI-rapporter med et identificere den.
    - Feltværdien **Rækkeetiket** bruges i Excel, så brugerne nemt kan identificere rækken. Den vises som celleværdien for en sammenkædet celle i ruden **Datavælger** og på kortet **Oplysninger**. 
    - Feltværdien **Nøglekolonne** indeholder det entydige id for rækken. Denne værdi gør det muligt for Excel at sammenkæde en celle med en bestemt række i tabellen.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Opsæt fremhævet tabel":::

1. Når du har udgivet eller importeret datasættet til Power BI-tjenesten, vises den fremhævede tabel i Excel-datatypegalleriet. Du og andre forfattere af rapporter kan også oprette rapporter, der er bygget ud fra dette datasæt.

1. I Excel: 
    - Excel cachelagrer listen over datatyper, så du skal genstarte Excel for at se nyligt udgivede, fremhævede tabeller.
    - Nogle datasæt understøttes ikke. De udvalgte tabeller, der er defineret i disse datasæt, vises ikke i Excel. Se næste afsnit, Overvejelser og begrænsninger, for at få flere oplysninger.

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Her er de aktuelle begrænsninger:

- Integrationen er tilgængelig i Excel i den aktuelle kanal.
- Udvalgte tabeller i Power BI-datasæt, der bruger følgende funktioner, vises ikke i Excel: 

    - DirectQuery-datasæt.
    - Datasæt med en direkte forbindelse.

- Excel viser kun data i kolonner, beregnede kolonner og målinger, der er defineret i den udvalgte tabel. Følgende er ikke angivet:
   
    - Målinger, der er defineret for relaterede tabeller.
    - Implicitte målinger, der er beregnet på baggrund af relationer.

- Excel viser kun udvalgte tabeller (*datatyper*), der er gemt i de nye Power BI-arbejdsområder. Udvalgte tabeller, der er gemt i de klassiske arbejdsområder, vises ikke som datatyper i Excel. Du kan [opgradere klassiske arbejdsområder til de nye arbejdsområder](service-upgrade-workspaces.md) i Power BI.

Datatyperne i Excel svarer til en opslagsfunktion. Det kræver en celleværdi, der er angivet i Excel-arket, og der søges efter tilsvarende rækker i udvalgte Power BI-tabeller. Søgeoplevelsen har følgende funktionsmåder:

- Rækkematchning er baseret på tekstkolonner i den udvalgte tabel. Den bruger den samme indeksering som Power BI Q&A-funktionen, som er optimeret til engelsksprogede søgninger. Søgning på andre sprog resulterer muligvis ikke i præcise matches. 
- Der søges ikke efter matches i de fleste numeriske kolonner. Hvis Rækkemærkat eller Nøglekolonne er numeriske, søges der efter matches i dem.
- Matchning er baseret på præcise og præfiksbaserede matches til individuelle søgeord. En celles værdi opdeles på baggrund af mellemrum eller andre mellemrumstegn, f.eks. faner. Derefter betragtes hvert ord som et søgeord. Værdier i en rækkes tekstfelt sammenlignes med hvert søgeord for at finde nøjagtige og præfiksbaserede forekomster. Der returneres en præfiksforekomst, hvis rækkens tekstfelt starter med søgeordet. Hvis en celle f.eks. indeholder "Orange County", så er "Orange" og "County" separate søgetermer. 

    - Rækker med tekstkolonner, hvis værdier svarer nøjagtigt til "Orange" eller "County", returneres. 
    - Rækker med tekstkolonner, hvis værdier starter med "Orange" eller "County", returneres. 
    - Det er vigtigt, at de rækker, der indeholder "Orange" eller "County", men ikke starter med dem, ikke returneres.

- Power BI returnerer maksimalt 100 rækkeforslag for hver celle.
- Nogle symboler understøttes ikke.
- Angivelse eller opdatering af den udvalgte tabel understøttes ikke for XMLA-slutpunktet
- Excel-filer med en datamodel kan bruges til at publicere udvalgte tabeller. Indlæs dataene i Power BI Desktop, og udgiv derefter den udvalgte tabel.
- Ændring af Tabelnavn, Rækkemærkat eller Nøglekolonne i den udvalgte tabel kan påvirke Excel-brugere, der har linket celler til rækker i tabellen. 
- Excel viser, hvornår dataene blev hentet fra Power BI-datasættet. Dette tidspunkt er ikke nødvendigvis det tidspunkt, hvor dataene blev opdateret i Power BI, eller tidspunktet for det seneste datapunkt i et datasæt. Antag f.eks., at et datasæt i Power BI blev opdateret for en uge siden, men de underliggende kildedata var en uge gammel, da opdateringen fandt sted. De faktiske data ville være to uger gamle, men Excel viser data, der hentes, som den dato og det klokkeslæt, hvor dataene blev indlæst i Excel.
- Under [Overvejelser og begrænsninger](service-excel-featured-tables.md#considerations-and-limitations) i artiklen "Få adgang til Power BI-tabeller i Excel" kan du finde andre Excel-overvejelser.

## <a name="next-steps"></a>Næste trin

- [Få adgang til Power BI-tabeller i Excel](service-excel-featured-tables.md)
- Læs om, hvordan du [bruger Excel-datatyper fra Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) i dokumentationen til Excel.
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

