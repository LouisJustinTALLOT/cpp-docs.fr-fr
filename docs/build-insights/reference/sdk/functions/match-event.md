---
title: MatchEvent
description: Référence C++ de la fonction MatchEvent du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f8022953e2f56f7c8917f161b094c50e0c5ecbdf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332774"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `MatchEvent` est utilisée pour faire correspondre un événement à une liste de types d’événements. Si l’événement correspond à un type de la liste, il est transféré à un gestionnaire en vue d’un traitement ultérieur.

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

*TEvent*\
Premier type d’événement que vous souhaitez faire correspondre.

*TEvents*\
Types d’événements restants que vous souhaitez faire correspondre.

*TCallable*\
Type qui prend en charge `operator()`. Pour plus d’informations sur les arguments passés à cet opérateur, consultez la description du paramètre *pouvant être appelé* .

*TExtraArgs*\
Types des arguments supplémentaires passés à `MatchEvent`.

*event*\
Événement à faire correspondre aux types d’événements décrits par *TEvent* et *TEvents*.

\ *pouvant être appelé*
`MatchEvent` *appelle une fois que* l’événement a été mis en correspondance avec l’un des types d’événements décrits par *TEvent* et *TEvents*. Le premier argument passé à *Callable* est une valeur r du type d’événement correspondant. Le Pack de paramètres *extraArgs* est parfait-transféré dans les paramètres restants de *Callable*.  

*extraArgs*\
Les arguments qui sont parfaits parfaits, transférés pour être *appelés* avec le type d’événement correspondant.

### <a name="return-value"></a>Valeur de retour

Valeur **booléenne** qui est **true** si la correspondance a réussi, ou **false** dans le cas contraire.

## <a name="remarks"></a>Notes

Les types d’événements à utiliser pour les paramètres *TEvent* et *TEvents* sont sélectionnés dans une liste de *classes de capture*. Pour obtenir la liste des événements et les classes de capture que vous pouvez utiliser pour les mettre en correspondance, consultez [table des événements](../event-table.md).

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
