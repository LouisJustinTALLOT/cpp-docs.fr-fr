---
title: Structure EVENT_COLLECTION_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights EVENT_COLLECTION_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 58be46d31af154bfe7ecef5c440092eaafdcbb0f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039597"
---
# <a name="event_collection_data-structure"></a>Structure EVENT_COLLECTION_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `EVENT_COLLECTION_DATA` structure décrit un tableau d’éléments [EVENT_DATA](event-data-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `Count` | Nombre d' `EVENT_DATA` éléments dans le tableau. |
| `Elements` | Pointeur vers le premier `EVENT_DATA` élément du tableau. |

::: moniker-end
