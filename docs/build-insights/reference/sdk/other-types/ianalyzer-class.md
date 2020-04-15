---
title: Cours IAnalyzer
description: La référence de classe CMD Build Insights SDK IAnalyzer.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: be9d80bb94450458c73fd6ce8d908985ba6f293d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329173"
---
# <a name="ianalyzer-class"></a>Cours IAnalyzer

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `IAnalyzer` classe fournit une interface pour analyser une trace de traçage d’événements pour Windows (ETW). Il est utilisé avec le [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), et [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) fonctions. Utilisez `IAnalyzer` comme classe de base pour créer votre propre analyseur qui peut faire partie d’un groupe d’analyseur ou de relogger.

## <a name="syntax"></a>Syntaxe

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>Notes

Les classes `IAnalyzer` qui dérivent peuvent être utilisées à la fois comme analyseurs et réloggers. Lorsqu’elles sont utilisées comme réloggers, les fonctions spécifiques au relogger redirigent vers leur équivalent analyseur. L’inverse n’est pas vrai : `IRelogger` une classe qui dérive de ne peut pas être utilisée comme analyseur. L’utilisation d’un analyseur dans un groupe de relogger est un modèle commun. Lorsqu’il est placé dans une position précoce d’un groupe de relogger, un analyseur peut pré-calculer l’information et les rendre disponibles pour les réloggers dans les positions ultérieures.

La valeur de retour par défaut pour toutes `AnalysisControl::CONTINUE`les fonctions qui ne sont pas remplacées est . Pour plus d’informations, voir [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Membres

En plus du membre [OnTraceInfo](irelogger-class.md#on-trace-info) de l’interface, `IRelogger` la `IAnalyzer` classe contient les membres suivants :

### <a name="destructor"></a>Destructeur

[IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Fonctions

[OnBeginAnalysis](#on-begin-analysis)\
[SurBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[SurBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity (en)](#on-start-activity)\
[OnStopActivité](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a>IAnalyzer

Détruit la classe IAnalyzer.

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a>OnBeginAnalysis

Pour les analyseurs faisant partie d’un groupe d’analyseurs, cette fonction est appelée avant le début de la première analyse. Pour les analyseurs faisant partie d’un groupe de relogger, cette fonction est appelée avant que le passage de relogage commence. Pour les analyseurs qui font partie du groupe d’analyseur et de rélogger de la même session de relogage, cette fonction est appelée deux fois avant le début de la première analyse.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a>SurBeginAnalysisPass

Pour les analyseurs faisant partie d’un groupe d’analyseurs, cette fonction est appelée au début de chaque passage d’analyse. Pour les analyseurs faisant partie d’un groupe de relogger, cette fonction est appelée au début du pass relogger. Pour les analyseurs qui font partie du groupe d’analyseur et de rélogger de la même session de reloglogging, cette fonction est appelée au début de chaque laissez-passer d’analyse, et au début du passage relogger.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Cette fonction ne peut pas être remplacée. Il est appelé par le C 'Build Insights SDK quand un analyseur fait partie d’un groupe de relogger. Cette fonction redirige l’appel vers [OnBeginAnalysis](#on-begin-analysis).

### <a name="return-value"></a>Valeur de retour

Le résultat de l’appel [OnBeginAnalysis.](#on-begin-analysis)

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>SurBeginReloggingPass

Cette fonction ne peut pas être remplacée. Il est appelé par le C 'Build Insights SDK quand un analyseur fait partie d’un groupe de relogger. Cette fonction redirige l’appel vers [OnBeginAnalysisPass](#on-begin-analysis-pass).

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Valeur de retour

Le résultat de l’appel [OnBeginAnalysisPass.](#on-begin-analysis-pass)

## <a name="onendanalysis"></a><a name="on-end-analysis"></a>OnEndAnalysis

Pour les analyseurs qui font partie d’un groupe d’analyseur, cette fonction est appelée après la fin du dernier passage d’analyse. Pour les analyseurs qui font partie d’un groupe de relogger, cette fonction est appelée après la fin du laissez-passer de rélogging. Pour les analyseurs qui font partie à la fois de l’analyseur et du groupe de rélogger de la même session de relogging, cette fonction est appelée deux fois :

1. après que toutes les passes d’analyse ont pris fin et avant le passage de rélogging commence, et
1. après la fin du laissez-passer de rélogging.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a>OnEndAnalysisPass

Pour les analyseurs faisant partie d’un groupe d’analyseurs, cette fonction est appelée à la fin de chaque passage d’analyse. Pour les analyseurs faisant partie d’un groupe de relogger, cette fonction est appelée à la fin du pass relogger. Pour les analyseurs qui font partie du groupe d’analyseur et de rélogger de la même session de reloglogging, cette fonction est appelée à la fin de chaque laissez-passer d’analyse, et à la fin du laissez-passer relogger.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>OnEndRelogging

Cette fonction ne peut pas être remplacée. Il est appelé par le C 'Build Insights SDK quand un analyseur fait partie d’un groupe de relogger. Cette fonction redirige l’appel vers [OnEndAnalysis](#on-end-analysis).

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Valeur de retour

Le résultat de l’appel [OnEndAnalysis.](#on-end-analysis)

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass

Cette fonction ne peut pas être remplacée. Il est appelé par le C 'Build Insights SDK quand un analyseur fait partie d’un groupe de relogger. Cette fonction redirige l’appel vers [OnEndAnalysisPass](#on-end-analysis-pass).

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Valeur de retour

Le résultat de l’appel [OnEndAnalysisPass.](#on-end-analysis-pass)

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>OnSimpleEvent

Cette fonction est appelée lorsqu’un simple événement est en cours de traitement. La deuxième version de cette fonction ne peut pas être remplacée. Il est appelé par le C 'Build Insights SDK quand un analyseur fait partie d’un groupe de relogger. Tous les appels vers la version 2 sont redirigés vers la version 1.

### <a name="version-1"></a>version 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>version 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Paramètres

*événementStack*\
La pile d’événements pour cet événement simple. Pour plus d’informations sur les piles d’événements, voir [Événements](../event-table.md).

*relogSession*\
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartActivity (en)

Cette fonction est appelée lorsqu’un événement de début d’activité est en cours de traitement. La deuxième version de cette fonction ne peut pas être remplacée. Il est appelé par le C 'Build Insights SDK quand un analyseur fait partie d’un groupe de relogger. Tous les appels vers la version 2 sont redirigés vers la version 1.

### <a name="version-1"></a>version 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>version 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Paramètres

*événementStack*\
La pile d’événements pour cet événement de début d’activité. Pour plus d’informations sur les piles d’événements, voir [Événements](../event-table.md).

*relogSession*\
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivité

Cette fonction est appelée lorsqu’un événement d’arrêt d’activité est en cours de traitement. La deuxième version de cette fonction ne peut pas être remplacée. Il est appelé par le C 'Build Insights SDK quand un analyseur fait partie d’un groupe de relogger. Tous les appels vers la version 2 sont redirigés vers la version 1.

### <a name="version-1"></a>version 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>version 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Paramètres

*événementStack*\
La pile d’événements pour cet événement d’arrêt d’activité. Pour plus d’informations sur les piles d’événements, voir [Événements](../event-table.md).

*relogSession*\
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur de retour

Un code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui devrait se passer ensuite.

::: moniker-end
