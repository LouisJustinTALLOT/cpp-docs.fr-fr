---
title: OnBeginEndPassFunc (typedef)
description: Référence C++ typedef OnBeginEndPassFunc du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6f5e602fdc460acf8e53307e88a1a3d7ad000893
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332424"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc (typedef)

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Le `OnBeginEndPassFunc` typedef est l’une des signatures de fonction utilisées dans les structures [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) et [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnBeginEndPassFunc)(
    void*                           callbackContext);
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `callbackContext` |  |

::: moniker-end
