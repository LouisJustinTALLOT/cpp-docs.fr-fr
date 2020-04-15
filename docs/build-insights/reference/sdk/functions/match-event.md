---
title: MatchEvent
description: La référence de fonction SDK MatchEvent build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c60653641c676716bcdd60865433773da79325f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323854"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEvent` fonction est utilisée pour faire correspondre un événement contre une liste de types d’événements. Si l’événement correspond à un type dans la liste, il est transmis à un gestionnaire pour un traitement ultérieur.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>Paramètres

*TEvent (en)*\
Le premier type d’événement que vous souhaitez assortir.

*Les TEvents*\
Les autres types d’événements que vous souhaitez assortir.

*TCallable*\
Un type `operator()`qui prend en charge . Pour plus d’informations sur les arguments transmis à cet opérateur, consultez la description du paramètre *appelant.*

*TExtraArgs*\
Les types d’arguments supplémentaires `MatchEvent`qui ont été transmis à .

*Événement*\
L’événement à correspondre avec les types d’événements décrits par *TEvent* et *TEvents*.

*Callable*\
`MatchEvent`invoque *callable* après avoir réussi à faire correspondre l’événement avec l’un des types d’événements décrits par *TEvent* et *TEvents*. Le premier argument passé à *callable* est une valeur r du type d’événement apparié. Le pack de paramètres *extraArgs* est parfaitement transmis dans les paramètres restants de *callable*.  

*extraArgs*\
Les arguments qui obtiennent parfait-avancé à *appeler* avec le type d’événement apparié.

### <a name="return-value"></a>Valeur de retour

Une valeur **bool** qui est **vrai** si l’appariement a été réussie, ou **faux** autrement.

## <a name="remarks"></a>Notes

Les types d’événements à utiliser pour les paramètres *TEvent* et *TEvents* sont sélectionnés parmi une liste de classes de *capture*. Pour une liste d’événements et les classes de capture que vous pouvez utiliser pour les assortir, voir [tableau d’événements](../event-table.md).

## <a name="example"></a>Exemple

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end
