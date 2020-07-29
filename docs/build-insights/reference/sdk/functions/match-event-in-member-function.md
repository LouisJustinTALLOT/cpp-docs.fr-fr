---
title: MatchEventInMemberFunction
description: Référence de la fonction MatchEventInMemberFunction du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d3fdc015b0744cb5d0f98a1c9025343b93489ed9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224147"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEventInMemberFunction` fonction est utilisée pour faire correspondre un événement au type décrit par le premier paramètre d’une fonction membre. L’événement correspondant est transféré à la fonction membre pour un traitement ultérieur.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>Paramètres

*TInterface*\
Type qui contient la fonction membre.

*TReturn*\
Type de retour de la fonction membre.

*TEvent*\
Type de l’événement à faire correspondre.

*TExtraParams*\
Types des paramètres supplémentaires acceptés par la fonction membre avec le type d’événement à faire correspondre.

*TExtraArgs*\
Types des arguments supplémentaires passés à `MatchEventInMemberFunction` .

*événement*\
Événement à faire correspondre au type d’événement décrit par *TEvent*.

*objectPtr*\
Pointeur vers un objet sur lequel *memberFunc* est appelé.

*memberFunc*\
Fonction membre qui décrit le type d’événement à faire correspondre.

*extraArgs*\
Les arguments qui sont parfaits sont transmis à *memberFunc* avec le paramètre de type d’événement.

### <a name="return-value"></a>Valeur de retour

**`bool`** Valeur qui est **`true`** si la correspondance a réussi, ou **`false`** sinon.

## <a name="remarks"></a>Notes

Le type d’événement à utiliser pour le paramètre *TEvent* peut être sélectionné dans une liste de *classes de capture*. Pour obtenir la liste des événements et les classes de capture que vous pouvez utiliser pour les mettre en correspondance, consultez [table des événements](../event-table.md).

## <a name="example"></a>Exemple

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end
