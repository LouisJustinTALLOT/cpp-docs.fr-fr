---
title: Structure SYMBOL_NAME_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights SYMBOL_NAME_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d234c6c225eff87a0eecd98fa5ff60bf92db97f5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041911"
---
# <a name="symbol_name_data-structure"></a>Structure SYMBOL_NAME_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `SYMBOL_NAME_DATA` structure décrit un symbole de compilateur frontal.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `Key` | Clé du symbole. Cette valeur est unique au sein de la trace en cours d’analyse. |
| `Name` | Nom du symbole. |

## <a name="remarks"></a>Remarques

Les symboles provenant de deux passes front-end de compilateur différents peuvent avoir le même nom mais une clé différente. Dans ce cas, utilisez des noms de symboles pour déterminer si deux types sont identiques.

::: moniker-end
