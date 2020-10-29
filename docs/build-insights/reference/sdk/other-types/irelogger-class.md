---
title: IRelogger, classe
description: Référence de la classe IRelogger du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e504ece95529f7279650062145f3ac0914449c98
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922517"
---
# <a name="irelogger-class"></a>IRelogger, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `IRelogger` classe fournit une interface pour le rejournalisation d’une trace de suivi d’v nements pour Windows (ETW). Elle est utilisée avec les fonctions [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) et [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Utilisez `IRelogger` comme classe de base pour créer votre propre journal qui peut faire partie d’un groupe de rejournalisation.

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

La valeur de retour par défaut pour toutes les fonctions qui ne sont pas substituées est `AnalysisControl::CONTINUE` . Pour plus d’informations, consultez [AnalysisControl](analysis-control-enum-class.md).

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

## <a name="irelogger"></a><a name="irelogger-destructor"></a> ~ IRelogger

Détruit la classe IRelogger.

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a> OnBeginRelogging

Cette fonction est appelée avant le début de la passe de reconnexion.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a> OnBeginReloggingPass

Cette fonction est appelée au début de la passe de reconnexion.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a> OnEndRelogging

Cette fonction est appelée une fois que la passe de reconnexion est terminée.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a> OnEndReloggingPass

Cette fonction est appelée à la fin de la passe de reconnexion.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a> OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Cette fonction est appelée lorsqu’un événement simple est traité.

### <a name="parameters"></a>Paramètres

*eventStack*\
Pile d’événements pour cet événement simple. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="onstartactivity"></a><a name="on-start-activity"></a> OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Cette fonction est appelée lorsqu’un événement de démarrage d’activité est en cours de traitement.

### <a name="parameters"></a>Paramètres

*eventStack*\
Pile d’événements pour cet événement de démarrage d’activité. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a> OnStopActivity

Cette fonction est appelée lorsqu’un événement d’arrêt d’activité est en cours de traitement.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Paramètres

*eventStack*\
Pile d’événements pour cet événement d’arrêt d’activité. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="ontraceinfo"></a><a name="on-trace-info"></a> OnTraceInfo

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
