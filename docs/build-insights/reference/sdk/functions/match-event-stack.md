---
title: MatchEventStack (en)
description: La référence de fonction CMD Build Insights SDK MatchEventStack.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a223d420e8c48667fbd1c6569f02d0486f597b5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323872"
---
# <a name="matcheventstack"></a>MatchEventStack (en)

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEventStack` fonction est utilisée pour correspondre à une pile d’événements par rapport à une hiérarchie d’événements spécifique. Les hiérarchies assorties sont transmises à un gestionnaire pour un traitement ultérieur. Pour en savoir plus sur les événements, les piles d’événements et les hiérarchies, consultez [la table d’événements](../event-table.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>Paramètres

*TEvent (en)*\
Le type de parent aîné à correspondre dans la pile d’événements.

*Les TEvents*\
Les autres types que vous souhaitez assortir dans la pile d’événements.

*TCallable*\
Un type `operator()`qui prend en charge . Pour plus d’informations sur les arguments transmis à cet opérateur, consultez la description du paramètre *appelant.*

*TExtraArgs*\
Les types d’arguments `MatchEventStack`supplémentaires passés à .

*événementStack*\
La pile d’événements pour correspondre à la hiérarchie de type événement décrit par *TEvent* et *TEvents*.

*Callable*\
Après avoir réussi à faire correspondre la pile de l’événement `MatchEventStack` avec la hiérarchie de type événement décrit par *TEvent* et *TEvents*, invoque *callable*. Il passe à *appeler* un argument de valeur r pour chaque type dans la hiérarchie d’événements. Le pack de paramètres *extraArgs* est parfaitement transmis dans les paramètres restants de *callable*.

*extraArgs*\
Les arguments qui obtiennent parfait-avancé à *appeler* avec le type d’événement apparié.

### <a name="return-value"></a>Valeur de retour

Une valeur **bool** qui est **vrai** si l’appariement a été réussie, ou **faux** autrement.

## <a name="remarks"></a>Notes

La dernière épreuve en *cas de matchStack* est toujours \[égalée contre la dernière entrée dans le *TEvent*concatenated , *TEvents...* \] liste de type. Toutes les autres entrées *de TEvent* et *TEvents* peuvent correspondre à n’importe quelle position dans *le casstack* sauf le dernier, à condition qu’ils soient dans le même ordre.

Les types d’événements à utiliser pour les paramètres *TEvent* et *TEvents* sont sélectionnés parmi une liste de classes de *capture*. Pour une liste d’événements et les classes de capture que vous pouvez utiliser pour les assortir, voir [tableau d’événements](../event-table.md).

## <a name="example"></a>Exemple

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end
