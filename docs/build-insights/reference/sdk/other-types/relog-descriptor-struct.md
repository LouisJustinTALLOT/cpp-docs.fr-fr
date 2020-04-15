---
title: structure RELOG_DESCRIPTOR
description: La référence de structure de construction SDK RELOG_DESCRIPTOR de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c3aee49fe9f609ca37082693ddcfd5e838cc96a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328940"
---
# <a name="relog_descriptor-structure"></a>structure RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `RELOG_DESCRIPTOR` structure est utilisée avec les fonctions [RelogA](../functions/relog-a.md) et [RelogW.](../functions/relog-w.md) Il décrit comment une trace de traçage d’événements pour Windows (ETW) doit être relogged.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | Le nombre d’analyses qui devraient être effectuées au-dessus de la trace etw pendant la phase d’analyse de la session de réinquage. |
| `AnalysisCallbacks` | Un [objet ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) qui précise les fonctions à appeler pendant la phase d’analyse de la session de réindage. |
| `RelogCallbacks` | Un [objet RELOG_CALLBACKS](relog-callbacks-struct.md) qui spécifie les fonctions à appeler pendant la phase de rélogging de la session de rélogging. |
| `SystemEventsRetentionFlags` | Un [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) le bitmask qui spécifie quels événements ETW système à garder dans la trace relogged. |
| `AnalysisContext` | Un contexte fourni par l’utilisateur qui est adopté comme argument à toutes les fonctions de rappel spécifiées dans`AnalysisCallbacks` |
| `RelogContext` | Un contexte fourni par l’utilisateur qui est adopté comme argument à toutes les fonctions de rappel spécifiées dans`RelogCallbacks` |

## <a name="remarks"></a>Notes

Le relogging des événements ETW au cours d’une session de relogging `RelogCallbacks`est contrôlé par l’utilisateur à travers les fonctions de rappel spécifiées dans . Cependant, les événements ETW système tels que les échantillons de processeur ne sont pas transmis à ces fonctions de rappel. Utilisez `SystemEventsRetentionFlags` le champ pour contrôler le réenquage des événements ETW système.

Les `AnalysisCallbacks` `RelogCallbacks` structures et les structures n’acceptent que les indications aux fonctions non membres. Vous pouvez contourner cette limitation en les fixant à un pointeur d’objet. Ce pointeur d’objet sera passé comme argument à toutes vos fonctions de rappel non-membres. Utilisez ce pointeur pour appeler les fonctions des membres à partir de vos fonctions de rappel non membres.

La phase d’analyse d’une session de relogging est toujours exécutée avant la phase de rélogging.

::: moniker-end
