---
title: OnRelogEventFunc (typedef)
description: Référence C++ typedef OnRelogEventFunc du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 619f9a142ad19a7809b867eda93f2db634825a8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332389"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc (typedef)

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

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
