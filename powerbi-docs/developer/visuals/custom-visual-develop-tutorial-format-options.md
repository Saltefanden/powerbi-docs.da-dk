---
title: Føj formateringsindstillinger til en brugerdefineret visual i Power BI
description: Et selvstudium i, hvordan du udvikler formateringsindstillinger for en brugerdefineret visual i Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 11/21/2018
ms.openlocfilehash: ec3ba601eb6cd5db4fbc19298d76ce0cd7346f53
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418733"
---
# <a name="tutorial-adding-formatting-options-to-a-power-bi-visual"></a>Selvstudium: Føj formateringsindstillinger til en visualisering i Power BI

I dette selvstudium gennemgås, hvordan du føjer almindelige egenskaber til din visualisering.

I dette selvstudium lærer du, hvordan du kan:
> [!div class="checklist"]
> * Tilføj egenskaber for visual.
> * Pak visualen.
> * Importér den brugerdefinerede visual til en rapport i Power BI Desktop.

## <a name="adding-formatting-options"></a>Tilføjelse af formateringsindstillinger

1. I **Power BI** skal du vælge **siden Formatér**.

    Du får vist en meddelelse med teksten – *Formateringsindstillinger er ikke tilgængelige for denne visual.*

    ![Formatering af malerullen](media/custom-visual-develop-tutorial-format-options/format-paintbrush.png)

2. I **Visual Studio Code** skal du åbne filen *capabilities.json*.

3. Før matrixen **dataViewMappings** skal du tilføje **objekter** (efter linje 8).

    ```json
    "objects": {},
    ```

    ![Tilføj objekter](media/custom-visual-develop-tutorial-format-options/add-objects.png)

4. Gem filen **capabilities.json**.

5. I **Power BI** skal du gennemse formateringsindstillingerne igen.

    > [!Note]
    > Hvis du ikke kan se ændringerne af formateringsindstillingerne, skal du vælge **Genindlæs brugerdefineret visual**.

    ![Se formateringsindstillinger](media/custom-visual-develop-tutorial-format-options/view-formatting-options.png)

6. Angiv indstillingen **Titel** til *Fra*. Bemærk, at visualen ikke længere viser navnet på målingen i øverste venstre hjørne.

    ![Indstillingen Felt er slået fra](media/custom-visual-develop-tutorial-format-options/tile-option-off.png)

    ![Feltet Intet navn](media/custom-visual-develop-tutorial-format-options/no-name-tile.png)

### <a name="adding-custom-formatting-options"></a>Tilføjelse af brugerdefinerede formateringsindstillinger

Du kan tilføje brugerdefinerede egenskaber for at gøre det muligt at konfigurere farven på cirklen og rammens bredde.

1. I PowerShell skal du standse den brugerdefinerede visual.

2. I Visual Studio Code skal du i filen **capabilities.json** indsætte følgende JSON-fragment i objektet kaldet **objects**.

    ```json
        {
            "circle": {
                "displayName": "Circle",
                "properties": {
                    "circleColor": {
                        "displayName": "Color",
                        "description": "The fill color of the circle.",
                        "type": {
                            "fill": {
                                "solid": {
                                    "color": true
                                }
                            }
                        }
                    },
                    "circleThickness": {
                        "displayName": "Thickness",
                        "description": "The circle thickness.",
                        "type": {
                            "numeric": true
                        }
                    }
                }
            }
        }
    ```

    JSON-fragmentet beskriver en cirkel med et gruppenavn, der består af to indstillinger med navnet circleColor og circleThickness.

   ![Kode for cirklens tykkelse](media/custom-visual-develop-tutorial-format-options/circle-thickness-code.png)

3. Gem filen **capabilities.json**.

4. I **ruden Stifinder** skal du gå til mappen **src** og derefter vælge **settings.ts**. *Denne fil repræsenterer indstillingerne for startvisualen*.

