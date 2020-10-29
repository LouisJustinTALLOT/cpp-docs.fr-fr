---
title: OnTraceInfoFunc (typedef)
description: Référence typedef OnTraceInfoFunc du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4aaa865fd0f907a67179e7ee967f23a9827b0026
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922459"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc (typedef)

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

Le `OnTraceInfoFunc` typedef est l’une des signatures de fonction utilisées dans les structures [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) et [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Paramètres

*traceInfo*\
Objet [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) qui contient des informations sur la trace en cours d’analyse ou de retardement.

*callbackContext*\
Valeur de contexte qui a été définie pour ce rappel dans [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Valeur de retour

Valeur [CALLBACK_CODE](callback-code-enum.md) qui contrôle ce qui doit se passer ensuite.

::: moniker-end
