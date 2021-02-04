---
title: Power BI Embedded generation 2 er forklaret som en del af Power BI integreret analyse
description: Få mere at vide om det Power BI Embedded generation 2-tilbud i Power BI integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 02/03/2021
ms.openlocfilehash: fa72ab380cac1a1ac6d12cb431bdacfb5964ee83
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2021
ms.locfileid: "99534488"
---
# <a name="power-bi-embedded-generation-2-preview"></a>Power BI Embedded generation 2 (eksempelvisning)

Power BI Embedded har for nylig udgivet en ny version af Power BI Embedded, **Power bi Embedded generation 2**, der refereres til som **integreret Gen2** . Integreret Gen2 er i øjeblikket tilgængelig som prøveversion og er tilgængelig for integrerede abonnenter, der kan bruges i prøve versions perioden. Du kan stadig oprette den oprindelige version af den Power BI Embedded ressource, kaldet den *integrerede gen 1*, eller oprette en ny *integreret gen 2* -ressource. I prøveperioden kan du køre begge typer Power BI Embedded kapaciteter parallelt og tildele et arbejdsområde til enten en Gen1 eller en Gen2-kapacitet ".

Alle Power BI Embedded gen 1-funktioner, f. eks. midlertidig afbrydelse og fortsættelse af kapaciteten, bevares i gen 2. Derudover indeholder den 2 kapacitets ressource følgende opdateringer og forbedret funktionalitet:

* **Forbedret ydeevne** – bedre ydeevne i enhver kapacitets størrelse og når som helst. Handlinger udføres altid med den højeste hastighed og kører ikke langsommere, når belastningen af kapaciteten nærmer sig kapacitetsgrænserne.

* **Større skalering** – herunder følgende forbedringer:

    * *Der er ingen grænser for opdaterings samtidighed* – du behøver ikke længere at spore tidsplaner for datasæt, der opdateres på din kapacitet

    * *Færre hukommelsesbegrænsninger*

    * *Komplet adskillelse mellem rapportinteraktion og planlagte opdateringer*

* **Lavere posteringsniveau for sideinddelte rapporter og AI-arbejdsbelastninger** – starter med en SKU på *a1* og vokser, efterhånden som du har brug for det.

* At skalere **en ressource** med det samme – Skaler straks din Power bi Embedded ressource. Du kan skalere en Gen1-ressource på få minutter for at skalere en Gen2 ressource på få sekunder.

* **Skalering uden nedetid** – med integreret Gen2 kan du skalere din Power bi Embedded ressource, uden at du oplever nedetid.

* **Forbedrede målepunkter** – herunder klar og normaliseret kapacitets udnyttelses data, afhængigt af hvad der er kompleksiteten ved analysen, der udføres i kapaciteten. Metrikker påvirkes ikke af andre faktorer, f. eks. kapacitetens størrelse og belastningsniveauet på systemet, mens der udføres analyser. Når du bruger de forbedrede målepunkter, kan du tydeligt se det indbyggede rapporteringsværktøj:
    * Analyse af udnyttelse
    * Budget planlægning
    * Tilbageførsler
    * Behovet for at opgradere din kapacitet

    >[!NOTE]
    >Forbedrede metrikværdier bliver tilgængelige senere i prøveperioden. Kunder, der ønsker at få adgang til udnyttelses målinger i de seneste syv dage, kan gøre dette ved at kontakte kundesupport.

## <a name="using-embedded-gen2"></a>Brug af integrerede Gen2

Opret en integreret Gen2-kapacitets ressource for at drage fordel af dens opdateringer. Hvis du vil oprette en integreret Gen2 kapacitets ressource, skal du følge vejledningen i [opret Power bi Embedded kapacitet i Azure-Portal](azure-pbie-create-capacity.md).

## <a name="known-limitations"></a>Kendte begrænsninger

* Integreret Gen2 kapacitetsudnyttelse kan ikke spores i [appen Metrics](../../admin/service-admin-premium-monitor-capacity.md). Du kan finde flere oplysninger under [opdateringer til Premium Gen2 Monitor](../../admin/service-premium-what-is.md#updates-for-premium-gen2-preview-2).

* Allokeringsindstillinger for hukommelse for bestemte arbejdsbelastninger gælder ikke for integrerede Gen2-kapaciteter. Du kan finde flere oplysninger under [forbedringer af Embedded gen 2-hukommelse](embedded-capacity.md#embedded-gen-2-memory-enhancements-preview)

* Hvis du bruger XMLA med Embedded Gen2, skal du sørge for, at du bruger de nyeste versioner af datamodellering og administrationsværktøjer.

* Analysis Services-funktioner i integrerede Gen2 understøttes kun i de nyeste klient biblioteker. Anslåede udgivelsesdatoer for afhængige værktøjer, der understøtter dette krav, er angivet med [kendte begrænsninger i Premium-Gen2](../../admin/service-premium-what-is.md#known-limitations-in-premium-gen2).

* Alle de aktuelle Azure Metrics og logfører diagnosticering til Power BI Embedded understøtter kun Gen1-kapaciteter.

## <a name="next-steps"></a>Næste trin

> [!div class="nextstepaction"]
> [Opret Power BI Embedded-kapacitet på Azure-portalen](azure-pbie-create-capacity.md)

> [!div class="nextstepaction"]
> [Kapacitet og SKU'er i Power BI Embedded-analyser](embedded-capacity.md)

> [!div class="nextstepaction"]
> [Hvad er Power BI Premium?](../../admin/service-premium-what-is.md)

> [!div class="nextstepaction"]
>[Integrer indhold for dine kunder](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Integrer til din organisation](embed-sample-for-your-organization.md)