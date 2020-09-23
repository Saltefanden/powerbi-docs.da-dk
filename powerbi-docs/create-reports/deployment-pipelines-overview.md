---
title: Oversigt over udrulningspipelines
description: Få mere at vide om udrulningspipelines i Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: contperfq1
ms.date: 09/15/2020
ms.openlocfilehash: 58d1adef9a9b2a8a4f818f94da2cb34e6529db83
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90855489"
---
# <a name="introduction-to-deployment-pipelines"></a>Introduktion til udrulningspipelines

I dagens verden er analyser en vigtig del af beslutningsprocessen i næsten alle organisationer. Den voksende brug af Power BI som analyseværktøj kræver, at der bruges flere data, at analyserne tager sig godt ud, og de er brugervenlige. Først og fremmest skal Power BI dog altid være tilgængelig og pålidelig. BI-udviklere skal kunne samarbejde effektivt for at imødekomme disse krav.

Værktøjet Udrulningspipelines giver BI-oprettere mulighed for at administrere organisationsindholds livscyklus. Værktøjet er effektivt og kan genbruges til oprettere i en virksomhed med Premium-kapacitet. Værktøjet gør det muligt for oprettere at udvikle og teste Power BI-indhold, før indholdet forbruges af brugerne. Indholdstyperne omfatter rapporter, dashboards og datasæt.

Værktøjet er designet som en pipeline med tre faser:

* **<a name="development"></a>Udvikling**
    
    Denne fase bruges til at designe, opbygge og overføre nyt indhold samme med andre udviklere. Dette er det første fase i udrulningspipelines.

* **<a name="test"></a>Test**

    Du er klar til at gå ind i testfasen, når du har foretaget alle ændringerne af dit indhold. Du uploader det ændrede indhold, så det kan flyttes til denne testfase. Her er tre eksempler på, hvilke opgaver der kan udføres i testmiljøet:

    * Del indhold med testere og reviewere

    * Indlæs og kør test med store datamængder

    * Test din app for at se, hvordan den vil se ud for slutbrugerne

* **<a name="production"></a>Produktion**

    Når du har testet indholdet, kan du bruge produktionsfasen til at dele den endelige version af dit indhold med virksomhedsbrugere på tværs af organisationen.

![Et skærmbillede af en udrulningspipeline med alle tre trin – udvikling, test og produktion – udfyldt.](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Kom i gang med udrulningspipelines](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Om processen for udrulningspipelines](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Fejlfinding af udrulningspipelines](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[Bedste fremgangsmåder for udrulningspipelines](deployment-pipelines-best-practices.md)
