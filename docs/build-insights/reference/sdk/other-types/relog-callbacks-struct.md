---
title: Structure RELOG_CALLBACKS
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights RELOG_CALLBACKS.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5dbed196e6cafaa301b6e07cd0f5546a0f4d563
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332340"
---
# <a name="relog_callbacks-structure"></a>Structure RELOG_CALLBACKS

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `RELOG_CALLBACKS` est utilisée lors de l’initialisation d’un objet [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Elle spécifie les fonctions à appeler lors de la reconnexion d’une trace de Suivi d’v nements pour Windows (ETW).

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

|  |  |
|--|--|
| `OnStartActivity` | Appelé pour traiter un événement de début d’activité. |
| `OnStopActivity` | Appelé pour traiter un événement d’arrêt d’activité. |
| `OnSimpleEvent` | Appelée pour traiter un événement simple. |
| `OnTraceInfo` | Appelée une fois au début de la passe de rejournalisation, après l’appel de `OnBeginReloggingPass`. |
| `OnBeginRelogging` | Appelé lors du démarrage d’une session de rejournalisation, avant que la passe de reconnexion ait commencé. |
| `OnEndRelogging` | Appelée lors de la fin d’une session de rejournalisation, une fois la passe de reconnexion terminée. |
| `OnBeginReloggingPass` | Appelée au début de la passe de reconnexion, avant le traitement d’un événement. |
| `OnEndReloggingPass` | Appelée à la fin de la passe de reconnexion, après le traitement de tous les événements. |

## <a name="remarks"></a>Notes

Tous les membres de la structure `RELOG_CALLBACKS` doivent pointer vers une fonction valide. Pour plus d’informations sur les signatures de fonction acceptées, consultez [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)et [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
