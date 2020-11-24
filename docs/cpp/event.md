---
title: __event
description: Découvrez comment utiliser le mot clé d’extension Microsoft C++ `__event` pour la gestion des événements natifs.
ms.date: 11/20/2020
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.openlocfilehash: 1678699d9b66c1a49dd5ca2bb019a6229c37a031
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483136"
---
# <a name="__event-keyword"></a>`__event` mot

Déclare un événement.

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode de conformité.

## <a name="syntax"></a>Syntaxe

> **`__event`** *`member-function-declarator`* **`;`**\
> **`__event`** **`__interface`** *`interface-specifier`* **`;`**\
> **`__event`** *`data-member-declarator`* **`;`**

## <a name="remarks"></a>Notes

Le mot clé spécifique **`__event`** à Microsoft peut être appliqué à une déclaration de fonction membre, à une déclaration d’interface ou à une déclaration de membre de données. Toutefois, vous ne pouvez pas utiliser le **`__event`** mot clé pour qualifier un membre d’une classe imbriquée.

Selon que votre source et votre récepteur d'événements sont C++ natif, COM ou managé (.NET Framework), vous pouvez utiliser les constructions suivantes en tant qu'événements :

| C++ natif | COM | Managé (.NET Framework) |
|--|--|--|
| fonctions membres | - | method |
| - | interface | - |
| - | - | membre de données |

Utilisez [`__hook`](../cpp/hook.md) dans un récepteur d’événements pour associer une fonction membre de gestionnaire à une fonction membre d’événement. Après avoir créé un événement avec le **`__event`** mot clé, tous les gestionnaires d’événements raccordés à cet événement sont ensuite appelés lorsque l’événement est appelé.

Une **`__event`** déclaration de fonction membre ne peut pas avoir de définition ; une définition est générée implicitement, la fonction membre d’événement peut donc être appelée comme s’il s’agissait d’une fonction membre ordinaire.

> [!NOTE]
> Une classe ou un struct basé sur un modèle ne peut pas contenir d’événements.

## <a name="native-events"></a>Événements natifs

Les événements natifs sont des fonctions membres. Le type de retour est généralement `HRESULT` ou **`void`** , mais peut être n’importe quel type intégral, y compris un **`enum`** . Lorsqu’un événement utilise un type de retour intégral, une condition d’erreur est définie lorsqu’un gestionnaire d’événements retourne une valeur différente de zéro. Dans ce cas, l’événement déclenché appelle les autres délégués.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Pour obtenir un exemple de code [, consultez Gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md) .

## <a name="com-events"></a>Événements COM

Les événements COM sont des interfaces. Les paramètres d’une fonction membre dans une interface de source d’événement doivent être *des* paramètres, mais elle n’est pas rigoureusement appliquée. Cela est dû au fait qu’un paramètre de *sortie* n’est pas utile lors de la multidiffusion. Un avertissement de niveau 1 est émis si vous utilisez un paramètre *out* .

Le type de retour est généralement `HRESULT` ou **`void`** , mais peut être tout type intégral, y compris **`enum`** . Lorsqu’un événement utilise un type de retour intégral et qu’un gestionnaire d’événements retourne une valeur différente de zéro, il s’agit d’une condition d’erreur. L’événement déclenché abandonne les appels aux autres délégués. Le compilateur marque automatiquement une interface source d’événement en tant que [`source`](../windows/attributes/source-cpp.md) dans l’IDL généré.

Le [`__interface`](../cpp/interface.md) mot clé est toujours requis après **`__event`** pour une source d’événement com.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Pour obtenir un exemple de code [, consultez Gestion des événements dans com](../cpp/event-handling-in-com.md) .

## <a name="managed-events"></a>Événements managés

Pour plus d’informations sur le codage des événements dans la nouvelle syntaxe, consultez [Event](../extensions/event-cpp-component-extensions.md).

Les événements managés sont des membres de données ou des fonctions membres. En cas d’utilisation avec un événement, le type de retour d’un délégué doit être conforme à la [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components). Le type de retour du gestionnaire d'événements doit correspondre à celui du délégué. Pour plus d’informations sur les délégués, consultez [délégués et événements](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md). Si un événement managé est un membre de données, son type doit être un pointeur vers un délégué.

Dans .NET Framework, vous pouvez traiter un membre de données comme s'il s'agissait d'une méthode (autrement dit, la méthode `Invoke` de son délégué correspondant). Pour ce faire, prédéfinissez le type délégué pour la déclaration d’un membre de données d’événement managé. En revanche, une méthode d’événement managé définit implicitement le délégué managé correspondant s’il n’est pas déjà défini. Par exemple, vous pouvez déclarer une valeur d'événement telle que `OnClick` comme événement de la manière suivante :

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Lors de la déclaration implicite d’un événement managé, vous pouvez spécifier `add` les `remove` accesseurs et qui sont appelés lors de l’ajout ou de la suppression de gestionnaires d’événements. Vous pouvez également définir la fonction membre qui appelle (déclenche) l’événement à l’extérieur de la classe.

## <a name="example-native-events"></a>Exemple : événements natifs

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>Exemple : événements COM

```cpp
// EventHandling_COM_Event.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT MyEvent();
};
[ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]
class CSource : public IEventSource {
public:
   __event __interface IEventSource;
   HRESULT FireEvent() {
      __raise MyEvent();
      return S_OK;
   }
};
```

## <a name="see-also"></a>Voir aussi

[Mot](../cpp/keywords-cpp.md)\
[Gestion des événements](../cpp/event-handling.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__hook`](../cpp/hook.md)\
[`__unhook`](../cpp/unhook.md)\
[`__raise`](../cpp/raise.md)
