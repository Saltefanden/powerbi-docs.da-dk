---
title: Lad brugerne tilpasse visualiseringer i en rapport
description: Lad læserne af en rapport oprette deres egen visning af en rapport uden at redigere den.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/25/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 4eae96dbdddae82a7f74f27c835874a19b04a69f
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256806"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Lad brugerne tilpasse visualiseringer i en rapport

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Når du deler en rapport med en bred målgruppe, vil nogle af brugerne måske gerne se en lidt anden visning af bestemte visualiseringer. Måske vil de gerne bytte om på aksen, ændre visualiseringstype eller føje noget til værktøjstippet. Det er svært at lave én visualisering, der opfylder alles krav. Med denne nye funktionalitet giver du dine virksomhedsbrugere mulighed for at udforske og tilpasse visualiseringer – alt sammen i læsevisningen af rapporten. De kan tilpasse visualiseringen, lige som de vil, og gemme den som et bogmærke, så de kan vende tilbage til den. De behøver ikke at have redigeringstilladelser til rapporten eller henvende sig til rapportforfatteren med en ændring.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Tilpas en visualisering":::
 
## <a name="what-report-users-can-change"></a>Hvad kan rapportbrugere ændre?

Denne funktion giver virksomhedsbrugerne mulighed for at få yderligere indsigt via ad hoc-udforskning af visualiseringer i en Power BI-rapport. Hvis du vil have mere at vide om, hvordan du bruger denne funktion som bruger, skal du se [Tilpas visualiseringer i dine rapporter](../consumer/end-user-personalize-visuals.md). Funktionen er ideel til rapportudviklere, der gerne vil aktivere grundlæggende udforskningsscenarier for læserne af deres rapport. Læserne af rapporten kan udføre følgende ændringer:

- Ret visualiseringstypen
- Udskift en måling eller dimension
- Tilføj eller fjern en forklaring
- Sammenlign to eller flere målinger
- Skift sammenlægninger osv.

Denne funktion muliggør ikke kun nye udforskningsegenskaber. Den omfatter også måder for brugerne at registrere og dele deres ændringer:

- Registrer deres ændringer
- Del deres ændringer
- Nulstil alle deres ændringer af en rapport
- Nulstil alle deres ændringer af en visualisering
- Ryd deres seneste ændringer

## <a name="use-perspectives-for-a-more-focused-view"></a>Brug perspektiver for at få en mere fokuseret visning

Hvis du vil tilpasse visualiseringer, kan du bruge **perspektiver** til at vælge et undersæt af en model, hvilket giver en mere fokuseret visning. Det kan være nyttigt at vælge et undersæt, når du arbejder med en stor datamodel, så du kan fokusere på et undersæt af feltet, der kan administreres, og ikke overvælde læserne af rapporten med hele samlingen af felter i den store model. 

![Tilpas visualiseringer](media/power-bi-personalize-visuals/power-bi-personalize-perspective-01.png)

Vær opmærksom på følgende, når du arbejder med perspektiver:

* Perspektiver er ikke beregnet til at blive brugt som en sikkerhedsmekanisme. Det er værktøjer, du kan bruge til at give slutbrugeren en bedre oplevelse. Al sikkerhed for et perspektiv nedarves fra den underliggende model.

* Perspektiver i både tabellariske og flerdimensionelle modeller understøttes. Men for perspektiver i flerdimensionelle modeller kan du kun indstille perspektivet til at være den samme som udgangskuben for rapporten.

* Før du sletter et perspektiv fra en model, skal du huske at kontrollere, at perspektivet ikke bruges i oplevelsen Tilpas visualiseringer. 

Hvis du vil bruge perspektiver, skal du aktivere Tilpas visualiseringer for rapporten. Du skal også oprette mindst ét perspektiv, der indeholder de dimensioner og målinger, du ønsker, at slutbrugerne skal interagere med i forbindelse med oplevelsen Tilpas visualiseringer.

