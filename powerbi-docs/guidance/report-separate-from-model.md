---
title: Adskil rapporter fra modeller i Power BI Desktop
description: Vejledning til adskillelse af rapporter fra modeller i Power BI Desktop.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 04/11/2020
ms.openlocfilehash: a45299015883615b4773fe5db1c9864e01a47c4b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418346"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Adskil rapporter fra modeller i Power BI Desktop

Når du opretter en ny Power BI Desktop-løsning, er "hent data" en af de første opgaver, du skal udføre. Når du henter data, kan det ende med to meget forskellige resultater. Det kan være:

- At der oprettes en [direkte forbindelse](../connect-data/desktop-report-lifecycle-datasets.md) til en model, som allerede er udgivet, og som kan være et Power BI-datasæt eller en Analysis Services-model, der hostes eksternt.
- At udviklingen af en ny model startes, som enten kan være en importmodel, en DirectQuery-model eller en sammensat model.

Denne artikel omhandler det andet scenarie. Den indeholder vejledning til, om en rapport og en model bør kombineres i en enkelt Power BI Desktop-fil.

## <a name="single-file-solution"></a>Løsning med en enkelt fil

En _løsning med en enkelt fil_ fungerer godt, når der altid kun vil være en enkelt rapport baseret på modellen. I dette tilfælde er det sandsynligt, at det er den samme person, som har oprettet modellen og rapporten. Vi definerer det som en _Personal BI_-løsning, selvom rapporten kan deles med andre. Sådanne løsninger kan repræsentere rollebaserede rapporter eller engangsvurderinger af en forretningsudfordring – ofte beskrevet som _ad hoc_-rapporter.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="En enkelt fil indeholder en model og en rapport, der er udviklet af samme person." border="true":::

## <a name="separate-report-files"></a>Separate rapportfiler

Det giver mening at adskille model- og rapportudvikling i separate Power BI Desktop-filer, når:

- Datadesignere og rapportforfattere er forskellige personer.
- Det er forstået, at en model vil være kilden til flere rapporter, nu eller i fremtiden.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Der er tre PBIX-filer. Den første indeholder kun en model. De andre to indeholder kun rapporter, og de har direkte forbindelse til den model, der hostes i Power BI-tjenesten. Rapporterne er udviklet af forskellige personer." border="true":::

Datadesignere kan stadig bruge oplevelsen til rapportskrivning i Power BI Desktop til at teste og validere deres modeldesign. Men så snart de har udgivet deres fil i Power BI-tjenesten, bør de fjerne rapporten fra arbejdsområdet. Og de skal huske at fjerne rapporten, hver gang de genudgiver og overskriver datasættet.

### <a name="preserve-the-model-interface"></a>Bevar modelgrænsefladen

Nogle gange er modelændringer uundgåelige. Datadesignere skal derfor være forsigtige, så de ikke ødelægger modelgrænsefladen. Hvis de gør det, kan den medføre, at relaterede rapportvisualiseringer eller dashboardfelter ødelægges. Ødelagte visualiseringer vises som fejl, og de kan resultere i frustration for rapportforfattere og -forbrugere. Og værre endnu – de kan reducere tilliden til dataene.

Så administrer modelændringer med stor forsigtighed. Hvis det er muligt, skal du undgå følgende ændringer:

- Omdøbning af tabeller, kolonner, hierarkier, hierarkiniveauer eller målinger.
- Ændring af kolonnedatatyper.
- Ændring af målingsudtryk, så de returnerer en anden datatype.
- Flytning af målinger til en anden starttabel. Det skyldes, at flytning af en måling kan ødelægge målinger, der er baseret på rapporten, og som fuldt ud kvalificerer målinger med navnet på deres starttabel. Vi anbefaler ikke, at du skriver DAX-udtryk ved hjælp af fuldt kvalificerede målingsnavne. Du kan finde flere oplysninger under [DAX: Referencer til kolonner og målinger](dax-column-measure-references.md).

Du kan roligt tilføje nye tabeller, kolonner, hierarkier, hierarkiniveauer eller målinger med én undtagelse: Det er muligt, at et nyt målingsnavn kolliderer med et målingsnavn, der er baseret på rapporten. For at undgå kollisioner anbefaler vi, at rapportforfattere indfører en navngivningskonvention, når de definerer målinger i deres rapporter. De kan foranstille målingsnavne, der er baseret på rapporter, med et understregningstegn eller et andet tegn.

Hvis du har behov for at udføre ændringer, der vil resultere i afbrydelser, anbefaler vi, at du gør et af følgende:

- [Få vist relateret indhold for datasættet](../consumer/end-user-related.md) i Power BI-tjenesten.
- Udforsk visningen [Dataafstamning](../collaborate-share/service-data-lineage.md) i Power BI-tjenesten.

Begge muligheder gør dig i stand til hurtigt at identificere relaterede rapporter og dashboards. Visningen Dataafstamning er sandsynligvis det bedste valg, da det er nemt at se kontaktpersonen for hver relaterede artefakt. Det er faktisk et link, der åbner en mail, som er adresseret til kontakten.

Vi anbefaler, at du kontakter ejeren af hver relaterede artefakt for at give vedkommende besked om planlagte ændringer, der vil medføre afbrydelser. På denne måde er vedkommende forberedt og klar til at rette og genudgive sine rapporter, hvilket hjælper med at minimere nedetiden og frustration.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Opret forbindelse til datasæt i Power BI-tjenesten fra Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
- [Få vist relateret indhold i Power BI-tjenesten](../consumer/end-user-related.md)
- [Dataafstamning](../collaborate-share/service-data-lineage.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
