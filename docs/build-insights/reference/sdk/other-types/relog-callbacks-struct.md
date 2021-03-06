---
title: Structure RELOG_CALLBACKS
description: Le kit de développement logiciel (SDK) C++ Build Insights RELOG_CALLBACKS référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b3beb656aa72ce4c8519c56c4c8bf6ca6577cf4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919797"
---
# <a name="relog_callbacks-structure"></a>Structure RELOG_CALLBACKS

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `RELOG_CALLBACKS` structure est utilisée lors de l’initialisation d’un objet [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Elle spécifie les fonctions à appeler lors de la reconnexion d’une trace de Suivi d’v nements pour Windows (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `OnStartActivity` | Appelé pour traiter un événement de début d’activité. |
| `OnStopActivity` | Appelé pour traiter un événement d’arrêt d’activité. |
| `OnSimpleEvent` | Appelée pour traiter un événement simple. |
| `OnTraceInfo` | Appelée une fois au début de la passe de rejournalisation, après que `OnBeginReloggingPass` a été appelé. |
| `OnBeginRelogging` | Appelé lors du démarrage d’une session de rejournalisation, avant que la passe de reconnexion ait commencé. |
| `OnEndRelogging` | Appelée lors de la fin d’une session de rejournalisation, une fois la passe de reconnexion terminée. |
| `OnBeginReloggingPass` | Appelée au début de la passe de reconnexion, avant le traitement d’un événement. |
| `OnEndReloggingPass` | Appelée à la fin de la passe de reconnexion, après le traitement de tous les événements. |

## <a name="remarks"></a>Notes

Tous les membres de la `RELOG_CALLBACKS` structure doivent pointer vers une fonction valide. Pour plus d’informations sur les signatures de fonction acceptées, consultez [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)et [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
