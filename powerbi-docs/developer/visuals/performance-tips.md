---
title: Tip til ydeevne
description: Sådan får du høj ydeevne i en visualisering i Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: c22c634ef59a1aae2994dcacaae62dc8ebed7474
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746069"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Sådan får du høj ydeevne i en visualisering i Power BI
I denne artikel gennemgås teknikker til, hvordan en udvikler kan opnå høj ydeevne ved gengivelse af visualiseringer. 

Der er ingen, der ønsker, at det tager tid at vise en visualisering. Det gælder derfor om at få mest mulig ydeevne ud af koden under visningen. 

> [!NOTE]
> Efterhånden som vi fortsætter med at forbedre platformen, frigives der hele tiden nye versioner af API'en. Det anbefales, at du holder dig ajour med den nyeste version, for at du kan få mest muligt ud af platformen for visualiseringer i Power BI og funktionssættet.
>
> Indlæsningstiden for visualiseringer i Power BI er siden den nyeste **version 2.1** blevet forbedret med 20 % i gennemsnit.

## <a name="power-bi-visual-performance-tips"></a>Tip til visualiseringer i Power BI
Her er nogle anbefalinger til, hvordan du kan opnå optimal ydeevne for visualiseringer. 

### <a name="use-user-timing-api"></a>Benyt API til brugertiming
Hvis du bruger **API'en til brugertiming** til at måle din apps JavaScript-ydeevne, kan du få hjælp til at afgøre, hvilke dele af scriptet der kræver optimering.

Du kan finde flere oplysninger i [API til brugertiming](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Gennemse animationsløkker
Tegner animationsløkken elementer, der ikke er blevet ændret, igen? 

 - Problem: Det er spild af tid at tegne elementer, der ikke ændres fra billede til billede.

 - Løsning: Opdater billeder selektivt. 
 
Når tiden er inde til at animere statiske visualiseringer, er det fristende at samle tegnekode i én opdateringsfunktion og gentagne gange kalde den med nye data for hver gentagelse af animationsløkken.

Du kan i stedet overveje følgende opdateringsmønster, hvor du bruger en visualiseringskonstruktørmetode til at tegne alt, der er statisk, hvorefter opdateringsfunktionen kun skal tegne de visualiseringselementer, der ændres. 

   > [!TIP]
   > Ineffektive animationsløkker ses typisk i akser og forklaringer.

### <a name="cache-dom-nodes"></a>Cachelagring af DOM-noder 
Når en node eller en liste over noder hentes fra DOM'en, skal du overveje, om du kan bruge dem igen på et senere tidspunkt (måske endda i den næste gentagelse af løkken). Så længe du ikke har brug for at tilføje eller slette yderligere noder i det relevante område, kan cachelagring forbedre dit programs samlede effektivitet.

Hvis du vil sikre, at din kode er hurtig og ikke gør browseren langsom, skal du sørge for, at der er en minimumgrænse for DOM-adgangen. 

- Før: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Efter: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Undgå DOM-manipulationer 
Begræns DOM-manipulationer så meget som muligt.  Indsættelseshandlinger som `prepend()`, `append()` og `after()` er tidskrævende og bør ikke benyttes, medmindre det er nødvendigt.

F.eks.:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

Ovenstående eksempel kan gøres hurtigere ved hjælp af `html()` og ved at bygge listen på forhånd: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Overvej JQuery

Hvis du begrænser dine JS-strukturer og bruger oprindelig JS, når det er muligt, kan det øge den tilgængelige båndbredde og reducere behandlingsspild. Det kan også begrænse kompatibilitetsproblemer med ældre browsere. 

Se [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) for at få flere oplysninger og alternative eksempler til funktioner som JQuerys `show`, `hide`, `addClass` og meget mere.  

### <a name="use-canvas-or-webgl"></a>Brug lærred eller WebGL 
I forbindelse med gentagen brug af animationer bør du overveje at bruge **lærred** eller **WebGL** i stedet for SVG. I modsætning til SVG bestemmes ydeevnen i forhold til størrelsen i stedet for indhold med disse muligheder. 

Du kan læse mere om forskellene i [SVG vs. lærred: Sådan træffer du et valg](/previous-versions/windows/internet-explorer/ie-developer/samples/gg193983(v=vs.85)). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Brug requestAnimationFrame i stedet for setTimeout 
Hvis du bruger [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) til at opdatere dine animationer på skærmen, kaldes dine animationsfunktioner, **før** browseren kalder en anden gentegning.

Du kan finde flere oplysninger i dette [eksempel](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) på problemfri animationer ved hjælp af `requestAnimationFrame`.

## <a name="next-steps"></a>Næste trin

Få mere at vide om teknikker til optimering i [Optimeringsvejledning til Power BI](../../guidance/power-bi-optimization.md).