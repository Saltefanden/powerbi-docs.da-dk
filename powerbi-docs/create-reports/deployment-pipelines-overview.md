---
title: Oversigt over udrulningspipelines
description: Få mere at vide om udrulningspipelines i Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: pbi-deployment
ms.custom: contperf-fy21q1
ms.date: 10/21/2020
ms.openlocfilehash: ba2aedd4d503d468ba47640dd29fcfe004825ba5
ms.sourcegitcommit: 7bf09116163afaae312eb2b232eb7967baee2c92
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/17/2020
ms.locfileid: "97621113"
---
# <a name="introduction-to-deployment-pipelines"></a>Introduktion til udrulningspipelines

I dagens verden er analyser en vigtig del af beslutningsprocessen i næsten alle organisationer. Den voksende brug af Power BI som analyseværktøj kræver, at der bruges flere data, at analyserne tager sig godt ud, og de er brugervenlige. Først og fremmest skal Power BI dog altid være tilgængelig og pålidelig. BI-udviklere skal kunne samarbejde effektivt for at imødekomme disse krav.

Værktøjet Udrulningspipelines giver BI-oprettere mulighed for at administrere organisationsindholds livscyklus. Det er et effektivt værktøj, der kan genbruges til oprettere i en virksomhed med Premium-kapacitet. Udrulningspipelines gør det muligt for oprettere at udvikle og teste Power BI-indhold, før indholdet forbruges af brugerne. Indholdstyperne omfatter rapporter, dashboards og datasæt.

Værktøjet er designet som en pipeline med tre faser:

* **<a name="development"></a>Udvikling**
    
    Denne fase bruges til at designe, opbygge og overføre nyt indhold samme med andre udviklere. Dette er det første fase i udrulningspipelines.

* **<a name="test"></a>Test**

    Du er klar til at gå ind i testfasen, når du har foretaget alle de nødvendige ændringer af dit indhold. Du uploader det ændrede indhold, så det kan flyttes til denne testfase. Her er tre eksempler på, hvilke opgaver der kan udføres i testmiljøet:

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
