---
title: Gestion des événements dans COM
description: Découvrez comment utiliser les extensions Microsoft C++ pour la gestion des événements COM.
ms.date: 11/20/2020
helpviewer_keywords:
- event handling [C++], COM
- event handling [C++], about event handling
- declaring events
- event handlers [C++], COM
- event handlers
- COM, events
- event receivers, in event handling
- event handling [C++]
- hooking events
- event receivers, name and signature matching
- event sources, in event handling
- declaring events, in COM
- declaring events, event handling in COM
ms.openlocfilehash: 0c664f052fe211c88ad097c9d2617ec47f180eff
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483111"
---
# <a name="event-handling-in-com"></a>Gestion des événements dans COM

Dans la gestion des événements COM, vous configurez une source d’événement et un récepteur d’événements à l’aide des [`event_source`](../windows/attributes/event-source.md) [`event_receiver`](../windows/attributes/event-receiver.md) attributs et, respectivement, en spécifiant `type` = `com` . Ces attributs injectent du code approprié pour les interfaces personnalisées, de distribution et doubles. Le code injecté permet aux classes avec attributs de déclencher des événements et de gérer des événements via des points de connexion COM.

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode de conformité.

## <a name="declaring-events"></a>Déclaration d’événements

Dans une classe de source d’événement, utilisez le [`__event`](../cpp/event.md) mot clé dans une déclaration d’interface pour déclarer les méthodes de cette interface en tant qu’événements. Les événements de cette interface sont déclenchés lorsqu'ils sont appelés comme méthodes d'interface. Les méthodes sur les interfaces d’événements peuvent avoir zéro ou plusieurs paramètres (qui doivent tous être *des paramètres in* ). Le type de retour peut être void ou un type intégral.

## <a name="defining-event-handlers"></a>Définition de gestionnaires d’événements

