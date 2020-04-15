---
title: Classe IRelogger
description: La référence de classe CMD Build Insights SDK IRelogger.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146377b2b44df43ed4b2f749efd9fb614a2a09c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329154"
---
# <a name="irelogger-class"></a>Classe IRelogger

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `IRelogger` classe fournit une interface pour rélogging une trace de traçage d’événements pour Windows (ETW). Il est utilisé avec les fonctions [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) et [MakeStaticReloggerGroup.](../functions/make-static-analyzer-group.md) Utilisez `IRelogger` comme classe de base pour créer votre propre relogger qui peut faire partie d’un groupe de relogger.

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

La valeur de retour par défaut pour toutes `AnalysisControl::CONTINUE`les fonctions qui ne sont pas remplacées est . Pour plus d’informations, voir [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Membres

### <a name="destructor"></a>Destructeur

[IRelogger](#irelogger-destructor)

### <a name="functions"></a>Fonctions

[OnBeginRelogging](#on-begin-relogging)\
[SurBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity (en)](#on-start-activity)\
[OnStopActivité](#on-stop-activity)\
[SurTraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a>IRelogger

Détruit la classe IRelogger.

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging

Cette fonction est appelée avant le passage de rélogging commence.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>SurBeginReloggingPass

Cette fonction est appelée au début du passage de rélogging.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>OnEndRelogging

Cette fonction est appelée après la fin du laissez-passer de rélogging.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass

Cette fonction est appelée à la fin du passage de rélogging.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Cette fonction est appelée lorsqu’un simple événement est en cours de traitement.

### <a name="parameters"></a>Paramètres

*événementStack*\
La pile d’événements pour cet événement simple. Pour plus d’informations sur les piles d’événements, voir [Événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartActivity (en)

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Cette fonction est appelée lorsqu’un événement de début d’activité est en cours de traitement.

### <a name="parameters"></a>Paramètres

*événementStack*\
La pile d’événements pour cet événement de début d’activité. Pour plus d’informations sur les piles d’événements, voir [Événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivité

Cette fonction est appelée lorsqu’un événement d’arrêt d’activité est en cours de traitement.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Paramètres

*événementStack*\
La pile d’événements pour cet événement d’arrêt d’activité. Pour plus d’informations sur les piles d’événements, voir [Événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="ontraceinfo"></a><a name="on-trace-info"></a>SurTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Cette fonction est appelée une fois au début de chaque passe d’analyse ou de relogging.

### <a name="parameters"></a>Paramètres

*traceInfo*\
Un objet [TraceInfo](../cpp-event-data-types/trace-info.md) qui contient des propriétés utiles sur la trace consommée.

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

::: moniker-end
