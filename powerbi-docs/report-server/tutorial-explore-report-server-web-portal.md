---
title: 'Selvstudium: Udforsk Power BI Report Server i en VM'
description: I dette selvstudium skal du oprette en virtuel maskine med Power BI-rapportserveren, der allerede er installeret, og udforske webportalen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: tutorial
ms.date: 05/06/2019
ms.openlocfilehash: 85fcd6249a833c35cb98fca6abf2881ab1a4bf7e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418411"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>Selvstudium: Udforsk webportalen til Power BI-rapportserver i en VM
I dette selvstudium skal du oprette en virtuel Azure-maskine med Power BI-rapportserver, der allerede er installeret, så du kan få vist, redigere og administrere eksempler på Power BI og sideinddelte rapporter samt KPI'er.

![Webportalen Rapportserver](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

Her er de opgaver, du skal udføre i dette selvstudium:

> [!div class="checklist"]
> * Opret en VM, og opret forbindelse til den
> * Start og udforsk webportalen til Power BI-rapportserver
> * Markér et element som favorit
> * Få vist og rediger en rapport i Power BI
> * Få vist, administrer og rediger en sideinddelt rapport
> * Få vist en Excel-projektmappe i Excel Online

Til dette selvstudium skal du have et Azure-abonnement. Hvis du ikke har en, skal du oprette en [gratis konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F), før du begynder.

## <a name="create-a-power-bi-report-server-vm"></a>Opret en virtuel maskine til Power BI-rapportserveren

Power BI-teamet har heldigvis oprettet en VM, der leveres sammen med Power BI-rapportserveren, som allerede er installeret.

1. Vælg Power BI-rapportserver på Azure Marketplace. Med dette links åbnes det direkte: [Power BI-rapportserver](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview).  

2. Vælg **Hent det nu**.
3. Vælg **Fortsæt** for at acceptere udbyderens vilkår for anvendelse og politik om beskyttelse af personlige oplysninger.

4. Vælg **Opret**.

    ![Opret en virtuel maskine til Power BI-rapportserveren](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create.png)

5. Angiv **navnet på VM'en** som **reportservervm** under **Trin 1 Grundlæggende**.

    Navnet på VM'en i Power BI-rapportserver må ikke indeholde bindestreger.

5. Opret et brugernavn og en adgangskode.

6. Som **Ressourcegruppe** skal du vælge **Opret ny** og kalde den for **reportserverresourcegroup** > **OK**.

    Hvis du gennemgår selvstudiet mere end én gang, skal du give ressourcegruppen et andet navn efter den første gang. Du kan ikke bruge samme navn på ressourcegruppen to gange i ét abonnement. 

    ![Navnet på VM'en og ressourcegruppen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

7. Bevar de andre standarder > **OK**.

8. Under **Trin 2 Indstillinger** skal du beholde standarderne > **OK**.
 
    Værdierne for **SQL Storage-kontoen** og **Diagnostics Storage-kontoen** skal også være entydige. Hvis du gennemgår selvstudiet mere end én gang, skal du give dem forskellige navne.

9. Under **Trin 3 Oversigt** skal du gennemse dine valg > **OK**.

10. Under **Trin 4 Køb** skal du gennemse Vilkår for anvendelse og Politik om beskyttelse af personlige oplysninger > **Opret**.

    Processen **Indsendelse af udrulning til Power BI-rapportserver** kan tage flere minutter.

## <a name="connect-to-your-virtual-machine"></a>Opret forbindelse til din virtuelle maskine

1. Vælg **Virtuelle maskiner** i navigationsruden i Azure. 

2. I feltet **Filtrer efter navn** skal du skrive "rapport". 

3. Vælg den VM, der hedder **REPORTSERVERVM**.

    ![Få vist den virtuelle maskine](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. Vælg **Opret forbindelse** under den virtuelle maskine REPORTSERVERVM.

    ![Opret forbindelse til den virtuelle maskine](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. I ruden **Opret forbindelse til virtuel maskine** skal du bevare standarderne og vælge **Download RDP-fil**.

1. I dialogboksen **Forbindelse til fjernskrivebord** skal du vælge **Opret forbindelse**.

6. Angiv det navn og den adgangskode, du har oprettet for VM'en > **OK**.

7. I næste dialogboks står der **Identiteten af fjerncomputeren kan ikke identificeres**. Vælg **Ja**.

   Sådan – din nye VM åbnes.

## <a name="power-bi-report-server-on-the-vm"></a>Power BI-rapportserver på den virtuelle maskine

Når din VM åbner, vises følgende elementer på skrivebordet.

![Den virtuelle maskine på Power BI-rapportserveren starter](media/tutorial-explore-report-server-web-portal/power-bi-report-server-vm-5-numbers.png)

|Tal  |Hvad er det  |
|---------|---------|
|![Nummer 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Eksempel på Power BI-rapporter (.PBIX) |
|![Nummer 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Links til dokumentation til Power BI-rapportserveren |
|![Nummer 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Starter Power BI Desktop optimeret til Power BI-rapportserver (januar 2019) |
|![Nummer 4](media/tutorial-explore-report-server-web-portal/number-4.png) | Åbner webportalen til Power BI-rapportserveren i browseren |
|![Nummer 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Starter SQL Server Data Tools for at oprette sideinddelte rapporter (. RDL) |

Dobbeltklik på ikonet **Webportalen Rapportserver**. Browseren åbner `https://localhost/reports/browse`. Du kan se forskellige filer grupperet efter type på webportalen. 

![Webportalen til Power BI-rapportserver](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|Tal  |Hvad er det  |
|---------|---------|
|![Nummer 1](media/tutorial-explore-report-server-web-portal/number-1.png) | KPI'er oprettet på webportalen |
|![Nummer 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Power BI-rapporter (.PBIX)  |
|![Nummer 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Mobilrapporter, der er oprettet i Mobile Report Publisher til SQL Server  |
|![Nummer 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  Sideinddelte rapporter, der er oprettet i Report Builder eller SQL Server Data Tools  |
|![Nummer 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Excel-projektmapper   | 
|![Nummer 6](media/tutorial-explore-report-server-web-portal/number-6.png) | Datakilder til sideinddelte rapporter | 


## <a name="tag-your-favorites"></a>Tag dine favoritter
Du kan mærke rapporter og KPI'er, som skal være favoritter. De er lettere at finde, fordi de alle sammen er samlet i en enkelt Favoritter-mappe, både i webportalen og i Power BI-mobilappsene. 

1. Klik på ellipsen ( **...** ) i øverste højre hjørne af **Avance** > KPI > **Føj til Favoritter**.
   
    ![Føj til Favoritter](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. Vælg **Favoritter** på båndet på webportalen for at se den sammen med andre favoritter på siden Favoritter på webportalen.
   
    ![Vis Favoritter.](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. Vælg **Gennemse** for at vende tilbage til webportalen.
   
## <a name="view-items-in-list-view"></a>Vis elementer i listevisning
Som standard vises indholdet på webportalen i Felt-visning.

Du kan skifte til Liste-visning, hvor det er nemt at flytte eller slette flere elementer ad gangen. 

1. Vælg **Felter** > **Liste**.
   
    ![Skift visninger.](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. Gå tilbage til visning af felter: Vælg **Liste** > **Felter**.

## <a name="power-bi-reports"></a>Power BI-rapporter

Du kan få vist og interagere med Power BI-rapporter på webportalen og starte Power BI Desktop direkte fra webportalen.

### <a name="view-power-bi-reports"></a>Se Power BI-rapporter

1. Under **Power BI-rapporter** på webportalen skal du vælge **Eksempel på kundeoversigtsrapport**. Rapporten åbnes i browseren.

1. Vælg USA-blokken i træstrukturen for at se, hvordan den fremhæver relaterede værdier i de andre visuelle elementer.

    ![Fremhævet Power BI-rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>Rediger i Power BI Desktop

1. Vælg **Rediger i Power BI Desktop**.

1. Vælg **Tillad** for at give dette websted tilladelse til at åbne et program på din computer. 

     Rapporten åbnes i Power BI Desktop. Bemærk navnet på den øverste linje "Power BI Desktop (januar 2019)". Det er den version, der er optimeret til Power BI-rapportserveren.

    Brug den version af Power BI Desktop, der er installeret på VM'en. Du kan ikke skifte mellem domæner for at uploade en rapport.

3. Udvid tabellen Kunder i ruden Felter, og træk feltet Beskæftigelse til Filtre på rapporteringsniveau.

    ![Træk et felt til ruden Filtre](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. Gem rapporten.

1. Gå tilbage til rapporten i browseren, og vælg ikonet **Opdater** for browseren.

    ![Ikonet Opdater for browser](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. Udvid ruden **Filtre** til højre for at se filteret **Beskæftigelse**, som du har tilføjet. Vælg **Professional**.

    ![Filtreret Power BI-rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. Vælg **Gennemse** for at vende tilbage til webportalen.

## <a name="paginated-rdl-reports"></a>Sideinddelte rapporter (.RDL)

Du kan få vist og administrere sideinddelte rapporter og starte Report Builder fra webportalen.

### <a name="manage-a-paginated-report"></a>Administrer en sideinddelt rapport

1. På webportalen under **Sideinddelte rapporter** skal du vælge **Flere indstillinger** (...) ud for **Salgsordre** > **Administrer**.

1. Vælg **Parametre**, og skift standardværdien for **SalesOrderNumber** til **SO50689** > **Anvend**.

   ![Angiv rapportparametre](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. Vælg **Gennemse** for at vende tilbage til webportalen.

### <a name="view-a-paginated-report"></a>Se en sideinddelt rapport

1. Vælg **Salgsordre** på webportalen.
 
3.  Du kan se, at den åbnes med den parameter for **Ordre**, som du har angivet, **SO50689**. 

    ![Parameter for sideinddelt rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    Du kan ændre parameteren her – sammen med andre parametre – uden at ændre standardværdierne.

1. Vælg **Ordre** **SO48339** > **Vis rapport**.

4. Du kan se, at dette er side 1 af 2. Vælg højre pil for at se den næste side. Tabellen fortsætter på denne side.

    ![Sideinddelt rapport, side 2 af 2](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. Vælg **Gennemse** for at vende tilbage til webportalen.

### <a name="edit-a-paginated-report"></a>Rediger en sideinddelt rapport

Du kan redigere sideinddelte rapporter i Report Builder, og du kan starte Report Builder direkte fra browseren.

1. På webportalen skal du vælge **Flere indstillinger** (...) ud for **Salgsordre** > **Rediger i Report Builder**.

1. Vælg **Tillad** for at give dette websted tilladelse til at åbne et program på din computer.

1. Rapporten Salgsordre åbnes i designvisning i Report Builder.

    ![Designvisning, sideinddelt rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. Vælg **Kør** for at få vist rapporten.

    ![Se eksempel på en sideinddelt rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. Luk Report Builder, og gå tilbage til browseren.

## <a name="view-excel-workbooks"></a>Se Excel-projektmapper

Du kan få vist og interagere med Excel-projektmapper i Excel Online i Power BI-rapportserveren. 

1. Vælg Excel-projektmappen **Office Liquidation Sale.xlsx**. Du bliver måske bedt om at angive legitimationsoplysninger. Vælg **Annuller**. 
    Den åbnes på webportalen.
1. Vælg **Apparat** i udsnitsværktøjet.

    ![Excel Online på webportalen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. Vælg **Gennemse** for at vende tilbage til webportalen.

## <a name="clean-up-resources"></a>Fjern ressourcer

Nu, hvor du er færdig med dette selvstudium, kan du slette ressourcegruppen, den virtuelle maskine og alle relaterede ressourcer. 

- Det kan du gøre ved at vælge ressourcegruppen for VM'en og vælge **Slet**.

## <a name="next-steps"></a>Næste trin

I dette selvstudium har du oprettet en VM med Power BI-rapportserveren. Du har prøvet nogle af funktionerne på webportalen, og du har åbnet en Power BI-rapport og en sideinddelt rapport i deres respektive editors. Denne VM har SQL Server Analysis Services-datakilder installeret, så du kan prøve at oprette dine egne Power BI-rapporter og sideinddelte rapporter med de samme datakilder. 

Du kan få mere at vide om, hvordan du opretter rapporter til Power BI-rapportserveren, ved at læse videre.

> [!div class="nextstepaction"]
> [Opret en Power BI-rapport til Power BI-rapportserveren](./quickstart-create-powerbi-report.md)