Hvis du vil oprette perspektivet, skal du bruge [Tabular Editor](https://tabulareditor.com/), som du kan downloade fra følgende placering: Download af Tabular Editor

Når du har installeret **Tabular Editor**, skal du åbne din rapport i **Power BI Desktop** og starte **Tabular Editor** under fanen **Eksterne værktøjer** på båndet som vist på følgende billede.

![Tabular Editor på båndet Eksterne værktøjer](media/power-bi-personalize-visuals/power-bi-personalize-perspective-02.png)

I Tabular Editor skal du højreklikke på mappen **Perspektiver** for at oprette et nyt perspektiv.

![Opret en ny mappe af typen Perspektiv i Tabular Editor](media/power-bi-personalize-visuals/power-bi-personalize-perspective-03.png)

Du kan dobbeltklikke på teksten for at omdøbe perspektivet.

![Omdøb perspektivet](media/power-bi-personalize-visuals/power-bi-personalize-perspective-04.png)

Derefter skal du føje felter til perspektivet ved at åbne mappen **Tabeller** i Tabular Editor og højreklikke på de felter, du vil have vist i perspektivet.

![Føj felter til et perspektiv](media/power-bi-personalize-visuals/power-bi-personalize-perspective-05.png)

Gentag processen for hvert af de felter, du vil føje til perspektivet. Du kan ikke tilføje duplikerede felter i et perspektiv, så muligheden for at tilføje felter er deaktiveret for de felter, du allerede har føjet til et perspektiv.

Når du har tilføjet alle de ønskede felter, skal du sørge for at gemme dine indstillinger både i Tabular Editor og derefter også i Power BI Desktop.

![Gem indstillinger for perspektiver i Tabular Editor og Power BI Desktop](media/power-bi-personalize-visuals/power-bi-personalize-perspective-06.png)

Når du har gemt det nye perspektiv i modellen, og du har gemt Power BI Desktop-rapporten, skal du navigere til ruden **Formatér** for siden, hvor du kan se en ny sektion for **Tilpas visualisering**.

![Sektionen Tilpas visualisering i ruden Formatér](media/power-bi-personalize-visuals/power-bi-personalize-perspective-07.png)

Indstillingen for *Rapport-læser-perspektiv* er som udgangspunkt angivet til *Standardfelter*. Når du vælger rullelistepilen, kan du se de andre perspektiver, du har oprettet.

![Vælg rullelistepilen for at se dine andre perspektiver](media/power-bi-personalize-visuals/power-bi-personalize-perspective-08.png)

Når du har angivet perspektivet for rapportsiden, filtreres oplevelsen Tilpas visualiseringer for den pågældende side til det valgte perspektiv. Hvis du vælger **Anvend på alle sider**, kan du anvende indstillingen for Perspektiv på alle eksisterende sider i rapporten.

![Vælg Anvend på alle sider for perspektivet for at anvende det på hele rapporten](media/power-bi-personalize-visuals/power-bi-personalize-perspective-09.png)

## <a name="enable-personalization-in-a-report"></a>Aktivér tilpasning i en rapport

Du kan aktivere denne funktion enten i Power BI Desktop eller Power BI-tjenesten.

### <a name="in-power-bi-desktop"></a>I Power BI Desktop

Du aktiverer funktionen i Power BI Desktop ved at gå til **Filer** > **Indstillinger** > **Indstillinger** > **Aktuel fil** > **Rapportindstillinger**. Sørg for, at **Tilpas visualiseringer** er slået til.

:::image type="content" source="media/power-bi-personalize-visuals/personalize-report-setting-desktop.png" alt-text="Tilpas en visualisering":::

### <a name="in-the-power-bi-service"></a>I Power BI-tjenesten

Du aktiverer funktionen i Power BI-tjenesten ved at gå til **Indstillinger** for din rapport.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Tilpas en visualisering":::

Aktivér **Tilpas visualiseringer** > **Gem**.

:::image type="content" source="media/power-bi-personalize-visuals/personalize-report-setting-service.png" alt-text="Tilpas en visualisering":::

## <a name="turn-the-feature-on-or-off-at-a-page-or-visual-level"></a>Slå funktionen til eller fra på et side- eller visualiseringsniveau

Når du aktiverer Tilpas visualiseringer for en given rapport, kan alle visualiseringer i denne rapport som standard tilpasses. Hvis du ikke ønsker, at alle visualiseringer skal kunne tilpasses, kan du slå indstillingen til eller fra for hver side eller visualisering.

### <a name="per-page"></a>Pr. side

Vælg fanen Side > vælg **Formatér** i ruden **Visualiseringer**.

:::image type="content" source="media/power-bi-personalize-visuals/personalize-page-level-setting.png" alt-text="Tilpas en visualisering":::
 
Slå skyderen for **Tilpas visualisering** >  **Til** eller **Fra**.

### <a name="per-visual"></a>Pr. visualisering

Vælg visualiseringen > vælg **Formatér** i ruden **Visualiseringer** > udvid **Overskrift i visualisering**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Tilpas en visualisering":::
 
Slå skyderen for **Tilpas visualisering** >  **Til** eller **Fra**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="Tilpas en visualisering":::


## <a name="limitations"></a>Begrænsninger

Der er i øjeblikket nogle få begrænsninger for funktionen, som du skal være opmærksom på.

- Denne funktion understøttes ikke til udgivelse på internettet.
- Brugerudforskninger bevares ikke automatisk. Du skal gemme din visning som et personligt bogmærke for at registrere dine ændringer.
- Denne funktion understøttes i Power BI-mobilapps til iOS- og Android-tablets og i Power BI Windows-appen. Den understøttes ikke i Power BI-mobilapps til telefoner. Ændringer af visualiseringer, som du gemmer som et personligt bogmærke, mens du er i Power BI-tjenesten, bevares i alle Power BI-mobilapps.

## <a name="next-steps"></a>Næste trin

[Tilpas visualiseringer i dine rapporter](../consumer/end-user-personalize-visuals.md).     

Prøv den nye funktionalitet til tilpasning af visualiseringer. Giv os din feedback på denne funktion, og hvordan vi fortsat kan forbedre den, på [webstedet med Power BI-ideer](https://ideas.powerbi.com/forums/265200-power-bi). 

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)