---
title: structure SYMBOL_NAME_DATA
description: La référence de structure de construction SDK SYMBOL_NAME_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1217572f20a772fde629533d6ab170c14dc5b5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325338"
---
# <a name="symbol_name_data-structure"></a>structure SYMBOL_NAME_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `SYMBOL_NAME_DATA` structure décrit un symbole frontal compilateur.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `Key` | La clé du symbole. Cette valeur est unique dans la trace analysée. |
| `Name` | Le nom du symbole. |

## <a name="remarks"></a>Notes

Les symboles provenant de deux différents cols avant compilateur peuvent avoir le même nom, mais une touche différente. Dans ce cas, utilisez des noms de symboles pour déterminer si deux types sont les mêmes.

::: moniker-end