5. I filen **settings.ts** skal du erstatte de to klasser med følgende kode.

    ```typescript
    export class CircleSettings {
        public circleColor: string = "white";
        public circleThickness: number = 2;
    }
    export class VisualSettings extends DataViewObjectsParser {
        public circle: CircleSettings = new CircleSettings();
    }
    ```

    ![Modulklasser](media/custom-visual-develop-tutorial-format-options/module-classes.png)

    Dette modul definerer de to klasser. Klassen **CircleSettings** definerer to egenskaber med navne, der svarer til de objekter, som er defineret i filen **capabilities.json** (**circleColor** og  **circleThickness**), og angiver også standardværdier. Klassen **VisualSettings** arver klassen **DataViewObjectParser** og tilføjer en **cirkel** med et egenskabsnavn, der svarer til det objekt, som er defineret i filen  *capabilities.json*, og returnerer en instans af **CircleSettings**.

6. Gem filen **settings.ts**.

7. Åbn filen **visual.ts**.

8. Î filen **visual.ts**

    importér `VisualSettings`, `VisualObjectInstanceEnumeration` og `EnumerateVisualObjectInstancesOptions`:

    ```typescript
    import { VisualSettings } from "./settings";
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration;
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions;
    ```

    og i klassen **Visual** skal du tilføje følgende egenskab:

    ```typescript
    private visualSettings: VisualSettings;
    ```

    Denne egenskab gemmer en reference til objektet **VisualSettings**, der beskriver indstillingerne for visualen.

    ![Tilføj klasse med visuals](media/custom-visual-develop-tutorial-format-options/visual-class-add-on.png)

9. I klassen **Visual** skal du tilføje følgende metode før **opdaterings** metoden. Denne metode bruges til at udfylde formateringsindstillingerne.

    ```typescript
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        const settings: VisualSettings = this.visualSettings || <VisualSettings>VisualSettings.getDefault();
        return VisualSettings.enumerateObjectInstances(settings, options);
    }
    ```

    Denne metode bruges til at udfylde formateringsindstillingerne.

    ![Objekt for visualindstillinger](media/custom-visual-develop-tutorial-format-options/visual-settings-object.png)

10. I **opdaterings** metoden skal du tilføje følgende kode efter angivelsen af variablen **radius**.

    ```typescript
    this.visualSettings = VisualSettings.parse<VisualSettings>(dataView);

    this.visualSettings.circle.circleThickness = Math.max(0, this.visualSettings.circle.circleThickness);
    this.visualSettings.circle.circleThickness = Math.min(10, this.visualSettings.circle.circleThickness);
    ```

    Denne kode henter formateringsindstillingerne. Den justerer alle værdier, der er overført til egenskaben **circleThickness**, og konverterer dem til 0, hvis de er negative, eller 10, hvis de har en værdi, der er større end 10.

    ![Variablen Radius](media/custom-visual-develop-tutorial-format-options/radius.png)

11. I forbindelse med **cirkelelementet** skal du ændre den værdi, der overføres til **fyldtypografien**, til følgende udtryk.

    ```typescript
    this.visualSettings.circle.circleColor
    ```

    ![Udfylder cirkelelementet](media/custom-visual-develop-tutorial-format-options/circle-element-fill.png)

12. I forbindelse med **cirkelelementet** skal du ændre den værdi, der overføres til **typografien for penselstrøgsbredde**, til følgende udtryk.

    ```typescript
    this.visualSettings.circle.circleThickness
    ```

    ![Penselstrøgsbredde for cirkel](media/custom-visual-develop-tutorial-format-options/circle-stroke-width.png)

13. Gem filen visual.ts.

14. I PowerShell skal du starte visualen.

    ```powershell
    pbiviz start
    ```

15. På værktøjslinjen i **Power BI**, der flyder over visualen, skal du vælge **Slå automatisk genindlæsning til/fra**.

16. I indstillingerne for **formatering af visual** skal du udvide **Cirkel**.

    ![Cirkelformat](media/custom-visual-develop-tutorial-format-options/circle-format.png)

    Rediger indstillingen for **farve** og **tykkelse**.

    Rediger indstillingen for **tykkelse** til en værdi, der er mindre end nul, og en værdi, der er højere end 10. Læg derefter mærke til, at visualen opdaterer værdien til en acceptabel minimum- eller maksimumværdi.

## <a name="packaging-the-custom-visual"></a>Pak den brugerdefinerede visual

