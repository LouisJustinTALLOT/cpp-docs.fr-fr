---
title: Structure TEMPLATE_INSTANTIATION_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights TEMPLATE_INSTANTIATION_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa669d715dbe56ce7e889330f46f307f520710f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333621"
---
# <a name="template_instantiation_data-structure"></a>Structure TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `TEMPLATE_INSTANTIATION_DATA` décrit une instanciation de modèle.

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
| `SpecializationSymbolKey` | Clé pour le type de la spécialisation de modèle. Cette valeur est unique au sein de la trace en cours d’analyse. |
| `PrimaryTemplateSymbolKey` | Clé pour le type de modèle principal qui était spécialisé. Cette valeur est unique au sein de la trace en cours d’analyse. |
| `KindCode` | Type de l’instanciation du modèle. Pour plus d’informations, consultez [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Notes

Les clés de la structure `TEMPLATE_INSTANTIATION_DATA` sont uniques au sein de la trace en cours d’analyse. Toutefois, deux clés différentes provenant de différentes passes front-end du compilateur peuvent pointer vers deux types identiques. Lors de l’utilisation d’informations `TEMPLATE_INSTANTIATION_DATA` à partir de plusieurs passes front-end du compilateur, utilisez les événements [SYMBOL_NAME](../event-table.md#symbol-name) pour déterminer si deux types sont identiques. les événements `SymbolName` sont émis à la fin d’une passe frontale du compilateur, une fois que toutes les instanciations de modèle ont eu lieu.

::: moniker-end
