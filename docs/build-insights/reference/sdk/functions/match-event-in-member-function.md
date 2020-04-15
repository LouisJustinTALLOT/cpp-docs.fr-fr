---
title: MatchEventInMemberFunction
description: La référence de la fonction de construction SDK MatchEventInMemberFunction.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 522630da16e3f4a1294316d88140f4bc25dca2c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323897"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEventInMemberFunction` fonction est utilisée pour faire correspondre un événement par rapport au type décrit par le premier paramètre d’une fonction membre. L’événement apparié est transmis à la fonction membre pour un traitement ultérieur.

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

*TInterface (en)*\
Le type qui contient la fonction de membre.

*TReturn TReturn*\
Le type de retour de la fonction membre.

*TEvent (en)*\
Le type d’événement à égaler.

*TExtraParams*\
Les types de paramètres supplémentaires acceptés par la fonction membre ainsi que le type d’événement pour correspondre.

*TExtraArgs*\
Les types d’arguments supplémentaires `MatchEventInMemberFunction`qui ont été transmis à .

*Événement*\
L’événement pour correspondre au type d’événement décrit par *TEvent*.

*objetPtr*\
Un pointeur à un objet sur lequel *le membreFunc* est appelé.

*membreFunc*\
La fonction membre qui décrit le type d’événement pour correspondre.

*extraArgs*\
Les arguments qui obtiennent parfait-transmis à *membreFunc* avec le paramètre de type d’événement.

### <a name="return-value"></a>Valeur de retour

Une valeur **bool** qui est **vrai** si l’appariement a été réussie, ou **faux** autrement.

## <a name="remarks"></a>Notes

Le type d’événement à utiliser pour le paramètre *TEvent* peut être sélectionné à partir d’une liste de classes de *capture*. Pour une liste d’événements et les classes de capture que vous pouvez utiliser pour les assortir, voir [tableau d’événements](../event-table.md).

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
