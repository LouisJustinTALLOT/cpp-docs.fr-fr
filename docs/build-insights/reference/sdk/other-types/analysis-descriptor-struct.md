---
title: Structure ANALYSIS_DESCRIPTOR
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights ANALYSIS_DESCRIPTOR.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fc11ce11e1faaae02edb36aac447c18ea8107e35
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332480"
---
# <a name="analysis_descriptor-structure"></a>Structure ANALYSIS_DESCRIPTOR

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `ANALYSIS_DESCRIPTOR` est utilisée avec les fonctions [analyze](../functions/analyze-a.md) et [AnalyzeW](../functions/analyze-w.md) . Il décrit comment une trace Suivi d’v nements pour Windows (ETW) doit être analysée.

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
| `NumberOfPasses` | Nombre de passes d’analyse à effectuer sur la trace ETW. |
| `Callbacks` | Objet [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) qui spécifie les fonctions à appeler pendant la session d’analyse. |
| `Context` | Contexte fourni par l’utilisateur qui est passé comme argument à toutes les fonctions de rappel spécifiées dans `Callbacks` |

## <a name="remarks"></a>Notes

La structure `Callbacks` accepte uniquement les pointeurs vers des fonctions non membres. Vous pouvez contourner cette limitation en affectant à `Context` un pointeur d’objet. Ce pointeur d’objet sera passé comme argument à toutes vos fonctions de rappel non-membre. Utilisez ce pointeur pour appeler des fonctions membres depuis vos fonctions de rappel non-membre.

::: moniker-end
