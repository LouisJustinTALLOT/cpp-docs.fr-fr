---
title: OnBeginEndPassFunc typedef
description: La référence Dactylo SDK OnBeginEndPassFunc typécef.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3b3fc453245a47463c29ceeb30dfdc48c79aef35
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329084"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc typedef

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

Le `OnBeginEndPassFunc` tapdef est l’une des signatures de fonction utilisées dans les structures [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) et [RELOG_CALLBACKS.](relog-callbacks-struct.md)

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