Angiv egenskabsværdier for projektet med det brugerdefinerede visual, opdater ikonfilen, og pak derefter den brugerdefinerede visual.

1. I **PowerShell** skal du standse den brugerdefinerede visual.

2. Åbn filen **pbiviz.json** i **Visual Studio Code**.

3. I objektet **visual** skal du ændre egenskaben **displayName** til *Circle Card*.

    I ruden **Visualiseringer** kan du se det viste navn, når du peger på ikonet.

    ![Visualen Vist navn](media/custom-visual-develop-tutorial-format-options/display-name-viz.png)

4. I forbindelse med egenskaben **description** skal du angive følgende tekst.

    *Viser en formateret målingsværdi i en cirkel*

5. Udfyld **supportUrl** og **gitHubUrl** for visualiseringen.

    Eksempel:

    ```json
    {
        "supportUrl": "https://community.powerbi.com",
        "gitHubUrl": "https://github.com/microsoft/PowerBI-visuals-circlecard"
    }
    ```

6. Angiv dine oplysninger under objektet **forfatter**.

7. Gem filen **pbiviz.json**.

8. I objektet **assets** kan du se, at dokumentet definerer en sti til et ikon. Ikonet er det billede, der vises i ruden **_Visualiseringer_** . Det skal være en **PNG**-fil, *20 pixel gange 20 pixel*.

9. I Windows Stifinder skal du kopiere icon.png-filen og derefter indsætte den for at erstatte standardfilen, der er placeret i mappen assets.

10. I ruden Stifinder i Visual Studio Code skal du udvide mappen assets og derefter vælge icon.png-filen.

11. Gennemse ikonet.

    ![Billede af ruden Visualiseringer](media/custom-visual-develop-tutorial-format-options/viz-pane-image.png)

12. I Visual Studio Code skal du sikre, at alle filer er gemt.

13. Angiv følgende kommando i PowerShell for at pakke den brugerdefinerede visual.

    ```powershell
    pbiviz package
    ```

    ![Mappen Dist](media/custom-visual-develop-tutorial-format-options/dist-folder.png)

Nu er pakken sendt til mappen **dist** i projektet. Pakken indeholder alt det, der kræves for at importere den brugerdefinerede visual til enten Power BI-tjenesten eller en rapport i Power BI Desktop. Du har nu pakket den brugerdefinerede visual, og den er klar til brug.

## <a name="importing-the-custom-visual"></a>Importér den brugerdefinerede visual

Du kan nu åbne rapporten i Power BI Desktop og importere den brugerdefinerede visual Circle Card.

1. Åbn **Power BI Desktop**, og opret en ny rapport med et hvilket som helst *eksempeldatasæt*

2. I ruden **_Visualiseringer_** skal du vælge **ellipsen** og derefter vælge **Importér** fra fil.

    ![Tilføj brugerdefineret visual på skrivebord](media/custom-visual-develop-tutorial-format-options/add-custom-viz-to-desktop.png)

3. I **importvinduet** skal du vælge **Importér**.

4. I vinduet Åbn skal du navigere til mappen **dist** i din projektmappe.

5. Vælg filen **circleCard.pbiviz**, og vælg derefter **Åbn**.

6. Når visualen er importeret, skal du vælge **OK**.

7. Kontrollér, at visualen er tilføjet i ruden **_Visualiseringer_** .

    ![Få vist i PBI Desktop-visualiseringsruden](media/custom-visual-develop-tutorial-format-options/view-in-desktop-viz-pane.png)

8. Peg på ikonet **Circle Card**, og læg mærke til det værktøjstip, der vises.

## <a name="debugging"></a>Fejlfinding

Se [fejlfindingsvejledningen](./visuals-how-to-debug.md#how-to-debug-power-bi-visuals) for tips til fejlfinding af et brugerdefineret visual.

## <a name="next-steps"></a>Næste trin

Du kan angive din nyligt udviklede visualisering, så andre kan bruge den, ved at sende den til **AppSource**. Du kan finde flere oplysninger om denne proces under [Publicer Power BI-visualiseringer i AppSource](office-store.md).
