---
title: OnTraceInfoFunc (typedef)
description: Référence C++ typedef OnTraceInfoFunc du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b168d6783b31454f6a2837bcad1fc81199ce9054
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332347"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc (typedef)

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

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
