---
title: Structure TEMPLATE_INSTANTIATION_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights TEMPLATE_INSTANTIATION_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 15bbb25c3abac339201179e763bffd916dba0480
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040871"
---
# <a name="template_instantiation_data-structure"></a>Structure TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `TEMPLATE_INSTANTIATION_DATA` structure décrit une instanciation de modèle.

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

| Nom | Description |
|--|--|
| `SpecializationSymbolKey` | Clé pour le type de la spécialisation de modèle. Cette valeur est unique au sein de la trace en cours d’analyse. |
| `PrimaryTemplateSymbolKey` | Clé pour le type de modèle principal qui était spécialisé. Cette valeur est unique au sein de la trace en cours d’analyse. |
| `KindCode` | Type de l’instanciation du modèle. Pour plus d’informations, consultez [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Remarques

Les clés de la `TEMPLATE_INSTANTIATION_DATA` structure sont uniques au sein de la trace en cours d’analyse. Toutefois, deux clés différentes provenant de différentes passes front-end du compilateur peuvent pointer vers deux types identiques. Lorsque vous consommez `TEMPLATE_INSTANTIATION_DATA` des informations à partir de plusieurs passes front-end du compilateur, utilisez les événements [SYMBOL_NAME](../event-table.md#symbol-name) pour déterminer si deux types sont identiques. `SymbolName` les événements sont émis à la fin d’une passe frontale du compilateur, une fois que toutes les instanciations de modèle ont eu lieu.

::: moniker-end
