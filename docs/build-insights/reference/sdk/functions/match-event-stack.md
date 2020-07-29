---
title: MatchEventStack
description: Référence de la fonction MatchEventStack du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae476c402c3ea0cad558ce41a979b4233e0f1dd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224121"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEventStack` fonction est utilisée pour faire correspondre une pile d’événements à une hiérarchie d’événements spécifique. Les hiérarchies correspondantes sont transférées à un gestionnaire en vue d’un traitement supplémentaire. Pour en savoir plus sur les événements, les piles d’événements et les hiérarchies, consultez [table des événements](../event-table.md).

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

*TEvent*\
Type du parent eldest à faire correspondre dans la pile des événements.

*TEvents*\
Types restants que vous souhaitez faire correspondre dans la pile des événements.

*TCallable*\
Type qui prend en charge `operator()` . Pour plus d’informations sur les arguments passés à cet opérateur, consultez la description du paramètre *pouvant être appelé* .

*TExtraArgs*\
Types des arguments supplémentaires passés à `MatchEventStack` .

*eventStack*\
Pile d’événements à faire correspondre à la hiérarchie des types d’événements décrite par *TEvent* et *TEvents*.

*pouvant être appelé*\
En cas de correspondance avec la pile d’événements avec la hiérarchie des types d’événements décrite par *TEvent* et *TEvents*, `MatchEventStack` appelle *Callable*. Il passe à un argument r-value *pouvant être appelé* pour chaque type dans la hiérarchie d’événements. Le Pack de paramètres *extraArgs* est parfait-transféré dans les paramètres restants de *Callable*.

*extraArgs*\
Les arguments qui sont parfaits parfaits, transférés pour être *appelés* avec le type d’événement correspondant.

### <a name="return-value"></a>Valeur de retour

**`bool`** Valeur qui est **`true`** si la correspondance a réussi, ou **`false`** sinon.

## <a name="remarks"></a>Notes

Le dernier événement dans *eventStack* est toujours mis en correspondance avec la dernière entrée de la liste concaténée \[ *TEvent*, *TEvents...* \] type. Toutes les autres entrées *TEvent* et *TEvents* peuvent correspondre à n’importe quelle position dans *eventStack* , à l’exception de la dernière, à condition qu’elles soient dans le même ordre.

Les types d’événements à utiliser pour les paramètres *TEvent* et *TEvents* sont sélectionnés dans une liste de *classes de capture*. Pour obtenir la liste des événements et les classes de capture que vous pouvez utiliser pour les mettre en correspondance, consultez [table des événements](../event-table.md).

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
