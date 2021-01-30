---
title: Størrelse af datagateway i det lokale miljø
description: Vejledning til arbejde med størrelse på datagatewayen i det lokale miljø.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/30/2019
ms.openlocfilehash: 35630891a66b9aed0b9e568d8e34180e3ee41544
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088390"
---
# <a name="on-premises-data-gateway-sizing"></a>Størrelse af datagateway i det lokale miljø

Denne artikel er målrettet Power BI-administratorer, der skal installere og administrere [datagatewayen i det lokale miljø](../connect-data/service-gateway-onprem.md).

Gatewayen er påkrævet, når Power BI skal have adgang til data, der ikke er tilgængelige direkte via internettet. Den kan installeres på en server i det lokale miljø eller på en VM-hostet IaaS (Infrastruktur som en service).

## <a name="gateway-workloads"></a>Gateway-arbejdsbelastninger

Datagatewayen i det lokale miljø understøtter to arbejdsbelastninger. Det er vigtigt, at du først forstår disse arbejdsbelastninger, før vi kommer ind på gatewaystørrelsen og -anbefalingerne.

### <a name="cached-data-workload"></a>Arbejdsbelastning for cachelagrede data

Arbejdsbelastningen for _cachelagrede data_ henter og transformerer kildedata til indlæsning i Power BI-datasæt. Det gør den i tre trin:

1. **Forbindelse**: Gatewayen opretter forbindelse til kildedata
1. **Datahentning og transformation**: Dataene hentes og transformeres om nødvendigt. Når det er muligt, sender Power Query-miksprogrammet transformationstrin til datakilden – hvilket kaldes _[forespørgselsdelegering](power-query-folding.md)_ . Hvis det ikke er muligt, skal transformationer udføres af gatewayen. I dette tilfælde forbruger gatewayen flere CPU- og hukommelsesressourcer.
1. **Overfør**: Data overføres til Power BI-tjenesten – det er vigtigt med en pålidelig og hurtig internetforbindelse, især ved store datamængder

![Diagram over cachelagrede data, der viser datagatewayen i det lokale miljø, som opretter forbindelse til kilder i det lokale miljø.](media/gateway-onprem-sizing/gateway-onprem-workload-cached-data.png)

### <a name="live-connection-and-directquery-workloads"></a>Direkte forbindelse- og DirectQuery-arbejdsbelastninger

Arbejdsbelastningen _Direkte forbindelse og DirectQuery_ bruges mest i pass-through-tilstand. Power BI-tjenesten sender forespørgsler, og gatewayen svarer med forespørgselsresultater. Generelt fylder forespørgselsresultater ikke ret meget.

