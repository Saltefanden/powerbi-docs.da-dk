---
title: Overblik over tjenesteprincipal
description: Overblik over tjenesteprincipal
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 6086185fb671b9f418ef2ec070b762020fbe8f75
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/13/2020
ms.locfileid: "91989464"
---
Tjeneste principalen er en godkendelsesmetode, der kan bruges til at lade et Microsoft Azure AD-program få adgang indhold og API'er i Power BI-tjenesten.

Når du opretter en Azure Active Directory-app, oprettes der et [tjenesteprincipalobjekt](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). Tjenesteprincipalobjektet, der også blot kaldes *tjenesteprincipal*, gør det muligt for Microsoft Azure AD at godkende din app. Når appen er godkendt, kan den få adgang til Microsoft Azure AD-lejerressourcer.

For at kunne godkende skal tjenesteprincipalen bruge Microsoft Azure AD-appens *program-id* og et af følgende:

* Programhemmelighed
* Certifikat