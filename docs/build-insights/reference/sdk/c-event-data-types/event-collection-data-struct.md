---
title: structure EVENT_COLLECTION_DATA
description: La référence de structure de construction SDK EVENT_COLLECTION_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 88ba39ede8c86f47c2e6458332ae005eddc06fda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325690"
---
# <a name="event_collection_data-structure"></a>structure EVENT_COLLECTION_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `EVENT_COLLECTION_DATA` structure décrit un éventail d’éléments [EVENT_DATA.](event-data-struct.md)

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
| `Count` | Le nombre `EVENT_DATA` d’éléments dans le tableau. |
| `Elements` | Pointeur vers `EVENT_DATA` le premier élément du tableau. |

::: moniker-end
