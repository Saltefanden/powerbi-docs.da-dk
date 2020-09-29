---
title: Kopiér og indsæt en visualisering i Power BI
description: Kopiér og indsæt en visualisering i Power BI
author: mihart
ms.reviewer: maggie tsang
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 09/18/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 785f16b84dee1509ab04255587724e5ce39a043c
ms.sourcegitcommit: cb606d3ae95300683caf1853e229d8981302a8e2
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/18/2020
ms.locfileid: "90763108"
---
# <a name="copy-and-paste-a-report-visualization"></a>Kopiér og indsæt en rapportvisualisering

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

I denne artikel beskrives to forskellige måder at kopiere og indsætte en visualisering på. 
* Kopiér en visualisering i en rapport, og indsæt den på en anden rapportside (kræver redigeringstilladelser til rapporten)

* Kopiér et billede af en visualisering fra Power BI til udklipsholder, og indsæt det i andre programmer (tilgængelig i Power BI-tjenesten og mobilversionen, ikke tilgængelig i Power BI Desktop)

## <a name="copy-and-paste-within-the-same-report"></a>Kopiér og indsæt i den samme rapport
Visualiseringer i Power BI-rapporter kan kopieres fra én side i rapporten til den samme side eller en anden side i den samme rapport. 

Kopiering og indsættelse af en visualisering kræver redigeringsrettigheder til rapporten. I Power BI-tjenesten betyder det, at rapporten skal åbnes i [Redigeringsvisning](../consumer/end-user-reading-view.md). 

Visualiseringer på *dashboards* kan ikke kopieres og indsættes i Power BI-rapporter eller andre dashboards.

1. Åbn en rapport, der har mindst én visualisering.  

2. Marker visualiseringen, og brug **Ctrl+C** for at kopiere og **Ctrl+V** for at indsætte.      

   ![kort video, der viser, hvordan du kopierer og indsætter](media/power-bi-visualization-copy-paste/copypasteviznew.gif)


## <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Kopiér en visualisering som et billede til Udklipsholder

Har du nogensinde ønsket at dele et billede fra en Power BI-rapport eller et dashboard? Du kan nu kopiere visualiseringen fra Power BI-tjenesten eller Power BI – Mobil og indsætte den i et hvilket som helst andet program, der understøtter indsættelse. 

Når du kopierer et statisk billede af en visualisering, får du en kopi af visualiseringen sammen med metadataene. Dette omfatter:
* et link, der fører tilbage til Power BI-rapporten eller -dashboardet
* titlen på rapporten eller dashboardet
* bemærk, om billedet indeholder fortrolige oplysninger
* tidsstempel for seneste opdatering
* filtre anvendt på visualiseringen

### <a name="copy-from-a-dashboard-tile"></a>Kopiér fra et dashboardfelt

1. Åbn Power BI-tjenesten, og naviger til det dashboard, du vil kopiere fra.

2. I øverste højre hjørne i visualiseringen skal du vælge **Flere indstillinger (...)** og vælge **Kopiér visualisering som billede**. 

    ![Ikonet Kopiér visualisering som billede er vist](media/power-bi-visualization-copy-paste/power-bi-copy-dashboard.png)

3. Når dialogboksen **Din visualisering er klar til kopiering** vises, skal du vælge **Kopiér til Udklipsholder**.

    ![dialogboks med indstillingen Kopiér til Udklipsholder](media/power-bi-visualization-copy-paste/power-bi-copied.png)

