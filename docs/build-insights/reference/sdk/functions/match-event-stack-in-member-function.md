---
title: MatchEventStackInMemberFunction
description: La référence de fonction de construction SDK MatchEventStackInMemberFunction.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28842a02e7edc2e00266d8c7941798f4ce714ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323888"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEventStackInMemberFunction` fonction est utilisée pour correspondre à une pile d’événements par rapport à une hiérarchie d’événements spécifique, décrite par la liste des paramètres d’une fonction membre. Les hiérarchies assorties sont transmises à la fonction de membre pour un traitement ultérieur. Pour en savoir plus sur les événements, les piles d’événements et les hiérarchies, consultez [la table d’événements](../event-table.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>Paramètres

*TInterface (en)*\
Le type qui contient la fonction de membre.

*TReturn TReturn*\
Le type de retour de la fonction membre.

*T1*, ..., *T10*\
Les types décrivant la hiérarchie de l’événement à correspondre.

*TExtraParams*\
Les types de paramètres supplémentaires acceptés par la fonction membre, et les types de hiérarchie d’événements.

*TExtraArgs*\
Les types d’arguments supplémentaires `MatchEventStackInMemberFunction`qui ont été transmis à .

*événementStack*\
La pile d’événements pour correspondre à la hiérarchie de type événement décrit par *T1* à travers *T10*.

*objetPtr*\
Un pointeur à un objet sur lequel *le membreFunc* est appelé.

*membreFunc*\
La fonction membre qui décrit la hiérarchie de type d’événement pour correspondre.

*extraArgs*\
Les arguments qui obtiennent parfait-transmis à *membreFunc* avec les paramètres de hiérarchie de type d’événement.

### <a name="return-value"></a>Valeur de retour

Une valeur **bool** qui est **vrai** si l’appariement a été réussie, ou **faux** autrement.

## <a name="remarks"></a>Notes

Le dernier événement dans *le casStack* est toujours égalé contre la dernière entrée dans la hiérarchie de type événement à correspondre. Tous les autres types dans la hiérarchie de type événement peuvent correspondre à n’importe quelle position dans *le casStack* sauf le dernier, à condition qu’ils soient dans le même ordre.

Les types d’événements à utiliser pour les paramètres *T1* à *T10* sont sélectionnés parmi une liste de classes de *capture*. Pour une liste d’événements et les classes de capture que vous pouvez utiliser pour les assortir, voir [tableau d’événements](../event-table.md).

## <a name="example"></a>Exemple

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end
