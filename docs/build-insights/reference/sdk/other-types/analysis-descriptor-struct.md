---
title: structure ANALYSIS_DESCRIPTOR
description: La référence de structure de construction SDK ANALYSIS_DESCRIPTOR de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1de7f2a5bc3f02a327daaecf8c2cebc44687ba43
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323612"
---
# <a name="analysis_descriptor-structure"></a>structure ANALYSIS_DESCRIPTOR

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `ANALYSIS_DESCRIPTOR` structure est utilisée avec les fonctions [AnalyzeA](../functions/analyze-a.md) et [AnalyzeW.](../functions/analyze-w.md) Il décrit comment une trace de traçage d’événements pour Windows (ETW) doit être analysée.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `NumberOfPasses` | Le nombre d’analyses qui devrait être effectuée sur la trace et l’ETW. |
| `Callbacks` | Un [objet ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) qui précise les fonctions à appeler pendant la session d’analyse. |
| `Context` | Un contexte fourni par l’utilisateur qui est adopté comme argument à toutes les fonctions de rappel spécifiées dans`Callbacks` |

## <a name="remarks"></a>Notes

La `Callbacks` structure n’accepte que les indications des fonctions non membres. Vous pouvez contourner cette `Context` limitation en définissant un pointeur d’objet. Ce pointeur d’objet sera passé comme argument à toutes vos fonctions de rappel non-membres. Utilisez ce pointeur pour appeler les fonctions des membres à partir de vos fonctions de rappel non membres.

::: moniker-end
