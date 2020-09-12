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
ms.openlocfilehash: d64a23c603d1f30726f30ffc91c1889c51138ef6
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041703"
---
# <a name="function_force_inlinee_data-structure"></a>Structure FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

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
