---
title: __event
ms.date: 11/04/2016
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
ms.openlocfilehash: c1c9fa5a6df4cbb1c18e5d5406bdde0197d155b2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498821"
---
# <a name="__event"></a>__event

Déclare un événement.

## <a name="syntax"></a>Syntaxe

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>Notes

Le mot clé **`__event`** peut être appliqué à une déclaration de méthode, à une déclaration d’interface ou à une déclaration de membre de données. Toutefois, vous ne pouvez pas utiliser le **`__event`** mot clé pour qualifier un membre d’une classe imbriquée.

Selon que votre source et votre récepteur d'événements sont C++ natif, COM ou managé (.NET Framework), vous pouvez utiliser les constructions suivantes en tant qu'événements :

|C++ natif|COM|Managé (.NET Framework)|
|------------------|---------|--------------------------------|
|Méthode|—|method|
|—|interface|—|
|—|—|membre de données|

Utilisez [__hook](../cpp/hook.md) dans un récepteur d’événements pour associer une méthode de gestionnaire à une méthode d’événement. Notez qu’après avoir créé un événement avec le **`__event`** mot clé, tous les gestionnaires d’événements raccordés à cet événement sont appelés lorsque l’événement est appelé.

Une **`__event`** déclaration de méthode ne peut pas avoir de définition ; une définition est générée implicitement, de sorte que la méthode d’événement peut être appelée comme s’il s’agissait d’une méthode ordinaire.

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="native-events"></a>Événements natifs

Les événements natifs sont des méthodes. Le type de retour est généralement HRESULT ou **`void`** , mais peut être n’importe quel type intégral, y compris un **`enum`** . Lorsqu’un événement utilise un type de retour intégral, une condition d’erreur est définie lorsqu’un gestionnaire d’événements retourne une valeur différente de zéro, auquel cas l’événement déclenché appelle les autres délégués.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Pour obtenir un exemple de code [, consultez Gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md) .

## <a name="com-events"></a>Événements COM

Les événements COM sont des interfaces. Les paramètres d’une méthode dans une interface de source d’événement doivent être dans des paramètres (mais cela n’est pas rigoureusement appliqué), car un paramètre *de* *sortie* n’est pas utile lors de la multidiffusion. Un avertissement de niveau 1 sera émis si vous utilisez un paramètre *out* .

Le type de retour est généralement HRESULT ou **`void`** , mais peut être tout type intégral, y compris **`enum`** . Lorsqu'un événement utilise un type de retour intégral et qu'un gestionnaire d'événements retourne une valeur différente de zéro, il s'agit d'une condition d'erreur. L'événement déclenché annule alors les appels aux autres délégués. Notez que le compilateur marque automatiquement une interface source d’événement en tant que [source](../windows/attributes/source-cpp.md) dans l’IDL généré.

Le mot clé [__interface](../cpp/interface.md) est toujours requis après **`__event`** pour une source d’événement com.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Pour obtenir un exemple de code [, consultez Gestion des événements dans com](../cpp/event-handling-in-com.md) .

## <a name="managed-events"></a>Événements managés

Pour plus d’informations sur le codage des événements dans la nouvelle syntaxe, consultez [Event](../extensions/event-cpp-component-extensions.md).

Les événements managés sont des méthodes ou des données membres. En cas d’utilisation avec un événement, le type de retour d’un délégué doit être conforme à la [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components). Le type de retour du gestionnaire d'événements doit correspondre à celui du délégué. Pour plus d’informations sur les délégués, consultez [délégués et événements](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md). Si un événement managé est un membre de données, son type doit être un pointeur vers un délégué.

Dans .NET Framework, vous pouvez traiter un membre de données comme s'il s'agissait d'une méthode (autrement dit, la méthode `Invoke` de son délégué correspondant). Vous devez prédéfinir le type délégué pour déclarer un membre de données d'événement managé. En revanche, une méthode d'événement managé définit implicitement le délégué managé correspondant, s'il n'est pas déjà défini. Par exemple, vous pouvez déclarer une valeur d'événement telle que `OnClick` comme événement de la manière suivante :

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Lors de la déclaration implicite d’un événement managé, vous pouvez spécifier des accesseurs add et remove qui seront appelés lorsque les gestionnaires d’événements sont ajoutés ou supprimés. Vous pouvez également définir la méthode qui appelle (déclenche) l'événement en dehors de la classe.

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

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Gestion des événements](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)
