---
title: Oprettelsesapp for tjenesteprincipal
description: Oprettelsesapp for tjenesteprincipal
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 80886eab6de6c125d0361b326f5d31d2b3bb35e5
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524510"
---
1. Log på [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Søg efter **appregistreringer**, og klik på linket **Appregistreringer**.

    ![azure-appregistrering](media/embedded-service-principal/azure-app-registration.png)

3. Klik på **Ny registrering**.

    ![ny registrering](media/embedded-service-principal/new-registration.png)

4. Udfyld de påkrævede oplysninger:
    * **Navn** – Angiv et navn til programmet
    * **Understøttede kontotyper** – Vælg understøttede kontotyper
    * (Valgfrit) **URI til omdirigering** – Angiv en URI, hvis det er nødvendigt

5. Klik på **Registrer**.

6. Efter registrering er *program-id'et* tilgængeligt via fanen **Oversigt**. Kopiér og gem *program-id'et* til senere brug.

    ![Skærmbillede, der viser, hvor du kan få vist et program-id under fanen Oversigt.](media/embedded-service-principal/application-id.png)