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
ms.openlocfilehash: c92fbd8ee7e1fff702757d003ab3bbe0bdabd886
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923442"
---
# <a name="template_instantiation_data-structure"></a>Structure TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

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

## <a name="remarks"></a>Notes

Les clés de la `TEMPLATE_INSTANTIATION_DATA` structure sont uniques au sein de la trace en cours d’analyse. Toutefois, deux clés différentes provenant de différentes passes front-end du compilateur peuvent pointer vers deux types identiques. Lorsque vous consommez `TEMPLATE_INSTANTIATION_DATA` des informations à partir de plusieurs passes front-end du compilateur, utilisez les événements [SYMBOL_NAME](../event-table.md#symbol-name) pour déterminer si deux types sont identiques. `SymbolName` les événements sont émis à la fin d’une passe frontale du compilateur, une fois que toutes les instanciations de modèle ont eu lieu.

::: moniker-end
