---
title: Structure ANALYSIS_DESCRIPTOR
description: Le kit de développement logiciel (SDK) C++ Build Insights ANALYSIS_DESCRIPTOR référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec2d0a76618d6ff2cf0e7fdff7e360a4fd2e0174
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919850"
---
# <a name="analysis_descriptor-structure"></a>Structure ANALYSIS_DESCRIPTOR

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `ANALYSIS_DESCRIPTOR` structure est utilisée avec les fonctions [analyze](../functions/analyze-a.md) et [AnalyzeW](../functions/analyze-w.md) . Il décrit comment une trace Suivi d’v nements pour Windows (ETW) doit être analysée.

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

| Nom | Description |
|--|--|
| `NumberOfPasses` | Nombre de passes d’analyse à effectuer sur la trace ETW. |
| `Callbacks` | Objet [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) qui spécifie les fonctions à appeler pendant la session d’analyse. |
| `Context` | Contexte fourni par l’utilisateur qui est passé comme argument à toutes les fonctions de rappel spécifiées dans `Callbacks` |

## <a name="remarks"></a>Notes

La `Callbacks` structure accepte uniquement les pointeurs vers des fonctions non membres. Vous pouvez contourner cette limitation en définissant `Context` sur un pointeur d’objet. Ce pointeur d’objet sera passé comme argument à toutes vos fonctions de rappel non-membre. Utilisez ce pointeur pour appeler des fonctions membres depuis vos fonctions de rappel non-membre.

::: moniker-end
