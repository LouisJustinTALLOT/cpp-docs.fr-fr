---
title: structure FUNCTION_FORCE_INLINEE_DATA
description: La référence de structure de construction SDK FUNCTION_FORCE_INLINEE_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a4781c9157130cb46e92906017af98710f5637b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325496"
---
# <a name="function_force_inlinee_data-structure"></a>structure FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `FUNCTION_FORCE_INLINEE_DATA` structure décrit une fonction inlinée par la force.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `Name` | Le nom de la fonction, codé dans UTF-8. |
| `Size` | La taille de la fonction, comme un certain nombre d’instructions intermédiaires. |

::: moniker-end
