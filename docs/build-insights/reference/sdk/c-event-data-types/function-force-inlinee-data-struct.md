---
title: Structure FUNCTION_FORCE_INLINEE_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights FUNCTION_FORCE_INLINEE_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e9de87bdc4e5a1a3e25483f8ba1766609c7d7622
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923570"
---
# <a name="function_force_inlinee_data-structure"></a>Structure FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `FUNCTION_FORCE_INLINEE_DATA` structure décrit une fonction forcée.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `Name` | Nom de la fonction, encodé au format UTF-8. |
| `Size` | Taille de la fonction, sous la forme d’un nombre d’instructions intermédiaires. |

::: moniker-end
