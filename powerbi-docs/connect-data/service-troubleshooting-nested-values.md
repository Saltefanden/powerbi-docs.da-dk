---
title: Fejlfinding af indlejrede værdier, der returneres som tekst i Power BI-tjenesten
description: Få mere at vide om, hvordan du løser fejl med indlejrede værdier, der konverteres til en streng, når du bruger forkerte indstillinger for beskyttelse af personlige oplysninger for datakilden
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 6/4/2019
LocalizationGroup: Reports
ms.openlocfilehash: b34f6ae838122b0b2036a953296d5032bdfe76b8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96401368"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Fejlfinding af indlejrede værdier, der returneres som tekst i Power BI-tjenesten

## <a name="cause"></a>Årsag

Tidligere har der været tilfælde, hvor en rapport i Power BI opdateres fint i Desktop, men mislykkes i Power BI-tjenesten med en fejl såsom "Vi kan ikke konvertere værdien "[Tabel]" til typen Tabel". En af årsagerne til denne fejl er, at når Data Privacy Firewall gemmer en datakilde i en buffer, konverteres indlejrede værdier, der ikke er skalar (f.eks. tabeller, poster, lister og funktioner), automatisk til tekstværdier (såsom "[Tabel]" eller "[Post]").

Nu, hvor Power BI-tjenesten understøtter indstilling af niveauer for beskyttelse af personlige oplysninger (eller komplet deaktivering af Firewall), kan sådanne fejl undgås ved [at konfigurere indstillingerne for beskyttelse af personlige oplysninger for datakilden](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) i Power BI-tjenesten, så de ikke er private.

Fra og med juni vil følgende fejl blive produceret i Power BI, når Firewall gemmer en indlejret tabel/post/liste osv. i en buffer, i stedet for at konvertere sådanne værdier til tekst uovervåget: 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Effekt på indlæsning/opdatering

Selvom ændringen er motiveret af, at Firewall gemme i buffer, påvirker den også indlæsning/opdatering. For at kunne håndtere funktionsmåden med lagring i buffer i Firewall var det også nødvendigt at ændre funktionsmåden for indlæsning af indlejrede tabeller/poster osv. i Power BI-modellen og Excel-datamodellen i PQ til Excel. Før ville indlejrede tabeller/poster osv. blive indlæst som tekstværdier (f.eks. "[Tabel]" eller "[Post]"). De behandles nu som fejl, hvilket resulterer i en null-værdi i den indlæste tabel og en gradvis forøgelse af fejlantal i de indlæste resultater.

Da disse fejl kun opstår under indlæsning/opdatering, vises de ikke i Power-forespørgselseditor.

### <a name="before"></a>Før

- Indlæsning/opdatering uden fejl
- Den indlæste tabel indeholder "[Tabel]", "[Post]" osv.
 

### <a name="after"></a>Efter

- Indlæsning/opdatering med fejl
- Den indlæste tabel indeholder NULL-værdier (i stedet for "[Tabel]", "[Post]" osv.)
 

## <a name="resolution"></a>Løsning

Er du ved at indlæse en kolonne, der indeholder værdier, som ikke er skalar (f.eks. tabeller, lister, poster osv.)?
Hvis det er tilfældet, bør du kunne undgå fejlene ved at fjerne kolonnen.
Hvis du ikke kan fjerne kolonnen, bør du kunne replikere den tidligere funktionsmåde ved at tilføje en brugerdefineret kolonne og bruge logik som i følgende eksempel:

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

Genskabes fejlen i Power BI Desktop, hvis du angiver alle dine indstillinger for beskyttelse af personlige oplysninger for datakilden til Privat?
Hvis det er tilfældet, bør du kunne løse fejlen ved [at konfigurere indstillingerne for beskyttelse af personlige oplysninger for datakilden](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) i Power BI-tjenesten, så de ikke er private.
