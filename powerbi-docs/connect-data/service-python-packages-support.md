---
title: Få mere at vide om, hvilke Python-pakker der understøttes
description: Python-pakker, der understøttes og ikke understøttes i Power BI
author: otarb
ms.author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 06/26/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: d3a30098b793ccb75cbae6c271ab1685b3176a10
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2021
ms.locfileid: "99616944"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Opret visuals ved hjælp af Python-pakker i Power BI-tjenesten
Du kan bruge det effektive [Python-programmeringssprog](https://www.python.org/) til at skabe visuals i Power BI-tjenesten. Mange Python-pakker understøttes i Power BI-tjenesten, og der understøttes hele tiden flere og flere.

De følgende afsnit indeholder en alfabetisk tabel over de Python-pakker, der understøttes i Power BI. 

## <a name="request-support-for-a-new-python-package"></a>Anmod om at få understøttet en ny Python-pakke
De Python-pakker, der understøttes i **Power BI-tjenesten**, står i følgende afsnit med titlen **Understøttede pakker**. Hvis du vil anmode om at få understøttet en Python-pakke, der ikke findes på denne liste, kan du sende din anmodning til [Ideer til Power BI](https://ideas.powerbi.com).

## <a name="requirements-and-limitations-of-python-packages"></a>Python-pakkers krav og begrænsninger
Der er en række krav og begrænsninger for Python-pakker:

* Aktuel Python-kørsel: Python 3.7.7.
* Power BI-tjenesten understøtter i de fleste tilfælde Python-pakker med gratis og open source-softwarelicenser, f.eks. GPL-2, GPL-3, MIT+ osv.
* Power BI-tjenesten understøtter pakker, der er publiceret i PyPI. Tjenesten understøtter ikke private eller brugerdefinerede Python-pakker. Brugerne opfordres til at gøre deres private pakker tilgængelige på PyPI, før de anmoder om, at pakken gøres tilgængelig i Power BI-tjenesten.
* Du kan installere en hvilken som helst pakke for Python-visuals i **Power BI Desktop**, herunder brugerdefinerede Python-pakker.
* Python-pakker, der leverer klient-/serverforespørgsler via internettet i tjenesten, understøttes ikke af hensyn til sikkerheden og beskyttelse af personlige oplysninger. Brug af netværk er blokeret for denne type forsøg.
* Godkendelsesprocessen for at medtage en ny Python-pakke har et træ af afhængigheder. Nogle afhængigheder, der skal være installeret i tjenesten, kan ikke understøttes.

## <a name="python-packages-that-are-supported-in-power-bi"></a>Python-pakker, der understøttes i Power BI
Du kan se de pakker, der **understøttes** i Power BI-tjenesten i følgende tabel.


|        Pakke        |   Version   |                                   Link                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|seaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>Næste trin
Kig på følgende artikler for at få flere oplysninger om Python i Power BI:

* [Opret Power BI-visuals med Python](desktop-python-visuals.md)
* [Kørsel af Python-scripts i Power BI Desktop](desktop-python-scripts.md)
* [Brug af Python i Query-editor](desktop-python-in-query-editor.md)
