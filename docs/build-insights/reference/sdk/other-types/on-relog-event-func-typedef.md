---
title: OnRelogEventFunc (typedef)
description: Référence typedef OnRelogEventFunc du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ed639ab59b900f97d29dc69240e45b2f52f2f3b3
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919746"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc (typedef)

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

Le `OnRelogEventFunc` typedef est l’une des signatures de fonction utilisées dans la structure [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Paramètres

*eventStack*\
Pile d’événements pour l’événement actuel. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

*relogSession*\
Pointeur de session de rejournalisation à utiliser lors de l’appel de [InjectEvent](../functions/inject-event.md).

*callbackContext*\
Valeur de contexte qui a été définie pour ce rappel dans [RELOG_DESCRIPTOR](analysis-descriptor-struct.md).

### <a name="return-value"></a>Valeur de retour

Valeur [CALLBACK_CODE](callback-code-enum.md) qui contrôle ce qui doit se passer ensuite.

::: moniker-end
