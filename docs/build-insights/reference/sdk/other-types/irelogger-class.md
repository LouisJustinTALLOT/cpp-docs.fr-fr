---
title: IRelogger, classe
description: Référence C++ de la classe IRelogger du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0796cec3fe4ac6183279e8d8013a9550f18b61c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417431"
---
# <a name="irelogger-class"></a>IRelogger, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `IRelogger` fournit une interface pour le rejournalisation d’une trace Suivi d’v nements pour Windows (ETW). Elle est utilisée avec les fonctions [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) et [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Utilisez `IRelogger` comme classe de base pour créer votre propre journal qui peut faire partie d’un groupe de rejournalisation.

## <a name="syntax"></a>Syntaxe

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>Notes

La valeur de retour par défaut pour toutes les fonctions qui ne sont pas remplacées est `AnalysisControl::CONTINUE`. Pour plus d’informations, consultez [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Membres

### <a name="destructor"></a>Destructeur

[~ IRelogger](#irelogger-destructor)

### <a name="functions"></a>Fonctions

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger-destructor"></a>~ IRelogger

Détruit la classe IRelogger.

```cpp
virtual ~IRelogger();
```

## <a name="on-begin-relogging"></a>OnBeginRelogging

Cette fonction est appelée avant le début de la passe de reconnexion.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Cette fonction est appelée au début de la passe de reconnexion.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-end-relogging"></a>OnEndRelogging

Cette fonction est appelée une fois que la passe de reconnexion est terminée.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

Cette fonction est appelée à la fin de la passe de reconnexion.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Cette fonction est appelée lorsqu’un événement simple est traité.

### <a name="parameters"></a>Paramètres

*eventStack*\
Pile d’événements pour cet événement simple. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Cette fonction est appelée lorsqu’un événement de démarrage d’activité est en cours de traitement.

### <a name="parameters"></a>Paramètres

*eventStack*\
Pile d’événements pour cet événement de démarrage d’activité. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-stop-activity"></a>OnStopActivity

Cette fonction est appelée lorsqu’un événement d’arrêt d’activité est en cours de traitement.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Paramètres

*eventStack*\
Pile d’événements pour cet événement d’arrêt d’activité. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Cette fonction est appelée une fois au début de chaque passe d’analyse ou de reconnexion.

### <a name="parameters"></a>Paramètres

*traceInfo*\
Objet [TraceInfo](../cpp-event-data-types/trace-info.md) qui contient des propriétés utiles sur la trace en cours de consommation.

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

::: moniker-end
