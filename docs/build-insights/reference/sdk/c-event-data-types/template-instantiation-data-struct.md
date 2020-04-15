---
title: structure TEMPLATE_INSTANTIATION_DATA
description: La référence de structure de construction SDK TEMPLATE_INSTANTIATION_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a38d19368e7c0a9912907f1da6e7a2e31ffe8d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325329"
---
# <a name="template_instantiation_data-structure"></a>structure TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `TEMPLATE_INSTANTIATION_DATA` structure décrit un modèle d’instantanéisation.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `SpecializationSymbolKey` | La clé pour le type de spécialisation du modèle. Cette valeur est unique dans la trace analysée. |
| `PrimaryTemplateSymbolKey` | La clé pour le type de modèle primaire qui était spécialisé. Cette valeur est unique dans la trace analysée. |
| `KindCode` | Le type d’instantanéisation du modèle. Pour plus d’informations, voir [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Notes

Les touches `TEMPLATE_INSTANTIATION_DATA` de la structure sont uniques dans la trace analysée. Cependant, deux touches différentes provenant de différentes passes avant compilateur peuvent indiquer deux types identiques. Lorsque `TEMPLATE_INSTANTIATION_DATA` vous consommez des informations provenant de plusieurs laissez-passer frontaux compilateur, utilisez les [SYMBOL_NAME](../event-table.md#symbol-name) événements pour déterminer si deux types sont les mêmes. `SymbolName`les événements sont émis à la fin d’un compilateur de passage front-end, après toutes les instantanés de modèle ont eu lieu.

::: moniker-end
