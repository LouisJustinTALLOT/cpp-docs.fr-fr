---
title: Structure RELOG_DESCRIPTOR
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights RELOG_DESCRIPTOR.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6f20835ed6535dd05def629200c113772e8f077
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332326"
---
# <a name="relog_descriptor-structure"></a>Structure RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `RELOG_DESCRIPTOR` est utilisée avec les fonctions [RelogA](../functions/relog-a.md) et [RelogW](../functions/relog-w.md) . Il décrit la façon dont une trace de Suivi d’v nements pour Windows (ETW) doit être reconnectée.

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
| `NumberOfAnalysisPasses` | Nombre de passes d’analyse à effectuer sur la trace ETW pendant la phase d’analyse de la session de rejournalisation. |
| `AnalysisCallbacks` | Objet [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) qui spécifie les fonctions à appeler lors de la phase d’analyse de la session de rejournalisation. |
| `RelogCallbacks` | Objet [RELOG_CALLBACKS](relog-callbacks-struct.md) qui spécifie les fonctions à appeler pendant la phase de rejournalisation de la session de rejournalisation. |
| `SystemEventsRetentionFlags` | Masque de [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) qui spécifie les événements ETW du système à conserver dans le suivi reconnecté. |
| `AnalysisContext` | Contexte fourni par l’utilisateur qui est passé comme argument à toutes les fonctions de rappel spécifiées dans `AnalysisCallbacks` |
| `RelogContext` | Contexte fourni par l’utilisateur qui est passé comme argument à toutes les fonctions de rappel spécifiées dans `RelogCallbacks` |

## <a name="remarks"></a>Notes

La reconnexion des événements ETW pendant une session de rejournalisation est contrôlée par l’utilisateur via les fonctions de rappel spécifiées dans `RelogCallbacks`. Toutefois, les événements ETW du système tels que les exemples d’UC ne sont pas transférés à ces fonctions de rappel. Utilisez le champ `SystemEventsRetentionFlags` pour contrôler le rejournalisation des événements ETW du système.

Les structures `AnalysisCallbacks` et `RelogCallbacks` acceptent uniquement les pointeurs vers des fonctions non membres. Vous pouvez contourner cette limitation en les définissant sur un pointeur d’objet. Ce pointeur d’objet sera passé comme argument à toutes vos fonctions de rappel non-membre. Utilisez ce pointeur pour appeler des fonctions membres depuis vos fonctions de rappel non-membre.

La phase d’analyse d’une session de rejournalisation est toujours exécutée avant la phase de rejournalisation.

::: moniker-end
