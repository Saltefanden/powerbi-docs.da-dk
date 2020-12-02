---
title: Effektanalyse af datakilder
description: Forstå, hvor din datakilde bruges.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 07/20/2020
LocalizationGroup: ''
ms.openlocfilehash: 8c8a2a701415d9e937c5b592c915e51a4921840b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411879"
---
# <a name="data-source-impact-analysis"></a>Effektanalyse af datakilder

Effektanalyse af datakilder hjælper dig med at se, hvor din datakilde bruges i hele organisationen. Dette kan være nyttigt, når datakilden midlertidigt eller permanent er offline, og du gerne vil have en idé om, hvem der er berørt af det. Analysen viser dig, hvor mange arbejdsområder, dataflow og datasæt der bruger datakilden, og giver dig mulighed for nemt at gå til de arbejdsområder, hvor de berørte dataflow og datasæt er placeret, så du kan undersøge dem nærmere.

Effektanalyse af datakilder kan også hjælpe dig med at opdage dublerede data i lejeren, f.eks. når flere forskellige brugere bygger ens modeller oven på den samme datakilde. Ved at hjælpe dig med at registrere disse redundante datasæt og dataflow understøtter effektanalysen af datakilder målet med at have "en enkelt kilde til sandheden".

## <a name="perform-data-source-impact-analysis"></a>Udfør en effektanalyse af datakilder

Sådan udfører du en effektanalyse af datakilder:

1. Gå til det arbejdsområde, der indeholder den datakilde, du er interesseret i, og åbn [dataafstamningsvisningen](service-data-lineage.md).
1. Find datakildens kort, og klik på ikonet for effektanalyse.

    ![Skærmbillede af datakildens kort, der viser knappen til effektanalyse.](media/service-data-source-impact-analysis/data-source-impact-analysis-button.png)
 
Sidepanelet for effektanalyse åbnes.

![Skærmbillede af sideruden til effektanalyse af datakilder.](media/service-data-source-impact-analysis/data-source-impact-analyis-side-pane.png)
 
* **Datakildetype**: Angiver datakildetypen
* **Sti til datakilde**: Stien til datakilden, som den er defineret i Power BI Desktop. På ovenstående billede er stien til datakilden til SQL Server-databasen f.eks. forbindelsesstrengen "twitterDB-yaronctestingdb1.database.windows.net" som defineret i Power BI Desktop (vist nedenfor). Den består af databasenavnet "twitterDB" og servernavnet "yaronctestingdb1.database.windows.net".

    ![Skærmbillede af definition af forbindelsesstreng i Power BI Desktop.](media/service-data-source-impact-analysis/connection-string-definition-in-desktop.png)
 
* **Effektoversigt**: Viser antallet af potentielt påvirkede arbejdsområder, dataflow og datasæt. Dette antal omfatter arbejdsområder, som du ikke har adgang til.
* **Brugsopdeling**: Viser navnet på de påvirkede dataflow og datasæt for hvert arbejdsområde. Hvis du vil undersøge effekten på et bestemt arbejdsområde, skal du klikke på navnet på arbejdsområdet for at åbne arbejdsområdet. Når du er i det berørte arbejdsområde, skal du bruge [effektanalysen af datasæt](service-dataset-impact-analysis.md) for at se oplysninger om tilknyttede rapporter og dashboards.

## <a name="notify-contacts"></a>Giv kontakter besked

Hvis du har foretaget en ændring af en datakilde eller påtænker at gøre det, kan det være en god idé at kontakte de relevante brugere for at fortælle dem om det. Når du giver kontakter besked, sendes der en mail til [listen over kontakter](service-create-the-new-workspaces.md#create-a-contact-list) for alle de påvirkede arbejdsområder (i tilfælde af klassiske arbejdsområder sendes mailen til arbejdsområdets administratorer). Dit navn vises på mailen, så kontakterne kan finde dig og besvare dig i en ny mailtråd. 

1. Klik på **Giv kontakter besked** i ruden Effektanalyse. Dialogboksen Giv kontakter besked vises.

   ![Skærmbillede af dialogboksen Giv kontaktpersoner besked for datakilden.](media/service-data-source-impact-analysis/notify-contacts-dialog.png)

1. I tekstfeltet kan du angive oplysninger om ændringen.
1. Når meddelelsen er klar, skal du klikke på **Send**.

## <a name="privacy"></a>Beskyttelse af personlige oplysninger

I sideruden for effektanalyse får du kun vist navnene på de arbejdsområder, datasæt og dataflow, som du har adgang til. De elementer, du ikke har adgang til, er angivet under Begrænset adgang. Det skyldes, at nogle elementnavne kan indeholde personlige oplysninger.
Antallet af påvirkede elementer omfatter alle påvirkede dataflow og datasæt, også dem, der befinder sig i arbejdsområder, som du ikke har adgang til.

## <a name="limitations"></a>Begrænsninger

Effektanalyse af datakilder understøttes endnu ikke for sideinddelte rapporter, så du kan ikke se, om datakilden har en direkte effekt på disse typer rapporter i lejeren.

## <a name="next-steps"></a>Næste trin

* [Effektanalyse af datasæt](service-dataset-impact-analysis.md)
* [Dataafstamning](service-data-lineage.md)