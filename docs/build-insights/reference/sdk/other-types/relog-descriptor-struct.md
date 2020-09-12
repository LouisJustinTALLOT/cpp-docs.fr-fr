---
title: Structure RELOG_DESCRIPTOR
description: Le kit de développement logiciel (SDK) C++ Build Insights RELOG_DESCRIPTOR référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 802e51ec4246f5ee95e3d204290743ffbd03be69
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041391"
---
# <a name="relog_descriptor-structure"></a>Structure RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `RELOG_DESCRIPTOR` structure est utilisée avec les fonctions [RelogA](../functions/relog-a.md) et [RelogW](../functions/relog-w.md) . Il décrit la façon dont une trace de Suivi d’v nements pour Windows (ETW) doit être reconnectée.

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

| Nom | Description |
|--|--|
| `NumberOfAnalysisPasses` | Nombre de passes d’analyse à effectuer sur la trace ETW pendant la phase d’analyse de la session de rejournalisation. |
| `AnalysisCallbacks` | Objet [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) qui spécifie les fonctions à appeler lors de la phase d’analyse de la session de rejournalisation. |
| `RelogCallbacks` | Objet [RELOG_CALLBACKS](relog-callbacks-struct.md) qui spécifie les fonctions à appeler pendant la phase de rejournalisation de la session de rejournalisation. |
| `SystemEventsRetentionFlags` | Masque de [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) qui spécifie les événements ETW du système à conserver dans le suivi reconnecté. |
| `AnalysisContext` | Contexte fourni par l’utilisateur qui est passé comme argument à toutes les fonctions de rappel spécifiées dans `AnalysisCallbacks` |
| `RelogContext` | Contexte fourni par l’utilisateur qui est passé comme argument à toutes les fonctions de rappel spécifiées dans `RelogCallbacks` |

## <a name="remarks"></a>Remarques

La reconnexion des événements ETW pendant une session de rejournalisation est contrôlée par l’utilisateur via les fonctions de rappel spécifiées dans `RelogCallbacks` . Toutefois, les événements ETW du système tels que les exemples d’UC ne sont pas transférés à ces fonctions de rappel. Utilisez le `SystemEventsRetentionFlags` champ pour contrôler le rejournalisation des événements ETW du système.

Les `AnalysisCallbacks` `RelogCallbacks` structures et acceptent uniquement les pointeurs vers des fonctions non membres. Vous pouvez contourner cette limitation en les définissant sur un pointeur d’objet. Ce pointeur d’objet sera passé comme argument à toutes vos fonctions de rappel non-membre. Utilisez ce pointeur pour appeler des fonctions membres depuis vos fonctions de rappel non-membre.

La phase d’analyse d’une session de rejournalisation est toujours exécutée avant la phase de rejournalisation.

::: moniker-end
