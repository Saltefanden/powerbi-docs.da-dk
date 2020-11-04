---
title: Underrapporter i sideinddelte rapporter i Power BI
description: I denne artikel får du mere at vide om understøttede datakilder for sideinddelte rapporter i Power BI-tjenesten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 04/29/2020
ms.openlocfilehash: d2cd4e9f5d6cb8872e266fabacb9f8a5a3e318cb
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298004"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Underrapporter i sideinddelte rapporter i Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

En *underrapport* er et sideinddelt rapportelement, der viser en anden sideinddelt rapport i den primære del af en sideinddelt hovedrapport. En underrapport i en rapport er begrebsmæssigt magen til en ramme på en webside. Du kan bruge den til at integrere en rapport i en anden rapport. Du kan bruge en hvilken som helst rapport som en underrapport. Du gemmer den rapport, der vises som underrapport, i det samme Premium-arbejdsområde som den overordnede rapport. Du kan designe den overordnede rapport, så den overfører parametre til underrapporten. En underrapport kan gentages i dataområder ved hjælp af en parameter til filtrering af data i hver enkelt forekomst af underrapporten.  
  
 ![Underrapport i en sideinddelt rapport](media/subreports/paginated-report-subreport.png "Underrapport i sideinddelt rapport")  
  
 I denne illustration stammer de kontaktoplysninger, der vises i hovedrapporten Salgsordre, faktisk fra underrapporten Kontakter.  
  
