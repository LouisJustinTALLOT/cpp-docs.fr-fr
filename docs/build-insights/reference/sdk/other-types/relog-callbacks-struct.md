---
title: structure RELOG_CALLBACKS
description: La référence de structure de construction SDK RELOG_CALLBACKS de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 60e7db81a48731090a23b82332704a79a51e97df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328971"
---
# <a name="relog_callbacks-structure"></a>structure RELOG_CALLBACKS

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `RELOG_CALLBACKS` structure est utilisée lors de l’initialisation [d’un objet RELOG_DESCRIPTOR.](relog-descriptor-struct.md) Il précise quelles fonctions appeler lors de la rélogging d’un event Tracing for Windows (ETW) trace.

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
| `OnStartActivity` | Appelé à traiter un événement de début d’activité. |
| `OnStopActivity` | Appelé à traiter un événement d’arrêt d’activité. |
| `OnSimpleEvent` | Appelé à traiter un événement simple. |
| `OnTraceInfo` | Appelé une fois au début du passage `OnBeginReloggingPass` de rélogging, après a été appelé. |
| `OnBeginRelogging` | Appelé lors du début d’une session de relogging, avant le passage de rélogging a commencé. |
| `OnEndRelogging` | Appelé à la fin d’une session de relogging, après la passe de relogging a pris fin. |
| `OnBeginReloggingPass` | Appelé au début du passage de rélogging, avant de traiter tout événement. |
| `OnEndReloggingPass` | Appelé lors de la fin de la passe de rélogging, après le traitement de tous les événements. |

## <a name="remarks"></a>Notes

Tous les `RELOG_CALLBACKS` membres de la structure doivent indiquer une fonction valide. Pour plus d’informations sur les signatures de fonction acceptées, voir [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md), et [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
