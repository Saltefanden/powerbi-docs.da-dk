---
title: Versionering af datamodel i Power BI
description: Datamodel, der eksponeres af en OData-tjeneste
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: d8ab94bd33aa2f0674f6dc45a93da0d2f42b1647
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91749293"
---
# <a name="data-model-versioning"></a>Versionering af datamodel

Den datamodel, der eksponeres af en OData-tjeneste, f.eks Power BI-datamodellen, definerer en kontrakt mellem OData-tjenesten og dens klienter. Tjenester har tilladelse til at udvide deres model, men kun i en sådan grad, at det ikke ødelægger eksisterende klienter. Ødelæggelse af ændringer, f.eks. ved at fjerne egenskaber eller ændre typen af eksisterende egenskaber, kræver, at en ny tjenesteversion leveres i en anden tjenesterod-URL-adresse for den nye model.  
  
Følgende datamodeltilføjelser betragtes som sikre og kræver ikke, at tjenester versionerer deres indgangspunkt.  
  
* Tilføjelse af en egenskab, der kan være null, eller som har en standardværdi: Hvis den har samme navn som en eksisterende dynamisk egenskab, skal den have den samme type (eller basistype) som den eksisterende dynamiske egenskab  
* Tilføjelse af en navigationsegenskab, der kan være null eller samlervurderet: Hvis den har samme navn som en eksisterende navigationsegenskab, skal den have den samme type (eller basistype) som den eksisterende dynamiske navigationsegenskab  
* Tilføjelse af en ny enhedstype til modellen  
* Tilføjelse af en ny kompleks type til modellen  
* Tilføjelse af et nyt objektsæt  
* Tilføjelse af en ny singleton  
* Tilføjelse af en handling, en funktion, en handlingsimport eller en funktionsimport
* Tilføjelse af en handlingsparameter, der kan være null  
* Tilføjelse af en typedefinition eller optælling  
* Tilføjelse af en hvilken som helst anmærkning til et modelelement, der ikke behøver at være forståeligt for klienten for at interagere med tjenesten korrekt  
  
Klienter ***SKAL*** være forberedt på, at tjenester foretager sådanne trinvise ændringer af deres model. Klienter skal især være forberedt på at modtage egenskaber og afledte typer, der ikke tidligere er blevet defineret af tjenesten.  
  
Tjenester ***MÅ IKKE*** ændre deres datamodel, afhængigt af den godkendte bruger. Hvis datamodellen er afhængig af bruger eller brugergruppe, SKAL alle ændringer være sikre ændringer, jf. dette afsnit, når den fulde model sammenlignes med den model, der er synlig for brugere med begrænsede godkendelser.  
  
Du kan få flere oplysninger om standarder for OData-datamodeller i [OData Version 4.0 Part 1: Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).  
  
## <a name="see-also"></a>Se også
[Oversigt over Power BI REST-API](/rest/api/power-bi/)