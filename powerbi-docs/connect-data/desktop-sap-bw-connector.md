---
title: Brug af SAP BW Connector (Business Warehouse) i Power BI Desktop
description: Brug af SAP BW Connector i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b3250124fa813f3da96e63455d483cf05f01cb6
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/30/2020
ms.locfileid: "91598845"
---
# <a name="use-the-sap-business-warehouse-connector-in-power-bi-desktop"></a>Brug af SAP BW Connector (Business Warehouse) i Power BI Desktop

Med Power BI Desktop har du adgang til data i *SAP Business Warehouse (BW)* .

Du kan få oplysninger om, hvordan SAP-kunder kan drage nytte af at integrere Power BI i deres eksisterende SAP BW-systemer i [Whitepaper til Power BI og SAP BW](https://aka.ms/powerbiandsapbw). Du kan få flere oplysninger om brug af DirectQuery med SAP BW i [DirectQuery og SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

Fra og med udgivelsen af Power BI Desktop fra juni 2018 og den offentligt tilgængelige udgivelse fra oktober 2018 kan du bruge *SAP BW Connector* med en implementering, der indeholder markante forbedringer af ydeevnen og egenskaberne. Microsoft udviklede SAP BW Connector *Implementation 2.0*. Du kan vælge enten version 1 af SAP BW Connector eller Implementation 2.0 SAP Connector. I de følgende afsnit beskrives installationen af hver version. Du kan vælge den ene eller den anden connector, når du opretter forbindelse til SAP BW fra Power BI Desktop.

Vi foreslår, at du bruger Implementation 2.0 SAP Connector, når det er muligt.

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>Installation af version 1 af SAP BW-connectoren

Vi anbefaler, at du bruger Implementation 2.0 SAP Connector, når det er muligt. I dette afsnit beskrives installationen af version 1 af SAP BW Connector.

1. Installer biblioteket *SAP NetWeaver* på din lokale computer. Du kan hente biblioteket SAP NetWeaver fra SAP-administratoren eller direkte fra [SAP Software Download Center](https://support.sap.com/swdc). Da strukturen i SAP Software Download Center ofte ændres, kan vi ikke give en mere specifik vejledning til, hvordan du henter programmet. SAP NetWeaver-biblioteket er som regel medtaget i installationen af SAP-klientværktøjer.

   Du kan søge efter *SAP-bemærkning nr. 1025361* for at få oplyst downloadplaceringen af den seneste version. Sørg for, at arkitekturen for SAP NetWeaver-biblioteket (32-bit eller 64-bit) svarer til din Power BI Desktop-installation. Installer alle de filer, der er inkluderet i *SAP NetWeaver RFC SDK* i henhold til SAP-bemærkningen.
2. Vælg **Hent data** i Power BI Desktop. Indstillingen **Database** indeholder *SAP Business Warehouse Application Server* og *SAP Business Warehouse Message Server*.

   ![Indstillingen Hent data for SAP](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Installation af Implementation 2.0 SAP Connector

Implementation 2.0 af SAP Connector kræver SAP .NET Connector 3.0. Adgang til download kræver en gyldig S-bruger. Kontakt dit SAP-basisteam for at få SAP .NET Connector 3.0.

Du kan downloade [SAP .NET Connector 3.0](https://support.sap.com/en/product/connectors/msnet.html) fra SAP.

Connectoren leveres i 32-bit- og 64-bit-versioner. Vælg den version, der stemmer overens med din Power BI Desktop-installation. I øjeblikket er der to versioner på webstedet til .NET 4.0-framework:

* SAP Connector til Microsoft .NET 3.0.22.0 til Windows 32-bit (x86) som ZIP-fil (6.896 KB), 1. juni 2019
* SAP Connector til Microsoft .NET 3.0.22.0 til Windows 64-bit (x64) som ZIP-fil (7.180 KB), 1. juni 2019

Når du installerer, skal du i **Valgfri installationstrin** sørge for, at du vælger *Installer assemblies til GAC*.

![Valgfri installationstrin for SAP](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> Den første version af SAP BW-implementeringen kræver NetWeaver-DLL-filer. Hvis du bruger Implementation 2.0 af SAP Connector, og du ikke bruger den første version, er NetWeaver DLL-filerne ikke påkrævet.

## <a name="version-1-sap-bw-connector-features"></a>Funktioner i version 1 af SAP BW Connector

Med version 1 af SAP BW Connector i Power BI Desktop kan du importere data fra dine *SAP Business Warehouse Server-kuber* eller bruge DirectQuery.

Du kan finde flere oplysninger om SAP BW Connector, og hvordan du bruger den sammen med DirectQuery, i artiklen [DirectQuery og SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

Når du opretter forbindelse, skal du angive en **server**, et **systemnummer** og et **klient-id** for at oprette forbindelsen.

![Indstillinger for SAP-serverforbindelse](media/desktop-sap-bw-connector/sap_bw_3a.png)

Du kan også angive to yderligere **avancerede indstillinger**: **Sprogkode** og en brugerdefineret **MDX-sætning** til at køre mod den angivne server.

![yderligere forbindelsesoplysninger](media/desktop-sap-bw-connector/sap_bw_4a.png)

Hvis du ikke angiver en MDX-sætning, viser forbindelsesindstillingen listen over de kuber, der er tilgængelige på serveren. Du kan foretage detailudledning og vælge elementer fra de tilgængelige kuber, herunder dimensioner og målinger. Power BI viser forespørgsler og kuber, der er vist af [Open Analysis-grænseflader](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Når du vælger ét eller flere elementer fra serveren, oprettes der et eksempel på outputtabellen i dialogboksen Navigator.

![Eksempelvisning af SAP-tabel](media/desktop-sap-bw-connector/sap_bw_5.png)

Dialogboksen **Navigator** indeholder også visningsmuligheder:

* **Vis kun valgte elementer**. Alle elementer vises som standard i **Navigator**.  Denne indstilling er nyttig til at bekræfte det sidste sæt valgte elementer. En alternativ metode til at få vist udvalgte elementer er ved at vælge kolonnenavne i eksempelområdet.
* **Aktivér datavisninger**. Denne værdi er standardværdien. Viser datavisninger. Deaktivering af dataeksempler reducerer antallet af kald til serveren, fordi der ikke længere anmodes om data til eksempelvisningerne.
* **Tekniske navne**. SAP BW understøtter *tekniske navne* for objekter i en kube. Tekniske navne giver ejeren af en kube mulighed for at vise *brugervenlige* navne for kubeobjekter i modsætning til kun at vise de *fysiske navne* for disse objekter i kuben.

![vinduet Navigator](media/desktop-sap-bw-connector/sap_bw_6.png)

Når du har valgt alle de nødvendige objekter, kan du beslutte, hvad du vil gøre, ved at vælge en af følgende indstillinger:

* Vælg **Indlæs** for at indlæse hele rækken af rækker for outputtabellen i Power BI Desktop-datamodellen. Visningen **Rapport** åbnes. Du kan begynde at visualisere dataene eller foretage yderligere ændringer ved hjælp af visningerne **Data** eller **Relationer**.
* Vælg **Rediger** for at åbne **Forespørgselseditor**. Angiv yderligere datatransformation og filtrer trin, før hele sættet af rækker overføres til Power BI Desktop-datamodellen.

Ud over at importere data fra SAP BW-kuber kan du også importere data fra en lang række andre datakilder i Power BI Desktop og derefter samle dem til en enkelt rapport. Denne mulighed giver mange typer interessante scenarier til rapportering og analyser ud fra SAP BW-data.

## <a name="using-implementation-20-sap-bw-connector"></a>Brug af Implementation 2.0 SAP BW Connector

Du skal oprette en ny forbindelse for at bruge Implementation 2.0 af SAP BW Connector. Følg disse trin for at oprette en ny forbindelse.

1. Vælg **Hent data**. Vælg enten **SAP Business Warehouse Application Server** eller **SAP Business Warehouse Message Server**, og opret derefter forbindelse.

2. Vælg implementeringen i dialogboksen Ny forbindelse. Hvis du vælger **2.0** for **Implementation**, som vist på følgende billede, aktiveres **Eksekveringstilstand**, **Batchstørrelse** og **Aktivér karakteristiske strukturer**.

    ![Dialogboksen SAP-forbindelse](media/desktop-sap-bw-connector/sap_bw_7.png)

3. Vælg **OK**. Herefter er oplevelsen den samme som beskrevet i [funktioner i Version 1 SAP BW Connector](#version-1-sap-bw-connector-features) for version 1 SAP BW Connector.

### <a name="new-options-for-implementation-20"></a>Nye indstillinger for Implementation 2.0

Implementation 2.0 understøtter følgende indstillinger:

* *ExecutionMode* – angiver den MDX-grænseflade, der bruges til at udføre forespørgsler på serveren. Følgende indstillinger er gyldige:

  * `SapBusinessWarehouseExecutionMode.BasXml`
  * `SapBusinessWarehouseExecutionMode.BasXmlGzip`
  * `SapBusinessWarehouseExecutionMode.DataStream`

    Standardværdien er `SapBusinessWarehouseExecutionMode.BasXmlGzip`.

    Hvis du bruger `SapBusinessWarehouseExecutionMode.BasXmlGzip`, kan det forbedre ydeevnen, hvis der er høje ventetider for store datasæt.

* *BatchSize* – angiver det maksimale antal rækker, der hentes ad gangen, når der udføres en MDX-sætning. Et lille antal vil medføre flere kald til serveren, når der hentes store datasæt. Et stort antal rækker kan forbedre ydeevnen, men det kan medføre hukommelsesproblemer på SAP BW-serveren. Standardværdien er 50.000 rækker.

* *EnableStructures* – indikerer, om der genkendes karakteristiske strukturer. Standardværdien for denne indstilling er falsk. Påvirker listen over de objekter, der kan vælges. Dette understøttes ikke med oprindelige forespørgsler.

Indstillingen *ScaleMeasures* frarådes i denne implementering. Funktionsmåden er nu den samme som indstillingen *ScaleMeasures = false*, som altid viser ikke-skalerede værdier.

### <a name="additional-improvements-for-implementation-20"></a>Yderligere forbedringer for Implementation 2.0

På følgende liste beskrives nogle yderligere forbedringer i den nye implementering:

* Bedre ydeevne.
* Mulighed for at hente flere millioner rækker af data og at finjustere ved hjælp af parameteren for batchstørrelsen.
* Muligheden for at skifte kørselstilstand.
* Understøttelse af komprimeret tilstand. Dette er især praktisk for forbindelse med høje ventetider eller store datasæt.
* Forbedret registrering af `Date`-variabler.
* [Eksperimentel] Vis dimensionerne `Date` (ABAP-typen DATS) og `Time` (ABAP-typen TIMS) som datoer og klokkeslæt i stedet for som tekstværdier.
* Bedre håndtering af undtagelser. De fejl, der opstår i BAPI-kald, bliver nu vist.
* Kolonnefoldning i tilstandene BasXml og BasXmlGzip. Hvis den genererede MDX-forespørgsel for eksempel henter 40 kolonner, men det aktuelle valg kun skal bruge 10, vil denne anmodning blive overført til serveren for at hente et mindre datasæt.

### <a name="changing-existing-reports-to-use-implementation-20"></a>Ændrer eksisterende rapporter til at bruge Implementation 2.0

Det er kun muligt at ændre eksisterende rapporter til at bruge Implementation 2.0 i importtilstand. Følg disse trin:

1. Åbn en eksisterende rapport, vælg **Rediger forespørgsler** på båndet, og vælg derefter den SAP Business Warehouse-forespørgsel, du vil opdatere.

1. Højreklik på forespørgslen, og vælg **Avanceret editor**.

1. I **Avanceret editor** skal du ændre `SapBusinessWarehouse.Cubes`-kaldet til følgende:

    Find ud af, om forespørgslen allerede indeholder en post med indstillinger som i eksemplet nedenfor:

    ![Skærmbillede, der viser en PlainText-forespørgsel med en post med indstillinger.](media/desktop-sap-bw-connector/sap_bw_9.png)

    Hvis det er tilfældet, skal du tilføje indstillingen `Implementation` 2.0 og fjerne indstillingen `ScaleMeasures`, hvis den findes, som vist:

    ![Skærmbillede, der viser en PlainText-forespørgsel med den tilføjede værdiimplementering = 2.0.](media/desktop-sap-bw-connector/sap_bw_10.png)

    Hvis forespørgslen ikke allerede indeholder en post med indstillinger, skal du tilføje den. For følgende indstilling:

    ![Skærmbillede, der viser en PlainText-forespørgsel med en post med indstillinger tilføjet.](media/desktop-sap-bw-connector/sap_bw_11.png)

    Skal du ændre den til:

    ![Skærmbillede, der viser en PlainText-forespørgsel for den nye indstilling med den tilføjede værdiimplementering = 2.0.](media/desktop-sap-bw-connector/sap_bw_12.png)

Vi har gjort alt for at gøre Implementation 2.0 af SAP BW Connector kompatibel med version 1. Der kan dog være nogle forskelle på grund af de forskellige SAP BW MDX-udførelsestilstande, der anvendes. Du kan forsøge at løse eventuelle uoverensstemmelser ved at skifte til en anden udførelsestilstand.

## <a name="troubleshooting"></a>Fejlfinding

Dette afsnit indeholder fejlfindingssituationer (og løsninger) til arbejdet med SAP BW-connectoren.

1. Numeriske data fra SAP BW returnerer decimaltegn i stedet for kommaer. 1,000,000 returneres f.eks. som 1.000.000.

   SAP BW returnerer decimaldata med enten et `,` (komma) eller et `.` (punktum) som decimalseparator. Når det skal angives, hvilken af dem SAP BW skal bruge som decimalseparator, foretager driveren, der bruges af Power BI Desktop, et kald til `BAPI_USER_GET_DETAIL`. Dette kald returnerer en struktur kaldet `DEFAULTS`, som indeholder feltet `DCPFM`, hvor *decimalformatets notation* er gemt. Dette felt kan have en af følgende tre værdier:

   * ' ' (mellemrum) = Decimaltegnet er et komma: N.NNN,NN
   * 'X' = Decimaltegnet er et punktum: N,NNN.NN
   * 'Y' = Decimaltegnet er N NNN NNN,NN

   Kunder, der har rapporteret dette problem, har registreret, at kaldet til `BAPI_USER_GET_DETAIL` mislykkes for en bestemt bruger (den bruger, der vises de forkerte data), med en fejlmeddelelse, der er meget lig følgende:

   ```xml
    You are not authorized to display users in group TI:
        <item>
            <TYPE>E</TYPE>
            <ID>01</ID>
            <NUMBER>512</NUMBER>
            <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
            <LOG_NO/>
            <LOG_MSG_NO>000000</LOG_MSG_NO>
            <MESSAGE_V1>TI</MESSAGE_V1>
            <MESSAGE_V2/>
            <MESSAGE_V3/>
            <MESSAGE_V4/>
            <PARAMETER/>
            <ROW>0</ROW>
            <FIELD>BNAME</FIELD>
            <SYSTEM>CLNTPW1400</SYSTEM>
        </item>
   ```

   For at løse problemet skal brugere bede deres SAP-administrator om at give den SAPBW-bruger, der anvendes i Power BI, ret til at udføre `BAPI_USER_GET_DETAIL`. Det er også en god ide at bekræfte, at brugeren har den krævede `DCPFM`-værdi som beskrevet tidligere i denne fejlfindingsløsning.

2. Forbindelse til SAP BEx-forespørgsler
   
   Du kan udføre BEx-forespørgsler i Power BI Desktop ved at aktivere en bestemt egenskab som vist på følgende billede:
   
   ![Aktiverer frigivelse til ekstern adgang](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. Der vises ikke et eksempel på data i vinduet **Navigator**, men i stedet vises fejlmeddelelsen *Objektreferencen er ikke indstillet til en forekomst af et objekt*.
   
   SAP-brugere skal have adgang til bestemte BAPI-funktionsmoduler for at få metadata og hente data fra SAP BW's InfoProviders. Disse moduler omfatter:

   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   Du løser dette problem ved at bekræfte, at brugeren har adgang til de forskellige MDPROVIDER-moduler samt `BAPI_IOBJ_GETDETAIL`. Hvis du vil foretage yderligere fejlfinding af dette eller lignende problemer, kan du aktivere sporing. **Vælg Fil** > **Indstillinger** > **Indstillinger**. Vælg **Diagnosticering** i **Indstillinger**, og vælg derefter **Aktivér sporing**. Prøv at hente data fra SAP BW, mens sporing er aktiv, og kig i sporingsfilen for at få flere detaljer.

## <a name="sap-bw-connection-support"></a>Understøttelse af SAP BW-forbindelse

Følgende tabel indeholder oplysninger om den aktuelle support af SAP BW.

|Produkt  |Tilstand  |Godkendelse  |Connector  |SNC-bibliotek  |Understøttet  |
|---------|---------|---------|---------|---------|---------|
|Power BI Desktop     |En hvilken som helst         | Bruger/adgangskode  | Programserver | I/T  | Ja  |
|Power BI Desktop     |En hvilken som helst         | Windows          | Programserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Desktop     |En hvilken som helst         | Windows via repræsentation | Programserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Desktop     |En hvilken som helst         | Bruger/adgangskode        | Meddelelsesserver | I/T  | Ja  |
|Power BI Desktop     |En hvilken som helst         | Windows        | Meddelelsesserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Desktop     |En hvilken som helst         | Windows via repræsentation | Meddelelsesserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Gateway     |Importér      | Samme som Power BI Desktop |         |   |   |
|Power BI Gateway     |DirectQuery | Bruger/adgangskode        | Programserver | I/T  | Ja  |
|Power BI Gateway     |DirectQuery | Windows via repræsentation (fast bruger, ingen SSO) | Programserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Gateway     |DirectQuery | Brug SSO via Kerberos til DirectQuery-forespørgsler | Programserver | sapcrypto + gsskrb5/gx64krb5   | Ja  |
|Power BI Gateway     |DirectQuery | Bruger/adgangskode        | Meddelelsesserver | I/T  | Ja  |
|Power BI Gateway     |DirectQuery | Windows via repræsentation (fast bruger, ingen SSO) | Meddelelsesserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Gateway     |DirectQuery | Brug SSO via Kerberos til DirectQuery-forespørgsler | Meddelelsesserver | gsskrb5/gx64krb5  | Nej  |
|Power BI Gateway     |DirectQuery | Brug SSO via Kerberos til DirectQuery-forespørgsler | Meddelelsesserver | sapcrypto  | Ja  |

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om SAP og DirectQuery i følgende ressourcer:

* [DirectQuery og SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery og SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [Brug af DirectQuery in Power BI](desktop-directquery-about.md)
* [Power BI-datakilder](power-bi-data-sources.md)
* [Hvidbog til Power BI og SAP BW](https://aka.ms/powerbiandsapbw)
