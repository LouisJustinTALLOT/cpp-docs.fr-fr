---
title: OnAnalysisEventFunc (typedef)
description: Référence typedef OnAnalysisEventFunc du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 069c89a01fa466e86986a821e5dd9d0b09f5c81a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919785"
---
# <a name="onanalysiseventfunc-typedef"></a>OnAnalysisEventFunc (typedef)

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

Le `OnAnalysisEventFunc` typedef est l’une des signatures de fonction utilisées dans la structure [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>Paramètres

*eventStack*\
Pile d’événements pour l’événement actuel. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

*callbackContext*\
Valeur de contexte qui a été définie pour ce rappel dans [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Valeur de retour

Valeur [CALLBACK_CODE](callback-code-enum.md) qui contrôle ce qui doit se passer ensuite.

::: moniker-end