Du opretter og redigerer definitionsfiler for sideinddelte rapporter (. rdl) i Power BI Report Builder. Du kan uploade underrapporter, der er gemt i SQL Server Reporting Services, til et Premium-arbejdsområde i Power BI-tjenesten. Hovedrapporterne og underrapporterne skal publiceres i det samme arbejdsområde. Installér [Power BI Report Builder](https://aka.ms/pbireportbuilder).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>Arbejd med Report Builder og Power BI-tjenesten

Power BI Report Builder kan arbejde med sideinddelte rapporter på computeren (kaldet lokale rapporter) eller med rapporter i Power BI-tjenesten.  Første gang, du åbner Report Builder, bliver du bedt om at logge på din Power BI-konto. Hvis ikke, skal du **logge på** i øverste højre hjørne.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Log på Power BI":::

Efter du er logget på, kan du se muligheden **Power BI-tjeneste** i Power BI Report Builder for mulighederne **Åbn** og **Gem som** i menuen **Filer**. Når du vælger muligheden **Power BI-tjeneste** til at gemme en rapport, kan du oprette en liveforbindelse mellem Power BI Report Builder og Power BI-tjenesten. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Åbn fra Power BI-tjenesten":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Gem en lokal rapport i Power BI-tjenesten

Du skal først oprette de to rapporter og gemme dem i det samme Power BI Premium-arbejdsområde, før du kan føje en underrapport til en hovedrapport. 

1. Hvis du vil åbne en eksisterende lokal rapport, skal du i menuen **Filer** vælge **Åbn** > **Denne pc** og vælge en .rdl-fil.  

2. I menuen **Filer** skal du vælge **Gem som** > **Power BI-tjeneste**.  Se [Publicer en sideinddelt rapport i Power BI-tjenesten](paginated-reports-save-to-power-bi-service.md) for at få flere oplysninger.

    > [!NOTE]
    > Du kan også uploade en rapport ved at starte i Power BI-tjenesten. Artiklen [Publicer en sideinddelt rapport i Power BI-tjenesten](paginated-reports-save-to-power-bi-service.md) indeholder flere detaljer.

3. I dialogboksen **Gem som** skal du vælge et Power BI Premium-arbejdsområde, hvor du kan gemme dine sideinddelte rapporter.  Premium-arbejdsområder har et rombeikon ![Premium-rombeikon](media/subreports/report-builder-premium-diamond.png) ud for deres navn.

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Gem som i Power BI-tjenesten":::

4. Vælg **Gem**.

## <a name="add-a-subreport-to-a-report"></a>Føj en underrapport til en rapport

Nu, hvor du har gemt begge rapporter i det samme Premium-arbejdsområde, kan du føje den ene til den anden som en underrapport. Der er to måder at tilføje en underrapport på. 

1. På båndet **Indsæt** skal du vælge knappen **Underrapport** eller højreklikke på rapportlærredet og vælge **Indsæt** > **Underrapport**.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Indsæt en underrapport i en rapport":::

    Dialogboksen **Egenskaber for underrapport** åbnes.  

2. Vælg knappen **Gennemse** > naviger til den rapport, du vil bruge som underrapport > angiv navnet på underrapporten i tekstfeltet **Navn**.

3. Konfigurer andre egenskaber efter behov, herunder [parametre](#use-parameters-in-subreports).

## <a name="use-parameters-in-subreports"></a>Brug parametre i underrapporter  
 Hvis du vil overføre parametre fra den overordnede rapport til underrapporten, skal du definere en rapportparameter i den rapport, du bruger som underrapport. Når du placerer underrapporten i den overordnede rapport, kan du vælge rapportparameteren og en værdi, der skal overføres fra den overordnede rapport til rapportparameteren i underrapporten.  
  
> [!NOTE]  
> Den parameter, du vælger fra underrapporten, er en parameter af typen *rapport* og ikke en parameter af typen *forespørgsel*.  
  
 Du kan placere en underrapport i den primære del af rapporten eller i et dataområde. Hvis du placerer en underrapport i et dataområde, gentages underrapporten med hver forekomst af gruppen eller rækken i dataområdet. Du kan overføre en værdi fra gruppen eller rækken til underrapporten. I egenskaben for værdi i underrapporten skal du bruge et feltudtryk for det felt, der indeholder den værdi, du vil overføre til parameteren for underrapporten.  
  
 Du kan finde flere oplysninger om at arbejde med parametre og underrapporter i [Tilføj en underrapport og parametre](/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs) i dokumentationen til SQL Server Reporting Services.  

## <a name="preview-paginated-reports-in-report-builder"></a>Se en forhåndsvisning af sideinddelte rapport i Report Builder

Du kan se en forhåndsvisning af rapporter i Report Builder.

- På båndet **Hjem** skal du vælge **Kør**. 

Da Report Builder er et designværktøj, kan forhåndsvisningen af rapporten se anderledes ud end gengivelsen af rapporten i Power BI-tjenesten.

### <a name="notes-about-previewing"></a>Noter om forhåndsvisning

- Report Builder gemmer ikke legitimationsoplysninger for de datakilder, der bruges i rapporter.  Report Builder beder dig om hvert sæt legitimationsoplysninger under forhåndsvisningen.  
- Hvis rapportens datakilder er i det lokale miljø, skal du konfigurere en gateway, når du har gemt rapporten i Power BI-arbejdsområdet.
- Hvis der opstår en fejl i Report Builder under forhåndsvisningen, returneres der en generisk meddelelse.  Hvis det er svært at udføre fejlfinding af fejlen, kan du overveje at gengive rapporten i Power BI-tjenesten.  

## <a name="considerations"></a>Overvejelser

### <a name="maintaining-the-connection"></a>Bevarelse af forbindelsen

Report Builder bevarer ikke forbindelsen til Power BI, når du lukker filen.  Det er muligt at arbejde med en lokal hovedrapport med underrapporter, der er gemt i Power BI-arbejdsområdet. Sørg for at gemme hovedrapporten i Power BI-arbejdsområdet, før du lukker rapporten.  Hvis du ikke gør det, får du måske vist meddelelsen "ikke fundet" under forhåndsvisningen, fordi der ikke er en liveforbindelse til Power BI-tjenesten.  I så fald skal du gå til en underrapport og vælge dens egenskaber.  Åbn underrapporten igen via Power BI-tjenesten.  Dermed genetableres forbindelsen, og alle andre underrapporter bør være okay.

### <a name="renaming-a-subreport"></a>Omdøbning af en underrapport

Hvis du omdøber en underrapport i arbejdsområdet, skal du rette navnereferencen i hovedrapporten. Ellers gengives underrapporten ikke. Hovedrapporten gengives stadig med en fejlmeddelelse i elementet for underrapporten.

## <a name="migrate-large-reports"></a>Overfør store rapporter

Hvis du overfører store rapporter til Power BI, bør du overveje at bruge [RdlMigration-værktøjet](../guidance/migrate-ssrs-reports-to-power-bi.md).  RdlMigration-værktøjet er blevet opdateret, så det kan håndtere dublerede navne på underrapporter.  Der kan forekomme dublerede navne på underrapporter, hvis to eller flere rapporter deler det samme navn, men befinder sig i forskellige undermapper.  Hvis navnene ikke fortolkes entydigt, er det kun den første underrapport, der genkendes.

Hvis du vil bruge Report Builder til at overføre store rapporter, anbefales det, at du arbejder med underrapporterne først. Gem hver enkel i Power BI-arbejdsområdet for at forhindre eventuelle dublerede rapportnavne.

## <a name="share-reports-with-subreports"></a>Del rapporter med underrapporter

Som beskrevet tidligere, skal hovedrapporter og underrapporter befinde sig i det samme arbejdsområde. Ellers gengives underrapporten ikke. Når du deler hovedrapporten, skal du også dele underrapporterne. Hvis du deler hovedrapporten i en app, skal du sørge for, at du også inkluderer underrapporterne i den pågældende app. Hvis du deler hovedrapporten med brugere eller brugergrupper direkte, skal du sørge for, at du også deler hver underrapport med de samme brugere eller brugergrupper.
  
## <a name="next-steps"></a>Næste trin

[Foretag fejlfinding af underrapporter i sideinddelte rapporter i Power BI](subreports-troubleshoot.md)

[Publicer en sideinddelt rapport i Power BI-tjenesten](../consumer/paginated-reports-view-power-bi-service.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)