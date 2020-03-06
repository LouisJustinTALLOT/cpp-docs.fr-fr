---
title: Structure EVENT_COLLECTION_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights EVENT_COLLECTION_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1a622a8459b6aa6d9dcbe0faaf90ae545b449466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333810"
---
# <a name="event_collection_data-structure"></a>Structure EVENT_COLLECTION_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `EVENT_COLLECTION_DATA` décrit un tableau d’éléments [EVENT_DATA](event-data-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `Count` | Nombre d’éléments `EVENT_DATA` dans le tableau. |
| `Elements` | Pointeur vers le premier élément `EVENT_DATA` dans le tableau. |

::: moniker-end
