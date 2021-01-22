---
title: Løs problemer, når Power BI Desktop startes
description: Løs problemer, når Power BI Desktop startes
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 11/14/2020
LocalizationGroup: Troubleshooting
ms.openlocfilehash: c41f8f9b23ef57d5dd6fd4b851918b7ffa5904a0
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226933"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Fejlfind åbning af Power BI Desktop

Denne artikel indeholder en beskrivelse og afhjælpning af en række situationer, hvor Power BI ikke åbner. 

## <a name="resolve-issues-with-opening-encrypted-pbix-files"></a>Løs problemer med at åbne krypterede PBIX-filer

Du kan ikke åbne krypterede .pbix-filer ved hjælp af en Power BI Desktop-version, der ikke understøtter Information Protection.

Hvis du fortsat har brug for at bruge Power BI Desktop, anbefales det, at du opdaterer det til en version, der understøtter Information Protection. Du kan downloade den [nyeste version af Power BI Desktop](https://www.microsoft.com/download/confirmation.aspx?id=58494) (dette link er et direkte downloadlink til det eksekverbare installationsprogram). Den nyeste version af Power BI Desktop understøtter Information Protection og kan dekryptere og åbne en krypteret PBIX-fil.

###

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Løs problemer med datagatewayen i det lokale miljø og Power BI Desktop

I Power BI Desktop kan brugere, der har installeret og kører tidligere versioner af *Power BI-datagatewayen i det lokale miljø*, blive blokeret, så de ikke kan starte Power BI Desktop. Det skyldes administrative politikbegrænsninger, som Power BI gatewayen i det lokale miljø har angivet for navngivne pipes på den lokale computer.

Du har tre muligheder for at løse det problem, der er knyttet til datagatewayen i det lokale miljø, og gøre det muligt at starte Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Løsning 1: Installér den nyeste version af Power BI-datagatewayen i det lokale miljø

Den nyeste version af Power BI datagatewayen i det lokale miljø angiver ikke begrænsninger for navngivne pipes på den lokale computer, hvilket gør det muligt at starte Power BI Desktop korrekt. Den anbefalede løsning, hvis du vil fortsætte med at bruge Power BI-datagatewayen i det lokale miljø, er at opdatere den. Du kan downloade den [nyeste version af Power BI-datagatewayen i det lokale miljø fra denne placering](https://go.microsoft.com/fwlink/?LinkId=698863). Linket er et direkte link til download af den eksekverbare installationsfil.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Løsning 2: Fjern eller stop Microsoft-tjenesten til Power BI-datagatewayen i det lokale miljø

Du kan fjerne Power BI-datagatewayen i det lokale miljø, hvis du ikke længere har brug for den. Eller du kan stoppe Power BI-datagatewayen i det lokale miljø, hvilket fjerner politikbegrænsningen og gør det muligt for Power BI Desktop at åbne den.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Løsning 3: Kør Power BI Desktop med administratorrettigheder

Du kan også starte Power BI Desktop som administrator, hvilket også gør det muligt for Power BI Desktop at åbne. Det anbefales stadig, at du installerer den nyeste version af Power BI-datagatewayen i det lokale miljø, som beskrevet tidligere.

Power BI Desktop er udviklet som en arkitektur til flere processer, og flere af disse processer kommunikerer ved hjælp af navngivne Windows-pipes. Der kan være andre processer, som er i konflikt med disse navngivne pipes. Den mest almindelige årsag til denne konflikt er sikkerhed, herunder situationer, hvor antivirussoftware eller firewalls blokerer pipes eller omdirigerer trafik til en bestemt port. Du kan muligvis løse problemet ved at åbne Power BI Desktop med administratorrettigheder. Hvis du ikke kan åbne med administratorrettigheder, skal du bede administratoren om at afgøre, hvilke sikkerhedsregler der forhindrer, at navngivne pipes kan kommunikere korrekt. Derefter kan du tilføje Power BI Desktop og de respektive underprocesser til hvidlister.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Løs problemer, når der oprettes forbindelse til SQL Server

Når du forsøger at oprette forbindelse til en SQL Server-database, kan du støde på en fejlmeddelelse, der minder om følgende tekst:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

Du kan ofte løse problemet, hvis du åbner Power BI Desktop som administrator, før du opretter SQL Server-forbindelsen.

Når du har åbnet Power BI Desktop som administrator og opretter forbindelse, registreres de påkrævede DLL'er korrekt. Herefter er det ikke nødvendigt at åbne Power BI Desktop som administrator. I de tilfælde, hvor du opretter forbindelse til SQL Server med alternative legitimationsoplysninger, skal du åbne Power BI Desktop som administrator, hver gang du opretter forbindelse.

## <a name="get-help-with-other-launch-issues"></a>Få hjælp til andre startproblemer

Vi bestræber os på at dække så mange af de problemer, der kan opstå i forbindelse med Power BI Desktop, som muligt. Vi kigger jævnligt på problemer, der kan påvirke mange kunder, og inkluderer dem i vores artikler.

Hvis problemet med at åbne Power BI Desktop ikke er knyttet til datagatewayen i det lokale miljø, eller hvis tidligere løsninger ikke virker, kan du sende en supporthændelse til *Power BI-support* (<https://support.powerbi.com>) for at få hjælp til at identificere og løse problemet.

Hvis du støder på andre problemer i fremtiden med Power BI Desktop, er det nyttigt at aktivere sporing og indsamle logfiler. Logfiler kan muligvis hjælpe dig med at isolere og identificere problemet. Hvis du vil slå sporing til, skal du vælge **Fil** > **Indstillinger** > **Indstillinger**, vælge **Diagnosticering** og derefter vælge **Aktivér sporing**. Power BI Desktop skal køre, for at du kan angive denne indstilling, men det er nyttigt, hvis der fremover opstår problemer med at åbne Power BI Desktop.