4. Når din visualisering er klar, skal du indsætte den i et andet program ved hjælp af **Ctrl + V** eller højreklikke på > Indsæt. På skærmbilledet nedenfor har vi indsat visualiseringen i Microsoft Word. 

    ![visualisering indsat i Word](media/power-bi-visualization-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Kopiér fra en visualisering i en rapport 

1. Åbn Power BI-tjenesten, og gå til den rapport, du vil kopiere fra.

2. I øverste højre hjørne i visualiseringen skal du vælge ikonet for **Kopiér visualisering som billede**. 

    ![Skærmbillede, der viser kopieret visualisering som et billedikon](media/power-bi-visualization-copy-paste/power-bi-copy-icon.png)

3. Når dialogboksen **Din visualisering er klar til kopiering** vises, skal du vælge **Kopiér til Udklipsholder**.

    ![dialogboks med indstillingen Kopiér til Udklipsholder](media/power-bi-visualization-copy-paste/power-bi-copied.png)


4. Når din visualisering er klar, skal du indsætte den i et andet program ved hjælp af **Ctrl + V** eller højreklikke på > Indsæt. På skærmbilledet nedenfor har vi indsat visualiseringen i en mail.

    ![visualisering indsat i Outlook](media/power-bi-visualization-copy-paste/power-bi-copy-email.png)

5. Hvis der er anvendt en følsomhedsmærkat for dataene i rapporten, får du vist en advarsel, når du vælger ikonet for kopiering.  

    ![advarsel om følsomme data](media/power-bi-visualization-copy-paste/power-bi-sensitive.png)

    Og der føjes en følsomhedsmærkat til metadataene under den indsatte visualisering. 

    ![visualisering med mærkat for fortrolige oplysninger](media/power-bi-visualization-copy-paste/power-bi-confidential.png)

### <a name="manage-use-of-copying-a-visual-as-an-image"></a>Administrer brugen af kopiering af en visualisering som et billede
Hvis du ejer indholdet eller er administrator af lejeren, kan du styre, om en visualisering kan kopieres som et billede fra en rapport eller et dashboard.

#### <a name="disable-copy-as-an-image-for-a-specific-visual"></a>Deaktiver kopiering som et billede for en bestemt visualisering
Hvis du ikke vil have, at brugerne skal kunne kopiere en bestemt visualisering, kan du fjerne ikonet for kopiering fra den pågældende visualisering i Power BI-tjenesten.    
1. Vælg ikonet med malerrullen for at åbne fanen Formatering. 

1. Åbn kortet **Formatering af visualisering**.
1. Rul ned til **Overskrift i visualisering**, udvid kortet, og slå **ikonet Kopiér** fra.

    ![malerrulle og ikon for kopiering er valgt](media/power-bi-visualization-copy-paste/power-bi-visual-header.png)

1. Hvis du ikke kan finde indstillingen **Overskrift i visualisering**, skal du slå indstillingen for moderne overskrift i visualisering til under **Rapportindstillinger**. 

    ![aktivering af den moderne overskrift i visualisering er valgt](media/power-bi-visualization-copy-paste/power-bi-use-modern.png)

1. Gem ændringerne. Del igen, og genudgiv efter behov.

#### <a name="disable-copy-as-an-image-for-a-group-of-users"></a>Deaktiver kopiering som et billede for en brugergruppe

Hvis du ejer indholdet eller er administrator af lejeren, kan du styre, hvem der kan kopiere visualiseringer. Denne indstilling deaktiverer *kopiering af visualisering som et billede* for alt indhold, som brugeren har adgang til i Power BI-lejeren.
  
1. Naviger til Administrationsportalen.

1. Under **Lejerindstillinger** skal du vælge **Eksport- og delingsindstillinger**. 

    ![aktivér kopiering og indsættelse af visualiseringer](media/power-bi-visualization-copy-paste/power-bi-enable.png)

1. Deaktiver **Kopiér og indsæt visualiseringer** for dine valgte brugergrupper. 

1. Gem ændringerne. Nu kan de angivne grupper ikke bruge **Kopiér visualisering som billede** i hele Power BI. 
  

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

   ![kopiering er ikke tilgængelig](media/power-bi-visualization-copy-paste/power-bi-copy-grey.png)


Spørgsmål: Jeg kan ikke finde indstillingen Kopiér som billede    
Svar: Hvis du bruger Power BI Desktop, er denne funktion endnu ikke tilgængelig    
Spørgsmål: Hvorfor er ikonet Kopiér deaktiveret på en visualisering?    
Svar: Vi understøtter i øjeblikket oprindelige Power BI-visualiseringer og certificerede visualiseringer. Der er begrænset understøttelse af bestemte visualiseringer, herunder: 
- ESRI og andre kortvisualiseringer 
- Python-visualiseringer 
- R-visualiseringer 
- PowerApps 
- Brugerdefinerede visualiseringer, der ikke er certificerede. Få mere at vide om [hvordan du certificerer din brugerdefinerede visualisering](../developer/visuals/power-bi-custom-visuals-certified.md) for at få din brugerdefinerede visualisering understøttet. 


Spørgsmål: Hvorfor indsættes min visualisering ikke korrekt?    
Svar: Der er begrænsninger for kopiering af visualiseringer som et billede, herunder: 
- For brugerdefinerede visualiseringer 
    - Visualiseringer med anvendte temaer og farver 
    - Feltskalering, når der indsættes 
    - Brugerdefinerede visualiseringer med animationer 
- Kopieringsbegrænsninger 
    - Et dashboardfelt, der er fastgjort for nylig, kan ikke kopieres 
    - Brugere kan ikke omdirigeres til indhold med Odata-filtre og specifikke tilstande, f.eks. personlige bogmærker 
- Det er muligvis ikke alt, som blev kopieret fra visualiseringen, der gengives i programmer med begrænset understøttelse af indsættelse af HTML-formateret indhold fra Udklipsholder 



## <a name="next-steps"></a>Næste trin
Få mere at vide om [Visualiseringer i Power BI-rapporter](power-bi-report-visualizations.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

