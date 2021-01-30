---
title: Vejledning til sammensatte modeller i Power BI Desktop
description: Vejledning til udvikling af sammensatte modeller.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/24/2019
ms.openlocfilehash: 5a88e22450b5ae9b8000f3c321d87a2349a9f960
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088597"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Vejledning til sammensatte modeller i Power BI Desktop

Denne artikel henvender sig til designere af sammensatte modeller i Power BI Desktop. Den indeholder en beskrivelse af brugseksempler for sammensatte modeller og giver dig designvejledning. Vejledningen hjælper dig især med at finde ud af, om en sammensat model passer til din løsning. Hvis det er tilfældet, kan denne artikel også hjælpe dig med at designe en optimal model.

> [!NOTE]
> Artiklen omfatter ikke en introduktion til sammensatte modeller. Hvis du ikke er helt bekendt med sammensatte modeller, anbefaler vi, at du først læser artiklen [Brug sammensatte modeller i Power BI Desktop](../transform-model/desktop-composite-models.md).
>
> Da sammensatte modeller består af mindst én DirectQuery-kilde, er det også vigtigt, at du har en grundig forståelse af [modelrelationer](../transform-model/desktop-relationships-understand.md), [DirectQuery-modeller](../connect-data/desktop-directquery-about.md)og [vejledning til design af DirectQuery-modeller](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Brugseksempler for sammensatte modeller

Når det er muligt, er det bedst at udvikle en model i importtilstand. Denne tilstand giver den største fleksibilitet i design og den bedste ydeevne.

Men udfordringer, der er relateret til store datamængder, eller rapportering om data næsten i realtid, kan ikke løses ved at importere modeller. I begge tilfælde kan du overveje en DirectQuery-model, så dine data gemmes i en enkelt datakilde, der [understøttes af DirectQuery-tilstand](../connect-data/power-bi-data-sources.md).

Du kan også overveje at udvikle en sammensat model i følgende situationer.

- Din model kan være en DirectQuery-model, men du vil øge ydeevnen. I en sammensat model kan du forbedre ydeevnen ved at konfigurere et passende lager for hver tabel. Du kan også tilføje [sammenlægninger](../transform-model/desktop-aggregations.md). Begge disse optimeringer gennemgås senere i denne artikel.
- Du vil kombinere en DirectQuery-model med flere data, som skal importeres i modellen. Importerede data kan indlæses fra en anden datakilde eller fra beregnede tabeller.
- Du vil kombinere to eller flere DirectQuery-datakilder i en enkelt model.

> [!NOTE]
> I sammensatte modeller kan Direkte forbindelse-kilder eller DirectQuery-analysedatabasekilder ikke kombineres. Direkte forbindelse-kilder omfatter [eksternt hostede modeller](../connect-data/service-datasets-understand.md#external-hosted-models) og Power BI-datasæt. DirectQuery-analysedatabase kilder omfatter SAP Business Warehouse og SAP HANA.

## <a name="optimize-model-design"></a>Optimer modeldesignet

Du kan optimere en sammensat model ved at konfigurere tabel[lagringstilstande](../transform-model/desktop-storage-mode.md) og ved at tilføje [akkumuleringer](../transform-model/desktop-aggregations.md).

### <a name="table-storage-mode"></a>Tabellagertilstand

I en sammensat model kan du konfigurere lagringstilstanden for hver tabel (undtagen beregnede tabeller):

- **DirectQuery**: Vi anbefaler, at du angiver denne tilstand for tabeller, der repræsenterer store datamængder eller skal levere resultater i næsten realtid. Der importeres aldrig data i disse tabeller. Disse tabeller er som regel være faktatypetabeller – tabeller, der bruges til opsummering.
- **Import**: Vi anbefaler, at du angiver denne tilstand for dimensionstypetabeller – tabeller, der bruges til filtrering og gruppering. Det er faktisk den eneste mulighed for tabeller, der er baseret på kilder, som ikke understøttes af DirectQuery-tilstand. Beregnede tabeller importerer altid tabeller.
- **Dual**: Vi anbefaler, at du angiver denne tilstand for dimensionstypetabeller, når der er en mulighed for, at de forespørges sammen med DirectQuery-faktatypetabeller fra den samme kilde.

Der er flere mulige scenarier, når Power BI forespørger en sammensat model:

- **Kun import- eller Dual-tabel(ler) forespørges**: Alle data hentes fra modelcachen. Der leveres den hurtigst mulige ydeevne. Dette scenarie er almindeligt for dimensionstypetabeller, der forespørges efter filtre eller udsnitsværktøjvisuals.
- **Dual-tabel(ler) eller DirectQuery-tabel (r) fra den samme kilde forespørges**: Alle data hentes, ved at der sendes en eller flere oprindelige forespørgsler til DirectQuery-kilden. Der leveres den hurtigst mulige ydeevne, især når der findes relevante indekser i kildetabellerne. Dette scenarie er almindeligt for forespørgsler, der relaterer Dual-dimensionstypetabeller og DirectQuery-faktatypetabeller. Disse forespørgsler finder sted _internt i kildegruppen_, hvorfor alle en til en- eller en til mange-relationer evalueres som [almindelige relationer](../transform-model/desktop-relationships-understand.md#regular-relationships).
- **Alle andre forespørgsler**: Disse forespørgsler omfatter relationer på tværs af kildegrupper. Det skyldes enten, at en import tabel relaterer til en DirectQuery-tabel, eller at en Dual-tabel relaterer til en DirectQuery-tabel fra en anden kilde – i det tilfælde fungerer den som en importtabel. Alle relationer evalueres som [begrænsede relationer](../transform-model/desktop-relationships-understand.md#limited-relationships). Det betyder også, at grupperinger, der anvendes på ikke-DirectQuery-tabeller, skal sendes til DirectQuery-kilden som en virtuel tabel. I dette tilfælde kan den oprindelige forespørgsel være ineffektiv, især for store grupperingssæt. Der er også en risiko for, at følsomme data vises i den oprindelige forespørgsel.

Kort sagt anbefaler vi, at du:

- Overvejer nøje, om en sammensat model er den rette løsning – mens den muliggør integration af forskellige kilder på model niveau, introducerer den også designkompleksitet med mulige konsekvenser
- Indstil lagringstilstanden til **DirectQuery**, når en tabel er en faktatypetabel, der lagrer store datamængder eller skal levere resultater i næsten realtid
- Indstil lagringstilstanden til **Dual**, når en tabel er en dimensionstypetabel og skal forespørges sammen med **DirectQuery**-faktatypetabeller, der er baseret på den samme kilde
- Konfigurer passende opdateringsfrekvenser for at holde modelcachen for Dual-tabeller (og eventuelle afhængige beregnede tabeller) synkroniseret med kildedatabasen/-databaserne
- Tilstræb dataintegritet på tværs af datakilder (herunder modelcachen) – begrænsede relationer fjerner rækker, når relaterede kolonneværdier ikke stemmer overens
- Optimer DirectQuery-datakilder med de rette indekser for at opnå effektive joinforbindelser samt effektiv filtrering og gruppering
- Indlæs ikke følsomme data i import- eller Dual-tabeller, hvis der er risiko for, at der opfanges en oprindelig forespørgsel – du kan finde flere oplysninger under [Brug sammensatte modeller i Power BI Desktop (sikkerhedsmæssige konsekvenser)](../transform-model/desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>Aggregeringer

Du kan føje sammenlægninger til DirectQuery-tabeller i din sammensatte model. Sammenlægninger cachelagres i modellen, og de opfører sig derfor som importtabeller (selvom de ikke kan bruges som modeltabeller). Deres formål er at forbedre ydeevnen for mere detaljerede forespørgsler. Du kan finde flere oplysninger i [Sammenlægninger i Power BI Desktop](../transform-model/desktop-aggregations.md).

Vi anbefaler, at en sammenlægningstabel følger en grundlæggende regel: Rækkeantallet skal være mindst 10 gange mindre end den underliggende tabel. Hvis den underliggende tabel f.eks. omfatter 1 milliard rækker, må sammenlægningstabellen ikke omfatte mere end 100 millioner rækker. Denne regel sikrer, at der er en tilstrækkelig ydeevne set i forhold til omkostningerne ved at oprette og vedligeholde sammenlægningstabellen.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Brug sammensatte modeller i Power BI Desktop](../transform-model/desktop-composite-models.md)
- [Modelrelationer i Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [DirectQuery-modeller i Power BI Desktop](../connect-data/desktop-directquery-about.md)
- [Brug DirectQuery i Power BI Desktop](../connect-data/desktop-use-directquery.md)
- [Fejlfinding af DirectQuery-model i Power BI Desktop](../connect-data/desktop-directquery-troubleshoot.md)
- [Power BI-datakilder](../connect-data/power-bi-data-sources.md)
- [Lagringstilstand i Power BI Desktop](../transform-model/desktop-storage-mode.md)
- [Sammenlægninger i Power BI Desktop](../transform-model/desktop-aggregations.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)
