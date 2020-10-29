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
ms.openlocfilehash: 17daaa6feb784c501d180a982cd4ad2b405ccf67
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921085"
---
# <a name="event_collection_data-structure"></a>Structure EVENT_COLLECTION_DATA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

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
