---
title: Integreret analyse-selvstudium til at få klient hemmeligheden
description: Få kunde hemmelighed til de integrerede analyse vejledninger.
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 12/09/2020
ms.custom: include file
ms.openlocfilehash: 875243aa890b80d21a73b20dec291329d256ba21
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494604"
---
Følg disse trin for at hente klienthemmeligheden:

1. Log på [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Søg efter **Programregistreringer**, og vælg linket **Programregistreringer**.

3. Vælg det Azure AD-program, du bruger til at integrere dit Power BI-indhold.

4. Under **Administrer** skal du vælge **Certifikater og hemmeligheder**.

5. Under **Klienthemmeligheder** skal du vælge **Ny klienthemmelighed**.

6. I pop op-vinduet **Tilføj en klienthemmelighed** skal du angive en beskrivelse af din programhemmelighed, vælge, hvornår programhemmeligheden udløber, og vælge **Tilføj**.

7. I afsnittet **Klienthemmeligheder** skal du kopiere strengen i kolonnen **Værdi** i den nyoprettede programhemmelighed. Værdien for klienthemmeligheden er dit *klient-id*.