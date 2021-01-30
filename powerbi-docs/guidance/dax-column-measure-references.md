---
title: 'DAX: Referencer til kolonner og målinger'
description: Vejledning i, hvordan du refererer til kolonner i målinger i dine DAX-udtryk.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/18/2019
ms.openlocfilehash: 3d9f4ea374783b90705a8ec5644d67ddc5d1168b
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088528"
---
# <a name="dax-column-and-measure-references"></a>DAX: Referencer til kolonner og målinger

Som datamodel refererer dine DAX-udtryk til modelkolonner og -målinger. Kolonner og målinger er altid knyttet til modeltabeller, men disse tilknytninger er forskellige. Der er derfor forskellige anbefalinger til, hvordan du refererer til dem i dine udtryk.

## <a name="columns"></a>Kolonner

En kolonne er et objekt på tabelniveau, og kolonnenavne skal være entydige i en tabel. Det er derfor muligt, at det samme kolonnenavn bruges flere gange i din model – forudsat at de tilhører forskellige tabeller. Der er én regel mere: en kolonne må ikke have det samme navn som et målingsnavn eller et hierarkinavn, der findes i den samme tabel.

DAX gennemtvinger generelt ikke brugen af en _fuldt kvalificeret_ reference til en kolonne. En fuldt kvalificeret reference betyder, at tabelnavnet står foran kolonnenavnet.

Her er et eksempel på en beregnet kolonnedefinition, der kun bruger referencer til kolonnenavne. Kolonnerne **Sales** og **Cost** tilhører begge tabellen **Orders**.

```dax
Profit = [Sales] - [Cost]
```

Den samme definition kan omskrives med fuldt kvalificerede kolonnereferencer.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Nogle gange er du nødt til at bruge fuldt kvalificerede kolonnereferencer, når Power BI registrerer flertydighed. Når du angiver en formel, bliver du advaret via en rød bølgelinje og en fejlmeddelelse. Desuden kræver nogle DAX-funktioner, for eksempel DAX-funktionen [LOOKUPVALUE](/dax/lookupvalue-function-dax), at du bruger fuldt kvalificerede kolonner.

Det anbefales, at du altid kvalificerer dine kolonnereferencer fuldt ud. Årsagerne er angivet i afsnittet [Anbefalinger](#recommendations).

## <a name="measures"></a>Målinger

En måling er et objekt på modelniveau. Derfor skal målingsnavne være entydige inden for modellen. Men i ruden **Felter** kan rapportforfattere se de målinger, der er knyttet til en enkelt modeltabel. Denne tilknytning er angivet af kosmetiske årsager, og du kan konfigurere den ved at angive egenskaben **Hjemmetabel** for målingen. Du kan finde flere oplysninger under [Målinger i Power BI Desktop (organisering af målinger)](../transform-model/desktop-measures.md#organizing-your-measures).

Det er muligt at bruge en fuldt kvalificeret måling i udtryk. DAX IntelliSense foreslår det endda. Det er dog ikke nødvendigt, og det er ikke en anbefalet praksis. Hvis du ændrer hjemmetabellen for en måling, brydes alle udtryk, der bruger en fuldt kvalificeret målingsreference til den. Du er derefter nødt til at redigere alle brudte formler for at fjerne (eller opdatere) målingsreferencen.

Det anbefales, at du aldrig kvalificerer målingsreferencer. Årsagerne er angivet i afsnittet [Anbefalinger](#recommendations).

## <a name="recommendations"></a>Anbefalinger

Vores anbefalinger er nemme og lette at huske:

- Brug altid fuldt kvalificerede kolonnereferencer
- Brug altid fuldt kvalificerede målingsreferencer

Årsag:

- **Formelindtastning**: Udtryk accepteres, da der ikke er nogen flertydige referencer at løse. Desuden opfylder du kravet til de DAX-funktioner, der kræver fuldt kvalificerede kolonnereferencer.
- **Robusthed**: Udtryk fungerer fortsat, selvom du ændrer egenskaben Hjemmetabel for en måling.
- **Læsbarhed**: Udtryk er hurtige og nemme at forstå – du kan hurtigt finde ud af, om det er en kolonne eller en måling ud fra, om den er fuldt kvalificeret eller ej.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Henvisning til DAX (Data Analysis Expressions)](/dax/)
- Læringsforløb: [Brug DAX i Power BI Desktop](/learn/paths/dax-power-bi/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)