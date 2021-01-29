---
title: Kontrol af certifikat tilbagekaldelse i Power BI Desktop
description: Hvordan du tilbagekalder certifikater i Power BI Desktop i BRUGERGRÆNSEFLADEN og i registreringsdatabasen
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 01/25/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 482f0f8279de9818b631ff79e7b37a215e7397bd
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2021
ms.locfileid: "99056997"
---
# <a name="certificate-revocation-in-power-bi-desktop"></a>Tilbagekaldte certifikater i Power BI Desktop

Power BI giver mulighed for at aktivere eller deaktivere certifikatkontrol på to måder. I november 2020 introducerede vi et enkelt Kontrolprogram til tilbagekaldelse af certifikater til/fra for Webforbindelse i Power BI Desktop. Nu kan du få mere detaljeret kontrol over kontrol af certifikat tilbagekaldelseskontrol.

## <a name="simple-certificate-revocation"></a>Enkel tilbagekaldelse af certifikater

I brugergrænsefladen i Power BI Desktop kan du aktivere eller deaktivere funktionen.

- I menuen **File** > **Indstillinger og indstillinger**  >  skal du vælge **sikkerhed** og derefter vælge eller fjern markeringen af **Aktiver kontrol af certifikat tilbagekald**.

## <a name="more-fine-grained-control"></a>Mere detaljeret kontrol

Du kan få mere detaljeret kontrol over kontrol af certifikat tilbagekaldelseskontrol med en tredje mulighed. 

- **Basic**  Den grundlæggende kontrol accepterer certifikater, hvis tilbagekaldsstatus er ukendt, f. eks. fordi certifikatet ikke angiver det. Denne kontrol er vigtigt for organisationer, der bruger firma proxyservere. Det er det samme som at markere afkrydsningsfeltet i Power BI Desktop.
- **Deaktiveret** Det samme som deaktivering af afkrydsningsfeltet i Power BI Desktop.
- **Omfattende** Du kan deaktivere eller aktivere kontrolelementet tilbagekald i *omfattende* tilstand, som ikke accepterer certifikater med ukendte status for tilbagekald. 


|Status for oplysninger om certifikat tilbagekaldelse | Omfattende kontrol | Grundlæggende kontrol | Ingen |
|---------|---------|---------|---------|
|Tilbagekaldt     |  ❌  | ❌  | ✔   |
|Ukendt  |  ❌    |  ✔   |    ✔  |
|Ikke tilbagekaldt  | ✔  |    ✔ |    ✔  |

Afkrydsningsfeltet simple enable eller disable findes stadig i Power BI Desktop brugergrænseflade. Hvis du vil bruge det mere detaljerede kontrolelement, skal du angive følgende DWORD-værdi i registreringsdatabasen: `DisableCertificateRevocationCheck` . Du kan angive denne værdi i registreringsdatabasenøglen Power BI Desktop. Det er en af disse, afhængigt af dit operativsystem:

```
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Microsoft Power BI Desktop
```

,

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop
```

Indstil værdien Registry til en af følgende værdier: 

|Værdi  |Tilstand  |Konfiguration  |
|---------|---------|---------|
|0     | Grundlæggende   | Der accepteres certifikater med en ukendt tilbagekaldelsesstatus. Det svarer til at aktivere afkrydsningsfeltet i Power BI Desktop. |
|1     | Deaktiveret  | Ignorerer alle tilbagekalds kontroller. Svarer til at deaktivere afkrydsningsfeltet i Power BI Desktop.  |
|2     | Udtømme  |  Kræver, at der ikke tilbagekaldes certifikater. Accepterer ikke certifikater med Ukendt tilbagekaldsstatus |

Konfigurer denne registreringsdatabaseindstilling, så du kan drage fordel af mere detaljeret kontrol i dag.