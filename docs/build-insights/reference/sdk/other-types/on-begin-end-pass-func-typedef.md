---
title: OnBeginEndPassFunc (typedef)
description: Référence typedef OnBeginEndPassFunc du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a97ae792392e5cc0dc83bab00a92d05609a4815
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922494"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc (typedef)

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

Le `OnBeginEndPassFunc` typedef est l’une des signatures de fonction utilisées dans les structures [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) et [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnBeginEndPassFunc)(
    void*                           callbackContext);
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `callbackContext` |  |

::: moniker-end
