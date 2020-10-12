---
title: Foretag fejlfinding af underrapporter i sideinddelte rapporter i Power BI
description: Få mere at vide om løsninger på almindelige problemer, når du bruger underrapporter, som er rapportelementer i en sideinddelt rapport.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: troubleshooting
ms.date: 04/29/2020
ms.openlocfilehash: 6a0e90036b759c409a9f5b3e994571c2a0eb510c
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747499"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Foretag fejlfinding af underrapporter i sideinddelte rapporter i Power BI

Nogle gange kan du få et uventet resultat, når du bruger underrapporter i sideinddelte rapporter, eller funktionen fungerer ikke som forventet. Denne artikel indeholder løsninger på almindelige problemer, når der bruges underrapporter. En *underrapport* er et rapportelement, der viser en anden rapport i den primære del af en sideinddelt hovedrapport. Du kan finde flere oplysninger i [Underrapporter i sideinddelte rapporter i Power BI](subreports.md).

## <a name="subreport-couldnt-be-found"></a>Der blev ikke fundet nogen underrapport

**Beskrivelse:** Underrapporten gengives ikke. Der vises i stedet en fejlmeddelelse.

### <a name="message"></a>Meddelelse

"Underrapporten 'Underrapport1' blev ikke fundet på den angivne placering 'Kundeoplysninger'. Bekræft, at underrapporten er blevet publiceret, og at navnet er korrekt."

### <a name="possible-reasons"></a>Mulige årsager

- En underrapport med det angivne navn findes ikke i det samme arbejdsområde eller i den samme app som hovedrapporten.
- Brugeren har ikke adgang til underrapporten.
- Antallet af underrapporter i hovedrapporten har nået grænsen for underrapporter (50 underrapporter).

### <a name="troubleshooting-steps"></a>Fejlfindingstrin

**I et arbejdsområde**

- Bekræft, at rapporten med navnet i fejlmeddelelsen findes. Der skelnes mellem store og små bogstaver i navnet.

**I en app**

- Bekræft, at rapporten med navnet i fejlmeddelelsen findes i appen. Kontakt forfatteren af appen for at få yderligere hjælp.

**Hvis rapporten deles**

1. Bekræft, at rapporten med navnet i fejlmeddelelsen er delt med dig.
2. Hvis rapporten findes, skal du bekræfte, at navnet på ejeren er det samme for hovedrapporten som for underrapporten. Kontakt derefter ejeren af hovedrapporten med de pågældende oplysninger.

## <a name="subreport-renders-with-unexpected-content"></a>Underrapporten gengives med uventet indhold

### <a name="possible-reason"></a>Mulig årsag

Power BI tillader, at brugerne har flere rapporter med det samme navn i det samme arbejdsområde

### <a name="troubleshooting-steps-for-report-authors"></a>Fejlfindingstrin (for rapportforfattere)

1. Åbn hovedrapporten i Power BI Report Builder, og fastlæg navnet på underrapporten.
2. Kig efter rapporter med det samme navn i arbejdsområdet.
3. Find den forventede rapport, og omdøb resten.

**For andre end forfattere:** Kontakt forfatteren.

## <a name="data-retrieval-fails"></a>Datahentning mislykkes

**Beskrivelse:** Datahentning mislykkes under gengivelse af underrapporten. Underrapporten gengives ikke. Der vises i stedet en fejlmeddelelse.

### <a name="message"></a>Meddelelse

"Datahentning mislykkedes for underrapporten 'Underrapport1', der findes her: 'Faktureringsoplysninger'. Find flere oplysninger i logfilerne."

### <a name="troubleshooting-steps"></a>Fejlfindingstrin

De samme som de generelle fejlfindingstrin for rapporter med problemer med adgang til data.

## <a name="rendering-fails-unspecified-parameters"></a>Gengivelse mislykkes: Uspecificerede parametre

**Beskrivelse:** Gengivelse af rapporten mislykkes pga. uspecificerede parametre. Underrapporten har obligatoriske parametre, men hovedrapporten angiver ikke dem alle.

### <a name="message"></a>Meddelelse 
"En eller flere parametre blev ikke angivet for underrapporten 'Underrapport1', der findes her: 'UnderraportAmedDS'."

### <a name="troubleshooting-steps-for-the-report-author"></a>Fejlfindingstrin (for rapportforfatterne)

1. Åbn hovedrapporten i Power BI Report Builder.
2. Åbn underrapporten i Power BI Report Builder.
3. Bekræft, at det sæt af parametre, der overføres i rapportelementet for underrapporten i hovedrapporten, stemmer overens med sættet af parametre i underrapporten.

**For andre end forfattere:** Kontakt forfatteren.

## <a name="rendering-fails-recursion-limit"></a>Gengivelse mislykkes: Grænse for rekursion

**Beskrivelse:** Gengivelse af underrapporten mislykkes pga. grænsen for rekursion. Underrapporter kan ikke indlejres dybere end 20 niveauer.

### <a name="message"></a>Meddelelse

"Rapporten eller underrapporten indeholder den rekursive underrapport 'Underrapport1', som overskred den maksimalt tilladte grænse for rekursion."

### <a name="troubleshooting-steps-for-report-authors"></a>Fejlfindingstrin (for rapportforfattere)

- Reducer indlejring.
- Redesign rapportstrukturen.

## <a name="other-errors"></a>Andre fejl

**Beskrivelse:** Fejl, der ikke hører under nogen af de tidligere kategorier.

### <a name="message"></a>Meddelelse

"Fejl: Underrapporten kunne ikke vises."

### <a name="possible-reasons"></a>Mulige årsager

- Flere fejl under gengivelse af underrapporten, f.eks. uoverensstemmelse mellem parametre med problemer med datahentning.
- Uventede fejl.

### <a name="troubleshooting-steps-for-report-authors"></a>Fejlfindingstrin (for rapportforfattere)

1. Bekræft, at underrapporten kan gengives direkte.
2. Hvis underrapporten kan gengives, skal du kontrollere parametrene i både underrapporten og hovedrapporten.
3. Sørg for, at der ikke er mere end 50 unikke underrapporter for hovedrapporten, og at underrapporten ikke er indlejret dybere end 20 niveauer.
4. Hvis du ikke kan løse problemet, skal du kontakte Power BI-support.

**For andre end forfattere:** Kontakt forfatteren.

## <a name="next-steps"></a>Næste trin

[Underrapporter i sideinddelte rapporter i Power BI](subreports.md)

[Publicer en sideinddelt rapport i Power BI-tjenesten](../consumer/paginated-reports-view-power-bi-service.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
