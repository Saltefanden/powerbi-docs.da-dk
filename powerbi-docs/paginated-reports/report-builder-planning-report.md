---
title: Planlægning af en rapport i Power BI Report Builder
description: Med Power BI Report Builder kan du oprette mange slags sideinddelte rapporter. Hvis du vil oprette en nyttig rapport, der er let at forstå, er det en god idé at planlægge den først.
author: maggiesMSFT
ms.author: maggies
ms.date: 07/25/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
ms.openlocfilehash: 2ed8dfd07cf5d7d04869b3bf2253bca09adbc0ba
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416226"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>Planlægning af en rapport i Power BI Report Builder

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Med Power BI Report Builder kan du oprette mange slags sideinddelte rapporter. Du kan f.eks. oprette rapporter, der viser en oversigt over eller detaljerede salgsdata, marketing- og salgstendenser, driftsrapporter eller dashboards. Du kan også oprette rapporter, der drager fordel af formateret tekst, f.eks. til salgsordrer, produktkataloger eller standardbreve. Alle disse rapporter oprettes ved hjælp af forskellige kombinationer af de samme grundlæggende byggesten i Report Builder. Hvis du vil oprette en nyttig rapport, der er let at forstå, er det en god idé at planlægge den først. Her er nogle ting, det kan være en god idé at overveje, før du går i gang:  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>I hvilket format skal rapporten vises?
  
Du kan gengive rapporter online i en browser, f.eks. på Power BI-portalen, eller eksportere dem til andre formater, f.eks. PDF, Word eller Excel. Det er vigtigt at overveje den endelige udformning af din rapport, da alle funktioner ikke er tilgængelige i alle eksportformater. 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>I hvilken struktur vil du præsentere dataene?
  
Du kan vælge mellem tabel, matrix (svarer til en rapport med tværgående faner eller pivottabeller), diagram, formaliafrie strukturer eller en kombination af disse til at præsentere data. Du kan finde flere oplysninger i [Tabeller, matrixer og lister i Power BI Report Builder](report-builder-tables-matrices-lists.md).  
  
## <a name="how-do-you-want-your-report-to-look"></a>Hvordan skal din rapport se ud?
  
Report Builder indeholder en masse rapportelementer, som du kan føje til din rapport for at gøre den nemmere at læse, fremhæve vigtige oplysninger, hjælpe din målgruppe med at navigere i rapporten osv. Det spiller en vigtig rolle at vide, hvordan rapporten skal vises, da det afgør, om du har brug for rapportelementer såsom tekstfelter, billeder, rektangler og linjer. Det kan også være en idé at vise eller skjule elementer, tilføje et dokumentkort, inkludere rapporter med detaljeadgang eller underrapporter eller linke til andre rapporter.   
  
## <a name="should-the-data-be-filtered"></a>Skal dataene filtreres?
  
Du vil muligvis indsnævre omfanget af rapporten for bestemte brugere eller lokationer eller for en bestemt tidsperiode. Hvis du vil filtrere rapportdataene, skal du bruge parametre til at hente og kun vise de ønskede data. Du kan finde flere oplysninger i [Rapportparametre i Power BI Report Builder](paginated-reports-parameters.md).  
  
## <a name="do-you-need-to-create-calculations"></a>Har du brug at oprette beregninger? 
  
Nogle gange indeholder din datakilde og dine datasæt ikke de nøjagtige felter, du skal bruge til din rapport. I denne situation skal du muligvis oprette dine egne beregnede felter. Det kan f.eks. være, at du vil gange prisen pr. enhed med antallet for at få salgsbeløbet for en fakturalinje. Udtryk bruges også til at levere betinget formatering og andre avancerede funktioner. Du kan finde flere oplysninger i [Udtryk i Power BI Report Builder](report-builder-expressions.md).  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>Vil du skjule rapportelementer indledningsvist?
  
Overvej, om du vil skjule rapportelementer, herunder dataområder, grupper og kolonner, når rapporten køres første gang. Du kan f.eks. indledningsvist præsentere en oversigtstabel og derefter zoome ind på detaljeniveauet i de detaljerede data. 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>Hvordan vil du levere din rapport?  
  
Du kan gemme din rapport på din lokale computer og fortsætte med at arbejde på den eller køre den lokalt med dine egne oplysninger. Men hvis du vil dele rapporten med andre, skal du gemme den på Power BI. Hvis du gemmer den på Power BI, kan andre køre den, når de vil. Alternativt kan du konfigurere et abonnement og e-mail-levering af rapporten til andre personer. Du kan få rapporten leveret i et bestemt eksportformat, hvis du foretrækker det. 
  
## <a name="next-steps"></a>Næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
