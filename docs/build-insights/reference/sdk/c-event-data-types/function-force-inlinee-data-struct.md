---
title: Structure FUNCTION_FORCE_INLINEE_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights FUNCTION_FORCE_INLINEE_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3d6929f2f16e9b1bd79b7fb8b383b40e031268bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333698"
---
# <a name="function_force_inlinee_data-structure"></a>Structure FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `FUNCTION_FORCE_INLINEE_DATA` décrit une fonction forcée.

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
| `Name` | Nom de la fonction, encodé au format UTF-8. |
| `Size` | Taille de la fonction, sous la forme d’un nombre d’instructions intermédiaires. |

::: moniker-end
