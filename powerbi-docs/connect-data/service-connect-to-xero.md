---
title: Opret forbindelse til Xero med Power BI
description: Xero til Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 03/06/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: c942e399eb32fd7118d515f0d072972e3a820578
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410476"
---
# <a name="connect-to-xero-with-power-bi"></a>Opret forbindelse til Xero med Power BI
Xero er et brugervenligt online regnskabsprogram, der er udviklet specielt til små virksomheder. Opret overbevisende visualiseringer baseret på din bogføring i Xero med denne Power BI-skabelonapp. Standarddashboardet indeholder mange metrikværdier for små virksomheder, f.eks. likviditet, indtægter i forhold til udgifter, avancetendens, debitordage og afkastningsgrad.

Opret forbindelse til [Xero-skabelonappen](https://app.powerbi.com/getdata/services/xero) til Power BI, eller få mere at vide om integration af [Xero og Power BI](https://help.xero.com/Power-BI).

## <a name="how-to-connect"></a>Sådan opretter du forbindelse

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Vælg **Xero** \> **Hent nu**.
4. Vælg **Installér** under **Installér denne Power BI-app?** .

    ![Installér Xero](media/service-connect-to-xero/power-bi-install-xero.png)

4. Vælg feltet **Xero** i ruden **App**.

   ![Vælg Xero-feltet](media/service-connect-to-xero/power-bi-start-xero.png)

6. Under **Kom i gang med din nye app** skal du vælge **Opret forbindelse**.

    ![Kom i gang med din nye app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Angiv et kaldenavn for den organisation, der er knyttet til din Xero-konto. Du kan kalde den hvad som helst. Det er hovedsageligt for at hjælpe brugere med flere Xero-organisationer med at skelne dem fra hinanden. Se oplysninger om [at finde parametre](#FindingParams) senere i denne artikel.

    ![Kaldenavn for organisation](media/service-connect-to-xero/params.png)

5. Vælg **OAuth** for **Godkendelsesmetode**. Når du bliver bedt om det, skal du logge på din Xero-konto og vælge den organisation, du vil oprette forbindelse til. Når logonprocessen er fuldført, skal du vælge **Log på** for at starte indlæsningsprocessen.
   
    ![Godkendelsesmetode](media/service-connect-to-xero/creds.png)
   
    ![Velkommen til Xero](media/service-connect-to-xero/creds2.png)
6. Efter godkendelsen startes importprocessen automatisk. Når processen er fuldført, vises der et nyt dashboard samt en ny rapport og model i navigationsruden. Vælg dashboardet for at få vist de importerede data.
   
     ![Xero-dashboard](media/service-connect-to-xero/power-bi-xero-dashboard.png)

**Hvad nu?**

* Prøv [at stille et spørgsmål i feltet Spørgsmål og svar](../consumer/end-user-q-and-a.md) øverst i dashboard'et
* [Rediger felterne](../create-reports/service-dashboard-edit-tile.md) i dashboard'et.
* [Vælg et felt](../consumer/end-user-tiles.md) for at åbne den underliggende rapport.
* Selvom dit datasæt opdateres dagligt, kan du ændre tidsplanen for opdatering eller prøve at opdatere det efter behov ved hjælp af **Opdater nu**

## <a name="whats-included"></a>Det følgende er inkluderet
Skabelonappens dashboard indeholder felter og metrikværdier, der dækker en lang række områder med tilsvarende rapporter, hvor man kan få flere oplysninger:  

| Område | Dashboardfelter | Rapport |
| --- | --- | --- |
| Penge |Dagligt Cashflow <br>Indbetal <br>Udbetal <br>Ultimosaldo efter konto <br>Closing balance today |Konti |
| Kunde |Faktureret salg <br>Faktureret salg efter kunde <br>Faktureret Salgsvækst tendens <br>Fakturaer forfalden <br>Udestående tilgodehavender <br>Forfalden tilgodehavender |Kunde <br>Lager |
| Leverandør |Køb faktureres <br>Faktureret indkøb efter leverandør <br>Køb faktureres væksttendens <br> Fakturaer forfaldsdato <br>Udestående skyldige beløb <br>Overskredne skyldige beløb |Leverandører <br>Lager |
| Lager |Månedlige salgsbeløb efter produkt |Lager |
| Resultatopgørelse |Månedlige resultatopgørelse <br>Overskud dette regnskabsår <br>Overskud denne måned <br>Mest populære udgift konti |Resultatopgørelse |
| Balancen |Samlede aktiver <br>Samlede passiver <br>Lighed |Balancen |
| Tilstand |Likviditetsgrad <br>Bruttoavance procentdel <br> Returner af samlede aktiver <br>Samlede passiver aktie forholdet mellem |Tilstand <br>Ordliste og tekniske noter |

Datasættet indeholder også følgende tabeller til at tilpasse dine rapporter og dashboards:  

* Adresser  
* Alerts  
* Bank-sætningen daglig saldo  
* Bank-sætninger.  
* Kontakter  
* Udgift krav  
* Linje Fakturaelementer  
* Fakturaer  
* Elementer  
* Slutningen af måneden  
* Organisation  
* Generelle kontooversigt  
* Xero-konti

## <a name="system-requirements"></a>Systemkrav
Følgende roller er påkrævet for at få adgang til Xero-skabelonappen: "Standard + Rapporter" eller "Rådgiver".

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Søgning efter parametre
Angiv et navn på din organisation, der skal spores i Power BI. Et navn giver dig mulighed for at oprette forbindelse til flere forskellige organisationer. Du kan ikke oprette forbindelse til den samme organisation flere gange, da det påvirker den planlagte opdatering.   

## <a name="troubleshooting"></a>Fejlfinding
* Xero-brugere skal have følgende roller for at få adgang til Xero-skabelonappen til Power BI: "Standard + Rapporter" eller "Rådgiver". Skabelonappen er afhængig af de brugerbaserede tilladelser til at få adgang til rapportdata via Power BI.
* Under indlæsningen er felterne på dashboardet i en generisk indlæsningstilstand. De forbliver på den måde, indtil hele indlæsningen er fuldført. Hvis du får en meddelelse om, at din indlæsning er fuldført, men felterne stadig er under indlæsning, skal du prøve at opdatere dashboardfelterne ved hjælp af den ... i øverste højre hjørne af dashboardet.
* Hvis din skabelonapp ikke opdateres, skal du kontrollere, om du har oprettet forbindelse til den samme organisation mere end én gang i Power BI. Xero tillader kun en enkelt aktiv forbindelse til en organisation, og du kan få vist en fejl, der angiver, at dine legitimationsoplysninger er ugyldige, hvis du opretter forbindelse til den samme mere end én gang.  
* Hvis du har problemer med at oprette forbindelse til Xero-skabelonappen til Power BI, f.eks. fejlmeddelelser eller meget langsom indlæsning, skal du først rydde din cache/cookies og genstarte browseren, og derefter skal du oprette forbindelse til Power BI igen.  

Hvis du oplever andre problemer, eller hvis problemet er vedvarende, skal du oprette en supportanmodning på https://support.powerbi.com.

## <a name="next-steps"></a>Næste trin
[Kom i gang med Power BI](../fundamentals/service-get-started.md)

[Hent data i Power BI](service-get-data.md)
