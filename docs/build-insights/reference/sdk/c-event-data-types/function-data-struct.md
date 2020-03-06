---
title: Structure FUNCTION_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights FUNCTION_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 718e93bed798786a4596ccb3e724b2b54d4fe79d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333733"
---
# <a name="function_data-structure"></a>Structure FUNCTION_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `FUNCTION_DATA` décrit une fonction.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FUNCTION_DATA_TAG
{
    const char*         Name;

} FUNCTION_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `Name` | Nom de la fonction, encodé au format UTF-8. |

::: moniker-end
