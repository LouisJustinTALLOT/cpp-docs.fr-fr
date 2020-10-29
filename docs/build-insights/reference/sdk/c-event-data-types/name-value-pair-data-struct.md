---
title: Structure NAME_VALUE_PAIR_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights NAME_VALUE_PAIR_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- NAME_VALUE_PAIR_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bab9f7ccedc4a94478d50863f2fae248722468e2
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923549"
---
# <a name="name_value_pair_data-structure"></a>Structure NAME_VALUE_PAIR_DATA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `NAME_VALUE_PAIR_DATA` structure décrit une paire nom/valeur.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct NAME_VALUE_PAIR_DATA_TAG
{
    const wchar_t*      Name;
    const wchar_t*      Value;
} NAME_VALUE_PAIR_DATA;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `Name` | Nom. |
| `Value` | La valeur. |

::: moniker-end
