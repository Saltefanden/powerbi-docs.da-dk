---
title: Vejledning til brug af afbildning for sideinddelte rapporter
description: Vejledning til brug af billeder for sideinddelte Power BI-rapporter.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/16/2020
ms.openlocfilehash: f83894561f8592d5e679a08773459f14a9d6fa1c
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087746"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Vejledning til brug af afbildning for sideinddelte rapporter

Denne artikel henvender sig til rapportforfattere, der designer [sideinddelte rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md) i Power BI. Den indeholder forslag, du kan bruge, hvis du arbejder med afbildning. Normalt kan billeder i rapportlayouts vise grafik som et virksomhedslogo eller billeder.

Billeder kan gemmes på tre forskellige placeringer:

- I rapporten (integreret)
- På en webserver
- I en database, som kan hentes af et datasæt

De kan derefter bruges i en række forskellige scenarier i dine rapportlayouts:

- Et fritstående logo eller billede
- Billeder, der er knyttet til datarækker
- Baggrund for visse rapportelementer:
  - Rapportens brødtekst
  - Tekstfelt
  - Rektangel
  - Tablixdataområde (tabel, matrix eller liste)

## <a name="suggestions"></a>Forslag

Overvej følgende forslag til professionelle rapportlayouts, nemmere vedligeholdelse og optimeret rapportydeevne:

- **Brug den mindst mulige størrelse**: Vi anbefaler, at du forbereder billeder, der er små, men stadig er skarpe. Det handler om, at der er balance mellem kvalitet og størrelse. Overvej at bruge en grafikeditor (f. eks. MS Paint) til at reducere billedfilens størrelse.
- **Undgå integrerede billeder**: For det første kan integrerede billeder øge rapportfilens størrelse, hvilket kan medføre en langsommere rapportgengivelse. For det andet kan integrerede billeder hurtigt blive et vedligeholdelsesmareridt, hvis du skal opdatere mange rapportbilleder (hvilket kan være tilfældet, hvis dit firmalogo ændres).
- **Brug et webserverlager**: Det er en god mulighed at gemme billeder på en webserver, især for virksomhedens logo, som kan hentes på virksomhedens websted. Vær dog opmærksom, hvis dine rapportbrugere opretter adgang til rapporter uden for dit netværk. I dette tilfælde skal du kontrollere, at billederne er tilgængelige via internettet.

    Når billeder relaterer til dine data (f. eks. billeder af sælgerne), kan du navngive billedfiler, så et rapportudtryk kan oprette billedets URL-sti dynamisk. Du kan f. eks. navngive billeder af sælgere ved hjælp af de enkelte sælgeres medarbejdernummer. Hvis rapportdatasættet henter medarbejdernummeret, kan du skrive et udtryk for at oprette den fulde billed-URL-sti.
- **Brug et databaselager**: Når en relationsdatabase gemmer billeddata, giver det mening at hente billeddataene direkte fra databasetabellerne – især når billederne ikke er for store.
- **Relevante baggrundsbilleder**: Hvis du beslutter at bruge baggrundsbilleder, skal du være forsigtig med ikke at distrahere rapportbrugeren og fjerne opmærksomheden fra dine rapportdata. 

    Sørg også for at bruge _billeder med vandmærke_. Normalt har billeder med vandmærke en gennemsigtig baggrund (eller har den samme baggrundsfarve, der bruges i rapporten). De kan også have en svag farve. Almindelige eksempler på billeder med vandmærke omfatter virksomhedens logo eller følsomhedsmærkater som "Kladde" eller "Fortrolig".

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Hvad er sideinddelte rapporter i Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
