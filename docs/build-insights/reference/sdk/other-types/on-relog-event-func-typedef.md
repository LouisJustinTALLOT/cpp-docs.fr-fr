---
title: OnRelogEventFunc typéef
description: La référence Dactylo SDK OnRelogEventFunc typedef.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2df8646d530c089b1239978d716b2b619a5b4b61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329067"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc typéef

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

Le `OnRelogEventFunc` tapdef est l’une des signatures de fonction utilisées dans la structure [RELOG_CALLBACKS.](relog-callbacks-struct.md)

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Paramètres

*événementStack*\
La pile d’événements pour l’événement actuel. Pour plus d’informations sur les piles d’événements, voir [Événements](../event-table.md).

*relogSession*\
Le pointeur de session de relogging à utiliser lors de l’appel de [l’InjectEvent](../functions/inject-event.md).

*callbackContext*\
La valeur contextuelle qui a été fixée pour ce rappel en [RELOG_DESCRIPTOR](analysis-descriptor-struct.md).

### <a name="return-value"></a>Valeur de retour

Une [valeur CALLBACK_CODE](callback-code-enum.md) qui contrôle ce qui devrait se passer ensuite.

::: moniker-end
