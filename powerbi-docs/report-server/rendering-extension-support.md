---
title: Overensstemmelse med ISO 14289-1 for udvidelsen til PDF-gengivelse – Power BI-rapportserver og SSRS
description: I dette dokument beskrives overensstemmelse med specifikationerne i ISO 14289-1 (PDF/UA) for udvidelsen til PDF-gengivelse til Power BI-rapportserver og SQL Server Reporting Services.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.openlocfilehash: eb2e3e599afad20401bfba0563041f8a7e442041
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418296"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server--ssrs"></a>Overensstemmelse med ISO 14289-1 for udvidelsen til PDF-gengivelse – Power BI-rapportserver og SSRS

Gælder for: Microsoft Power BI-rapportserver og SQL Server Reporting Services (SSRS)

I dette dokument beskrives overensstemmelse med specifikationerne i [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/) for udvidelsen til PDF-gengivelse til Power BI-rapportserver og SQL Server Reporting Services.

> [!NOTE]
> Du kan gemme eller udskrive denne whitepaper ved at vælge **Udskriv** i din browser og derefter vælge **Gem som PDF**.

## <a name="1--scope"></a>1.  Område

Ikke tilgængelig

## <a name="2--normative-references"></a>2.  Normreferencer

Ikke tilgængelig

## <a name="3--terms-and-definitions"></a>3.  Begreber og definitioner

Ikke tilgængelig

## <a name="4--notation"></a>4.  Notation

Ikke tilgængelig

## <a name="5-version-identification"></a>5. Versionsidentifikation

PDF-gengivelsesudvidelsen giver understøttelse af PDF/UA som beskrevet i dette dokument. I nogle tilfælde, der er angivet nedenfor, påhviler det brugeren at foretage de nødvendige handlinger for at sikre, at en PDF-fil er i fuld overensstemmelse med PDF/UA.  Vi forventer, at brugeren tilføjer de relevante PDF/UA-versioner og overensstemmelses-id'er som det sidste trin i denne proces for at angive, at det nødvendige arbejde er blevet gjort for at gøre PDF-filen fuldt kompatibel med PDF/UA.

Alt, der er angivet i dette dokument, er baseret på gengivelse af et PDF-dokument med enhedsoplysninger, der angiver AccessiblePdf som `true`. I nogle tilfælde kan begrænsninger for overholdelse skyldes begrænsninger i Report Definition Language (RDL).

## <a name="6--conformance-requirements"></a>6.  Overensstemmelseskrav

|     Kriterier     |     Understøttende funktion     |     Bemærkninger      |
|----|--------|--------|
|    6.1 Generelt    |                 Understøttet    |    PDF-udvidelse til gengivelse skaber PDF-version 1.7.    |
|    6.2 Filer i overensstemmelse    |                 Understøttes med undtagelser    |    Se bemærkningerne i afsnit 7 – Krav til filformater.    |
|    6.3 Læser i overensstemmelse    |     Ikke tilgængelig     |         |
|    6.4 Assisterende teknologi i overensstemmelse    |     Ikke tilgængelig     |         |

## <a name="7--file-format-requirements"></a>7.  Krav til filformater

