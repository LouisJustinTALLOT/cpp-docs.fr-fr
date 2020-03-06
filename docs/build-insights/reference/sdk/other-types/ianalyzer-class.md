---
title: IAnalyzer, classe
description: Référence C++ de la classe IAnalyzer du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53f7b36695bb24d96ccfe88afbb56ff717c94dc9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332452"
---
# <a name="ianalyzer-class"></a>IAnalyzer, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `IAnalyzer` fournit une interface pour l’analyse d’une trace Suivi d’v nements pour Windows (ETW). Elle est utilisée avec les fonctions [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)et [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Utilisez `IAnalyzer` comme classe de base pour créer votre propre analyseur qui peut faire partie d’un analyseur ou d’un groupe de rejournalisation.

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

Les classes qui dérivent de `IAnalyzer` peuvent être utilisées comme des analyseurs et des rejournalisation. Lorsqu’ils sont utilisés comme rejournalisation, les fonctions spécifiques au rejournalisation redirigent vers leur équivalent d’analyseur. L’inverse n’est pas vrai : une classe qui dérive de `IRelogger` ne peut pas être utilisée en tant qu’analyseur. L’utilisation d’un analyseur dans un groupe de rejournalisation est un modèle courant. Lorsqu’il est placé à la position initiale d’un groupe de rejournalisation, un analyseur peut précalculer les informations et les rendre disponibles pour les réenregistrements dans les positions ultérieures.

La valeur de retour par défaut pour toutes les fonctions qui ne sont pas remplacées est `AnalysisControl::CONTINUE`. Pour plus d’informations, consultez [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Membres

En plus du membre [OnTraceInfo](irelogger-class.md#on-trace-info) de l’interface `IRelogger`, la classe `IAnalyzer` contient les membres suivants :

### <a name="destructor"></a>Destructeur

[~ IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Fonctions

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer-destructor"></a>~ IAnalyzer

Détruit la classe IAnalyzer.

```cpp
virtual ~IAnalyzer();
```

## <a name="on-begin-analysis"></a>OnBeginAnalysis

Pour les analyseurs appartenant à un groupe d’analyseur, cette fonction est appelée avant le début de la première étape d’analyse. Pour les analyseurs qui font partie d’un groupe de rejournalisation, cette fonction est appelée avant le début de la passe de reconnexion. Pour les analyseurs faisant partie de l’analyseur et du groupe de rejournalisation de la même session de rejournalisation, cette fonction est appelée deux fois avant le début de la première étape d’analyse.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

Pour les analyseurs appartenant à un groupe d’analyseur, cette fonction est appelée au début de chaque passe d’analyse. Pour les analyseurs qui font partie d’un groupe de rejournalisation, cette fonction est appelée au début de la passe de Refrappe. Pour les analyseurs faisant partie de l’analyseur et du groupe de rejournalisation de la même session de rejournalisation, cette fonction est appelée au début de chaque passe d’analyse et au début de la passe de Refrappe.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Cette fonction ne peut pas être substituée. Elle est appelée par le C++ Kit de développement logiciel (SDK) Build Insights lorsqu’un analyseur fait partie d’un groupe de rejournalisation. Cette fonction redirige l’appel vers [OnBeginAnalysis](#on-begin-analysis).

### <a name="return-value"></a>Valeur de retour

Résultat de l’appel [OnBeginAnalysis](#on-begin-analysis) .

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Cette fonction ne peut pas être substituée. Elle est appelée par le C++ Kit de développement logiciel (SDK) Build Insights lorsqu’un analyseur fait partie d’un groupe de rejournalisation. Cette fonction redirige l’appel vers [OnBeginAnalysisPass](#on-begin-analysis-pass).

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Valeur de retour

Résultat de l’appel [OnBeginAnalysisPass](#on-begin-analysis-pass) .

## <a name="on-end-analysis"></a>OnEndAnalysis

Pour les analyseurs qui font partie d’un groupe d’analyseur, cette fonction est appelée après la fin de la dernière analyse. Pour les analyseurs qui font partie d’un groupe de rejournalisation, cette fonction est appelée une fois que la passe de reconnexion est terminée. Pour les analyseurs qui font partie de l’analyseur et du groupe de rejournalisation de la même session de rejournalisation, cette fonction est appelée deux fois :

1. une fois que toutes les analyses sont terminées et avant le début de la passe de rejournalisation, et
1. une fois la passe de reconnexion terminée.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-end-analysis-pass"></a>OnEndAnalysisPass

Pour les analyseurs appartenant à un groupe d’analyseur, cette fonction est appelée à la fin de chaque passe d’analyse. Pour les analyseurs qui font partie d’un groupe de rejournalisation, cette fonction est appelée à la fin de la passe de Refrappe. Pour les analyseurs faisant partie de l’analyseur et du groupe de rejournalisation de la même session de rejournalisation, cette fonction est appelée à la fin de chaque passe d’analyse, et à la fin de la passe de Refrappe.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-end-relogging"></a>OnEndRelogging

Cette fonction ne peut pas être substituée. Elle est appelée par le C++ Kit de développement logiciel (SDK) Build Insights lorsqu’un analyseur fait partie d’un groupe de rejournalisation. Cette fonction redirige l’appel vers [OnEndAnalysis](#on-end-analysis).

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Valeur de retour

Résultat de l’appel [OnEndAnalysis](#on-end-analysis) .

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

Cette fonction ne peut pas être substituée. Elle est appelée par le C++ Kit de développement logiciel (SDK) Build Insights lorsqu’un analyseur fait partie d’un groupe de rejournalisation. Cette fonction redirige l’appel vers [OnEndAnalysisPass](#on-end-analysis-pass).

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Valeur de retour

Résultat de l’appel [OnEndAnalysisPass](#on-end-analysis-pass) .

## <a name="on-simple-event"></a>OnSimpleEvent

Cette fonction est appelée lorsqu’un événement simple est traité. La deuxième version de cette fonction ne peut pas être substituée. Elle est appelée par le C++ Kit de développement logiciel (SDK) Build Insights lorsqu’un analyseur fait partie d’un groupe de rejournalisation. Tous les appels à la version 2 sont redirigés vers la version 1.

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

*eventStack*\
Pile d’événements pour cet événement simple. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

*relogSession*\
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-start-activity"></a>OnStartActivity

Cette fonction est appelée lorsqu’un événement de démarrage d’activité est en cours de traitement. La deuxième version de cette fonction ne peut pas être substituée. Elle est appelée par le C++ Kit de développement logiciel (SDK) Build Insights lorsqu’un analyseur fait partie d’un groupe de rejournalisation. Tous les appels à la version 2 sont redirigés vers la version 1.

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

*eventStack*\
Pile d’événements pour cet événement de démarrage d’activité. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

*relogSession*\
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

## <a name="on-stop-activity"></a>OnStopActivity

Cette fonction est appelée lorsqu’un événement d’arrêt d’activité est en cours de traitement. La deuxième version de cette fonction ne peut pas être substituée. Elle est appelée par le C++ Kit de développement logiciel (SDK) Build Insights lorsqu’un analyseur fait partie d’un groupe de rejournalisation. Tous les appels à la version 2 sont redirigés vers la version 1.

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

*eventStack*\
Pile d’événements pour cet événement d’arrêt d’activité. Pour plus d’informations sur les piles d’événements, consultez [événements](../event-table.md).

*relogSession*\
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur de retour

Code [AnalysisControl](analysis-control-enum-class.md) qui décrit ce qui doit se passer ensuite.

::: moniker-end