Vous définissez des gestionnaires d’événements dans une classe de récepteur d’événements. Les gestionnaires d’événements sont des méthodes avec des signatures (types de retour, conventions d’appel et arguments) qui correspondent à l’événement qu’ils géreront. Pour les événements COM, les conventions d’appel ne doivent pas nécessairement correspondre. Pour plus d’informations, consultez [événements com dépendants](#vcconeventhandlingincomanchorlayoutdependentcomevents) de la disposition ci-dessous.

## <a name="hooking-event-handlers-to-events"></a>Raccordement de gestionnaires d’événements à des événements

De même, dans une classe de récepteur d’événements, vous utilisez la fonction Intrinsic [`__hook`](../cpp/hook.md) pour associer des événements à des gestionnaires d’événements et pour dissocier [`__unhook`](../cpp/unhook.md) des événements de gestionnaires d’événements. Vous pouvez raccorder plusieurs événements à un gestionnaire d'événements, ou plusieurs gestionnaires d'événements à un événement.

> [!NOTE]
> En général, il existe deux techniques pour permettre à un récepteur d'événements COM d'accéder aux définitions de l'interface de source d'événements. La première, comme indiqué ci-dessous, consiste à partager un fichier d'en-tête commun. La seconde consiste à utiliser [#import](../preprocessor/hash-import-directive-cpp.md) avec le `embedded_idl` qualificateur Import, afin que la bibliothèque de types de source d’événements soit écrite dans le fichier. tlh avec le code généré par attribut préservé.

## <a name="firing-events"></a>Déclenchement d’événements

Pour déclencher un événement, appelez une méthode dans l’interface déclarée avec le **`__event`** mot clé dans la classe source de l’événement. Si des gestionnaires ont été raccordés à l'événement, les gestionnaires sont appelés.

### <a name="com-event-code"></a>Code d’événement COM

L'exemple suivant montre comment déclencher un événement dans une classe COM. Pour compiler et exécuter l'exemple, consultez les commentaires du code.

```cpp
// evh_server.h
#pragma once

[ dual, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IEvents {
   [id(1)] HRESULT MyEvent([in] int value);
};

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT FireEvent();
};

class DECLSPEC_UUID("530DF3AD-6936-3214-A83B-27B63C7997C4") CSource;
```

Puis le serveur :

```cpp
// evh_server.cpp
// compile with: /LD
// post-build command: Regsvr32.exe /s evh_server.dll
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include "evh_server.h"

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[coclass, event_source(com), uuid("530DF3AD-6936-3214-A83B-27B63C7997C4")]
class CSource : public IEventSource {
public:
   __event __interface IEvents;

   HRESULT FireEvent() {
      __raise MyEvent(123);
      return S_OK;
   }
};
```

Puis le client :

```cpp
// evh_client.cpp
// compile with: /link /OPT:NOREF
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <stdio.h>
#include "evh_server.h"

[ module(name="EventReceiver") ];

[ event_receiver(com) ]
class CReceiver {
public:
   HRESULT MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
      return S_OK;
   }

   HRESULT MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
      return S_OK;
   }

   void HookEvent(IEventSource* pSource) {
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void UnhookEvent(IEventSource* pSource) {
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   // Create COM object
   CoInitialize(NULL);
   {
      IEventSource* pSource = 0;
      HRESULT hr = CoCreateInstance(__uuidof(CSource), NULL,         CLSCTX_ALL, __uuidof(IEventSource), (void **) &pSource);
      if (FAILED(hr)) {
         return -1;
      }

      // Create receiver and fire event
      CReceiver receiver;
      receiver.HookEvent(pSource);
      pSource->FireEvent();
      receiver.UnhookEvent(pSource);
   }
   CoUninitialize();
   return 0;
}
```

### <a name="output"></a>Output

```Output
MyHandler1 was called with value 123.
MyHandler2 was called with value 123.
```

## <a name="layout-dependent-com-events"></a><a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a> Événements COM dépendants de la disposition

La dépendance aux dispositions représente un problème uniquement dans le cadre de la programmation COM. Dans la gestion des événements natifs et managés, les signatures (type de retour, Convention d’appel et arguments) des gestionnaires doivent correspondre à leurs événements, mais les noms de gestionnaires ne doivent pas nécessairement correspondre à leurs événements.

Toutefois, dans la gestion des événements COM, lorsque vous affectez au *`layout_dependent`* paramètre de la valeur `event_receiver` **`true`** , le nom et la correspondance de signature sont appliqués. Les noms et les signatures des gestionnaires dans le récepteur d’événements et dans les événements raccordés doivent correspondre exactement.

Lorsque *`layout_dependent`* a la valeur **`false`** , la Convention d’appel et la classe de stockage (virtuelle, statique, etc.) peuvent être mélangées et mises en correspondance entre la méthode d’événement de déclenchement et les méthodes de raccordement (ses délégués). C’est un peu plus efficace *`layout_dependent`* = **`true`** .

Par exemple, supposons que `IEventSource` est défini pour disposer des méthodes suivantes :

```cpp
[id(1)] HRESULT MyEvent1([in] int value);
[id(2)] HRESULT MyEvent2([in] int value);
```

Supposez que la source d'événement a la forme suivante :

```cpp
[coclass, event_source(com)]
class CSource : public IEventSource {
public:
   __event __interface IEvents;

   HRESULT FireEvent() {
      MyEvent1(123);
      MyEvent2(123);
      return S_OK;
   }
};
```

Ensuite, dans le récepteur d'événements, tout gestionnaire raccordé à une méthode dans `IEventSource` doit correspondre au nom et à la signature, comme indiqué :

```cpp
[coclass, event_receiver(com, true)]
class CReceiver {
public:
   HRESULT MyEvent1(int nValue) {  // name and signature matches MyEvent1
      ...
   }
   HRESULT MyEvent2(E c, char* pc) {  // signature doesn't match MyEvent2
      ...
   }
   HRESULT MyHandler1(int nValue) {  // name doesn't match MyEvent1 (or 2)
      ...
   }
   void HookEvent(IEventSource* pSource) {
      __hook(IFace, pSource);  // Hooks up all name-matched events
                               // under layout_dependent = true
      __hook(&IFace::MyEvent1, pSource, &CReceive::MyEvent1);   // valid
      __hook(&IFace::MyEvent2, pSource, &CSink::MyEvent2);   // not valid
      __hook(&IFace::MyEvent1, pSource, &CSink:: MyHandler1); // not valid
   }
};
```

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../cpp/event-handling.md)