- Du kan finde flere oplysninger om direkte forbindelse under [Datasæt i Power BI-tjenesten (eksternt hostede modeller)](../connect-data/service-datasets-understand.md#external-hosted-models).
- Du kan finde flere oplysninger om DirectQuery under [Datasæt i Power BI-tjenesten (eksternt hostede modeller)](../connect-data/service-dataset-modes-understand.md#directquery-mode).

Denne arbejdsbelastning kræver CPU-ressourcer til routing af forespørgsler og forespørgselsresultater. Der er normalt meget mindre CPU-efterspørgsel end det, der kræves af arbejdsbelastningen for cachelagrede data – især når det er nødvendigt for at transformere data til cachelagring.

Sikker, hurtig og konsekvent forbindelse er vigtig for at sikre, at rapportbrugerne får en dynamisk oplevelse.

![Diagram over direkte forbindelse og DirectQuery, der viser data gatewayen i det lokale miljø, som opretter forbindelse til datakilder i det lokale miljø.](media/gateway-onprem-sizing/gateway-onprem-workload-liveconnection-directquery.png)

## <a name="sizing-considerations"></a>Overvejelser i forbindelse med størrelse

Det kan afhænge af følgende variabler, hvordan du bestemmer den korrekte størrelse for din gateway computer:

- For arbejdsbelastning for cachelagrede data:
  - Antallet af samtidige datasæt, der opdateres
  - Typerne af datakilder (relationsdatabase, analytisk database, datafeeds eller filer)
  - Den mængde data, der skal hentes fra datakilder
  - De transformationer, der skal udføres af Power Query-miksprogrammet
  - Den mængde data, der skal overføres til Power BI-tjenesten
- For Direkte forbindelse- og DirectQuery-arbejdsbelastninger:
  - Antallet af samtidige rapportbrugere
  - Antallet af visuals på rapportsider (hvert enkelt visual sender mindst én forespørgsel)
  - Frekvensen af opdateringer af forespørgselscache for Power BI-dashboard
  - Antallet af rapporter i realtid, der bruger funktionen [Automatisk sideopdatering](../create-reports/desktop-automatic-page-refresh.md)
  - Angiver, om datasæt gennemtvinger [sikkerhed på rækkeniveau (RLS)](../create-reports/desktop-rls.md)

Generelt kræver direkte forbindelse og DirectQuery-arbejdsbelastninger tilstrækkelige CPU-ressourcer, mens arbejdsbelastninger for cachelagede data kræver mere CPU og hukommelse. Begge arbejdsbelastninger afhænger af, at der er en god forbindelse til Power BI-tjenesten og datakilderne.

> [!NOTE]
> Power BI-kapaciteter sætter grænser for parallelle modelopdateringer og Direkte forbindelse- og DirectQuery-gennemløb. Der er ingen grund til at tilpasse gatewaystørrelsen, så den leverer mere end det, Power BI-tjenesten understøtter. Der gælder andre begrænsninger med Premium SKU (og A SKU med en tilsvarende størrelse). Du kan finde flere oplysninger i [Hvad er Power BI Premium? (kapacitetsnoder)](../admin/service-premium-what-is.md#capacity-nodes).

## <a name="recommendations"></a>Anbefalinger

Anbefalingerne for gatewaystørrelsen afhænger af mange variabler. I dette afsnit giver vi dig generelle anbefalinger, som du kan tage med i overvejelserne.

### <a name="initial-sizing"></a>Startstørrelse

Det kan være svært at beregne den rigtige størrelse nøjagtigt. Vi anbefaler, at du starter med en maskine med mindst 8 CPU-kerner, 8 GB RAM og flere Gigabit-netværkskort. Du kan derefter måle en typisk gatewaybelastning ved at logføre tællerresultater for CPU- og hukommelsessystem. Du kan finde flere oplysninger under [Overvåg og optimer ydeevne for data gateways i det lokale miljø](/data-integration/gateway/service-gateway-performance).

### <a name="connectivity"></a>Forbindelser

Planlæg den bedst mulige forbindelse mellem Power BI-tjenesten og din gateway samt din gateway og datakilderne.

- Tilstræb pålidelighed, hurtige hastigheder og lave, ensartede ventetider
- Fjern – eller reducer – maskinhop mellem gatewayen og dine datakilder
- Fjern alle netværksbegrænsninger, der pålægges af firewall-proxy-laget. Du kan finde flere oplysninger om Power BI's slutpunkter i [Føj Power BI URL-adresser til din hvidliste](../admin/power-bi-allow-list-urls.md).
- Konfigurer [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) til at oprette en privat, administreret forbindelse til Power BI
- Ved datakilder i Azure VM'er, skal du sikre, at VM'er er [placeret sammen med Power BI-tjenesten](../admin/service-admin-where-is-my-tenant-located.md)
- Sørg for, at der er en god forbindelse mellem gatewaymaskinen og Active Directory i det lokale miljø for arbejdsbelastninger for direkte forbindelser til SQL Server Analysis Services (SSAS), der involverer dynamisk sikkerhed på rækkeniveau

### <a name="clustering"></a>Clustering

I forbindelse med udrulninger i stor skala kan du oprette en gateway til klyngeinstallationer. Med klynger undgås enkelte fejlpunkter, og der kan udføres belastningsjustering af trafik på tværs af gateways. Du kan:

- Installere en eller flere gateways i en klynge
- Isolere arbejdsbelastninger til separate gateways eller klynger af gatewayservere

Du kan finde flere oplysninger under [Administrer klynger med høj tilgængelighed og belastningsjustering for datagateways i det lokale miljø](/data-integration/gateway/service-gateway-high-availability-clusters).

### <a name="dataset-design-and-settings"></a>Datasætdesign og -indstillinger

Datasætdesign og deres indstillinger kan påvirke arbejdsbelastningen for gatewayen. Hvis du vil reducere gatewaybelastningen, kan du overveje følgende handlinger.

For importdatasæt:

- Konfigurer mindre hyppig opdatering af data
- Konfigurer [trinvis opdatering](../admin/service-premium-incremental-refresh.md) for at minimere den mængde data, der skal overføres
- Når det er muligt, skal du sørge for, at der foretages [forespørgselsdelegering](power-query-folding.md)
- Konverter designet til en DirectQuery-model eller [sammensat](../connect-data/service-dataset-modes-understand.md#composite-mode) model, især ved store datamængder eller behov for resultater med kort ventetid

For DirectQuery-datasæt:

- Optimere datakilder samt model- og rapportdesign – du kan finde flere oplysninger under [Vejledning til DirectQuery-modeller i Power BI Desktop](directquery-model-guidance.md)
- Opret [sammenlægninger](../transform-model/desktop-aggregations.md) for at cachelagre resultater på højere niveauer og dermed reducere antallet af DirectQuery-anmodninger
- Begræns intervaller for [Automatisk sideopdatering](../create-reports/desktop-automatic-page-refresh.md) i rapportdesign og kapacitetsindstillinger
- Begræns opdateringsfrekvensen for dashboardcachen, især når der gennemtvinges dynamisk sikkerhed på rækkeniveau
- Konverter designet til en importmodel eller [sammensat](../connect-data/service-dataset-modes-understand.md#composite-mode) model, især ved mindre datamængder eller i forbindelse med ikke-midlertidige data

For Direkte forbindelse-datasæt:

- Begræns opdateringsfrekvensen for dashboardcachen, især når der gennemtvinges dynamisk sikkerhed på rækkeniveau

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Vejledning i at installere en datagateway til Power BI](../connect-data/service-gateway-deployment-guidance.md)
- [Konfigurer proxyindstillinger for datagatewayen i det lokale miljø](/data-integration/gateway/service-gateway-proxy)
- [Overvåg og optimer ydeevne for datagateways i det lokale miljø](/data-integration/gateway/service-gateway-performance)
- [Foretag fejlfinding af gateways – Power BI](../connect-data/service-gateway-onprem-tshoot.md)
- [Foretag fejlfinding af datagatewayen i det lokale miljø](/data-integration/gateway/service-gateway-tshoot)
- [Vigtigheden af forespørgselsdelegering](power-query-folding.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)