|     Kriterier     |     Understøttende funktion     |     Bemærkninger      |
|-----|-------|------------------------|
|    7.1 Generelt    |                 Understøttes med undtagelser    |    Alt reelt indhold skal mærkes som defineret i ISO 32000-1:2008, 14.8. Artefakter (ISO 32000-1:2008, 14.8.2.2.2) må ikke mærkes i strukturtræet. <li> PDF-gengivelsesudvidelsen giver ikke fleksibiliteten til eksplicit at markere individuelle elementer som artefakter, så det vil i stedet markere alt, der er knyttet til kriterierne i ISO 32000-1:2008, 14.8.2.2.2.<br>Indholdet skal være markeret i strukturtræet med semantisk relevante koder i en logisk læserækkefølge. <br> **Note** 4 WCAG 2.0, retningslinje 1.4, forklarer problemer med kontrast, farve og anden formatering for at sikre tilgængelighed. <br><li> Brugeren skal sikre, at vedkommendes dokument ikke er underlagt disse problemer. <br>Standardmærker defineret i ISO 32000-1:2008, 14.8.4 må ikke gentilknyttes. <li> PDF-gengivelsesudvidelsen gentilknytter ikke standardkoderne. Dokumenter starter med dokumentets rodelement. <br>Filer, der hævder at være i overensstemmelse med denne internationale standard, skal have en værdi for mistænkte på False (ISO 32000-1:2008, tabel 321). <li> PDF-gengivelsesudvidelsen har ikke en post med mistænkte. Denne egenskab er valgfri.    |
|    7.2 Tekst    |                 Understøttes med undtagelser    |    Indholdet skal mærkes i logisk læserækkefølge. Det mest semantisk relevante mærke skal bruges for hvert logisk element i dokumentindholdet. <br><li> PDF-gengivelsesudvidelsen mærker så vidt muligt indhold i logisk læserækkefølge.<br>Tegnkoder skal knyttes til Unicode som beskrevet i ISO 32000-1:2008, 14.8.2.4.2. Tegn, der ikke er inkluderet i Unicode-specifikationen, må bruge området for privat brug i Unicode eller erklære en anden tegnkodning. <br>Naturligt sprog skal erklæres som beskrevet i ISO 32000-1:2008, 14.9.2 og/eller som beskrevet i ISO 32000-1:2008, 7.9.2. Ændringer af et naturligt sprog skal deklareres. Ændringer af et naturligt sprog i tekststrenge (f.eks. i alternative beskrivelser) skal deklareres ved hjælp af et sprog-id som beskrevet i ISO 32000-1:2008, 14.9.2.2. <br><li> PDF-gengivelsesudvidelsen deklarerer kun et naturligt sprog på dokumentniveau    |
|    7.3 Grafik    |                 Understøttes med undtagelser    |    Grafikobjekter undtagen tekstobjekter skal mærkes med en figurkode som beskrevet i ISO 32000-1:2008, 14.8.4.5, tabel 340. Hvis en af følgende undtagelser er sand, skal grafikken mærkes som en artefakt: <br><li> grafikken repræsenterer ikke meningsfuldt indhold, eller <li>  grafikken vises som en baggrund til et linkannotation, og i dette tilfælde skal den alternative tekst på linket beskrive både grafikken og linket. <li> PDF-gengivelsesudvidelsen mærker grafikobjekter med figurkoden. <br>En billedtekst, der ledsager en figur, skal mærkes med et billedtekstmærke. <li> PDF-gengivelsesudvidelsen tillader i øjeblikket ikke billedtekster på figurer med et billedtekstmærke. <br>Figurkoder skal indeholde en alternativ gengivelse eller erstatningstekst, der repræsenterer det indhold, som er markeret med den mærkede figur, som det er angivet i ISO 32000-1:2008, 14.7.2, tabel 323. <br>**Note** 1 Se også WCAG 2.0, retningslinje 1.1. <br>Hvis tekst, der er repræsenteret i et grafikelement, ikke er tekst på et naturligt sprog, der er beregnet til at blive læst af en menneskelig læser, skal der angives en alternativ tekst, der beskriver grafikkens art eller formål. <br>**Note** 2 Tekst, der er et eksempel på en type eller et eksempel på det skrivesystem, der bruges af et sprog, er eksempler på tekst, som ikke er på et naturligt sprog.   PDF-gengivelsesudvidelsen understøtter al tekst i figurer, selvom det er op til brugeren for at tilføje den alternative tekst. <br>Yderligere bemærkning om attributten BBox: <br><li> PDF-gengivelsesudvidelsen skriver i øjeblikket ikke attributten BBox. <li> En løsning, der kan bruges til manuelt at skifte illustrationer som nye figurer eller som artefakter.    |
|    7.4 Overskrifter    |                 Ikke tilgængelig    |    RDL understøtter ikke mærkning af overskrifter på nogen måde. Det er op til brugeren at mærke dem efter behov.    |
|    7.5 Tabeller    |                 Understøttes med undtagelser    |    Tabeller skal indeholde overskrifter. Tabeloverskrifter skal mærkes i henhold til ISO 32000-1:2008, tabel 337 og tbel 349. <br>**Note** 1 Tabeller kan indeholde kolonneoverskrifter, rækkeoverskrifter eller begge dele. <br>**Note** 2 Der skal være så mange tilgængelige oplysninger om strukturen i tabeller som muligt, når teknologiske hjælpemidler er i brug. Overskrifter spiller en vigtig rolle i de strukturelle oplysninger. <br><li> Det er op til brugeren at medtage overskrifter i deres tabeller. RDL- og PDF-gengivelsesudvidelsen understøtter rækkeoverskrifter. <br>  Strukturelementer af typen TH skal have en områdeattribut.   <li> PDF-gengivelsesudvidelsen omfatter en områdeattribut for elementer for kolonne- og rækkemedlemmer, men ikke for hjørneceller.<br>Tabelmærkningsstrukturer må kun bruges til at mærke indhold, der vises i logiske rækker og/eller kolonnerelationer.   <li> Dette afhænger af, hvordan brugeren har valgt at bruge tabeller i deres RDL.    |
|    7.6 Lister    |                 Ikke tilgængelig    |    RDL understøtter ikke opmærkning af lister. I RDL er de struktureret i en tabel med en enkelt tabelcelle. <br>Det er op til brugeren at genmærke dem efter behov.    |
|    7.7 Matematiske udtryk    |                 Understøttes med undtagelser    |    Alle matematiske udtryk skal stå i en formelkode, som det er beskrevet i ISO 32000-1:2008, 14.8.4.5, og skal have en Alt-attribut. <br><li> PDF-gengivelsesudvidelsen omfatter i øjeblikket ikke matematiske udtryk i en formel kode. <br>Kravene vedrørende tilknytning af tegn til Unicode skal gælde for matematiske udtryk som angivet i ISO 32000-1:2008, 9.10.2 og 14.8.2.4. <br><li> Dette understøttes af PDF-gengivelsesudvidelsen.    |
|    7.8 Sidehoveder og sidefødder    |                 Understøttet    |    Løbende sidehoveder og sidefødder skal identificeres som sideinddelingsartefakter og skal klassificeres som undertyperne sidehoved eller sidefod i henhold til ISO 32000-1:2008, 14.8.2.2.2, tabel 330. <br><li> Sidehoveder og sidefødder behandles og kodes som artefakter.    |
|    7.9 Noter og referencer    |                 Ikke tilgængelig    |    PDF-gengivelsesudvidelsen understøtter ikke mærkning af noter og referencer. <br>Det er op til brugeren at mærke dem efter behov.    |
|    7.10 Valgfrit indhold    |                 Ikke tilgængelig    |         |
|    7.11 integrerede filer    |                 Ikke tilgængelig    |         |
|    7.12 Artikeltråde    |                 Ikke tilgængelig    |         |
|    7.13 Digitale signaturer    |                 Ikke tilgængelig    |         |
|    7.14 Ikke-interaktive formularer    |                 Ikke tilgængelig    |         |
|    7.15 XFA    |                 Ikke tilgængelig    |         |
|    7.16 Sikkerhed    |                 Ikke tilgængelig    |         |
|    7.17 Navigation    |                 Understøttet    |    Et dokument skal indeholde en dokumentdisposition, der matcher læserækkefølgen og niveauet af navigationsdestinationer (ISO 32000-1:2008, 12.3.3). <br><li> RDL understøtter bogmærker for et rapportelement, men brugeren skal vælge denne indstilling. Disse bogmærker gengives derefter som en dokumentkontur af PDF-gengivelsesudvidelsen. <br>Hvis det er angivet, skal posterne i træet med PageLabels-taltræet (ISO 32000-1:2008, 7.7.2, tabel 28) være semantisk relevante. <br><li> PDF-gengivelsesudvidelsen indeholder ikke et PageLabels-taltræ.    |
|    7.18 Annotationer    |                 Ikke tilgængelig    |    RDL understøtter ikke annotationer    |
|    7.21 skrifttyper    |                 Understøttet    |         |
|    7.21.1 Generelt    |                 Understøttet    |         |
|    7.21.2 Skrifttyper    |                 Understøttet    |         |
|    7.21.3 Sammensatte skrifttyper    |                 Understøttet    |         |
|    7.21.3.1 Generelt    |                 Understøttet    |         |
|    7.21 3.2 CID-skrifttyper    |                 Understøttet    |         |
|    7.21.3.3 CMaps    |                 Understøttet    |         |
|    7.21.4 Integration    |                 Understøttet    |         |
|    7.21.4.1 Generelt    |                 Understøttet    |         |
|    7.21.4.2 Integration af delmængde    |                 Understøttet    |         |
|    7.21.5 Skrifttypemålepunkter    |                 Understøttet    |         |
|    7.21.6 Tegnkodning    |                 Understøttet    |         |
|    7.21.7 Unicode-tegnkort    |                 Understøttet    |         |
|    7.21.8 Brug af .notdef glyph    |                 Understøttet    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Overholdelse af krav til læseren

Ikke tilgængelig

## <a name="9--at-requirements"></a>9.  AT-krav

Ikke tilgængelig

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Næste trin
[Administratoroversigt](admin-handbook-overview.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

