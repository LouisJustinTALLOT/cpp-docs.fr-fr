---
title: MatchEventStackInMemberFunction
description: Référence C++ de la fonction MatchEventStackInMemberFunction du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a966ea5209a25a62c08cb0873d0565299a15d27
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332788"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `MatchEventStackInMemberFunction` est utilisée pour faire correspondre une pile d’événements à une hiérarchie d’événements spécifique, décrite par la liste des paramètres d’une fonction membre. Les hiérarchies correspondantes sont transférées à la fonction membre pour un traitement ultérieur. Pour en savoir plus sur les événements, les piles d’événements et les hiérarchies, consultez [table des événements](../event-table.md).

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

*TInterface*\
Type qui contient la fonction membre.

*TReturn*\
Type de retour de la fonction membre.

*T1*,..., *T10*\
Types décrivant la hiérarchie d’événements à faire correspondre.

*TExtraParams*\
Types des paramètres supplémentaires acceptés par la fonction membre et les types de hiérarchies d’événements.

*TExtraArgs*\
Types des arguments supplémentaires passés à `MatchEventStackInMemberFunction`.

*eventStack*\
Pile d’événements à faire correspondre à la hiérarchie des types d’événements décrite par *T1* à *T10*.

*objectPtr*\
Pointeur vers un objet sur lequel *memberFunc* est appelé.

*memberFunc*\
Fonction membre qui décrit la hiérarchie des types d’événements à faire correspondre.

*extraArgs*\
Les arguments qui sont parfaits sont transmis à *memberFunc* avec les paramètres de hiérarchie de type d’événement.

### <a name="return-value"></a>Valeur de retour

Valeur **booléenne** qui est **true** si la correspondance a réussi, ou **false** dans le cas contraire.

## <a name="remarks"></a>Notes

Le dernier événement dans *eventStack* est toujours mis en correspondance avec la dernière entrée de la hiérarchie des types d’événements à faire correspondre. Tous les autres types dans la hiérarchie des types d’événements peuvent correspondre à n’importe quelle position dans *eventStack* , à l’exception de la dernière, à condition qu’ils soient dans le même ordre.

Les types d’événements à utiliser pour les paramètres *T1* à *T10* sont sélectionnés dans une liste de *classes de capture*. Pour obtenir la liste des événements et les classes de capture que vous pouvez utiliser pour les mettre en correspondance, consultez [table des événements](../event-table.md).

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
