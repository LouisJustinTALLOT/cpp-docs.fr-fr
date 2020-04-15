---
title: OnAnalysisEventFunc typedef
description: La référence Dactylo SDK OnAnalysisEventFunc typedef.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eacd174279caff0db22586d5e40d3a866afc4459
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329130"
---
# <a name="onanalysiseventfunc-typedef"></a>OnAnalysisEventFunc typedef

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

Le `OnAnalysisEventFunc` tapdef est l’une des signatures de fonction utilisées dans la structure [ANALYSIS_CALLBACKS.](analysis-callbacks-struct.md)

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>Paramètres

*événementStack*\
La pile d’événements pour l’événement actuel. Pour plus d’informations sur les piles d’événements, voir [Événements](../event-table.md).

*callbackContext*\
La valeur contextuelle qui a été fixée pour ce rappel en [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Valeur de retour

Une [valeur CALLBACK_CODE](callback-code-enum.md) qui contrôle ce qui devrait se passer ensuite.

::: moniker-end
