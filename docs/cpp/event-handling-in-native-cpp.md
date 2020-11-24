---
title: Gestion des événements en mode natif C++
description: Découvrez comment utiliser les extensions Microsoft C++ pour la gestion des événements en C++ natif.
ms.date: 11/20/2020
helpviewer_keywords:
- event handling [C++]
ms.openlocfilehash: 5ad9128b7ff596674c3b08687b722c81b7a10aa8
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483176"
---
# <a name="event-handling-in-native-c"></a>Gestion des événements en mode natif C++

Dans la gestion des événements C++ native, vous configurez une source d’événement et un récepteur d’événements à l’aide des attributs [event_source](../windows/attributes/event-source.md) et [event_receiver](../windows/attributes/event-receiver.md) , respectivement, en spécifiant `type` = `native` . Ces attributs permettent aux classes sur lesquelles ils sont appliqués de déclencher des événements et de gérer des événements dans un contexte non COM natif.

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode de conformité.

## <a name="declaring-events"></a>Déclaration d’événements

Dans une classe de source d’événement, utilisez le [`__event`](../cpp/event.md) mot clé sur une déclaration de méthode pour déclarer la méthode en tant qu’événement. Veillez à déclarer la méthode, mais ne la définissez pas. Dans ce cas, elle génère une erreur du compilateur, car le compilateur définit la méthode implicitement lorsqu’elle est transformée en événement. Les événements natifs peuvent être des méthodes avec zéro, un ou plusieurs paramètres. Le type de retour peut être **`void`** ou n’importe quel type intégral.

## <a name="defining-event-handlers"></a>Définition de gestionnaires d’événements

Dans une classe de récepteur d’événements, vous définissez des gestionnaires d’événements. Les gestionnaires d’événements sont des méthodes avec des signatures (types de retour, conventions d’appel et arguments) qui correspondent à l’événement qu’ils géreront.

## <a name="hooking-event-handlers-to-events"></a>Raccordement de gestionnaires d’événements à des événements

De même, dans une classe de récepteur d’événements, vous utilisez la fonction Intrinsic [`__hook`](../cpp/hook.md) pour associer des événements à des gestionnaires d’événements et pour dissocier [`__unhook`](../cpp/unhook.md) des événements de gestionnaires d’événements. Vous pouvez raccorder plusieurs événements à un gestionnaire d'événements, ou plusieurs gestionnaires d'événements à un événement.

## <a name="firing-events"></a>Déclenchement d’événements

Pour déclencher un événement, appelez la méthode déclarée en tant qu’événement dans la classe source de l’événement. Si des gestionnaires ont été raccordés à l'événement, les gestionnaires sont appelés.

### <a name="native-c-event-code"></a>Code d’événement C++ natif

L'exemple suivant montre comment déclencher un événement en C++ natif. Pour compiler et exécuter l'exemple, consultez les commentaires du code. Pour générer le code dans l’IDE de Visual Studio, vérifiez que l' **`/permissive-`** option est désactivée.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```cpp
// evh_native.cpp
// compile by using: cl /EHsc /W3 evh_native.cpp
#include <stdio.h>

[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};

[event_receiver(native)]
class CReceiver {
public:
   void MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
   }

   void MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
   }

   void hookEvent(CSource* pSource) {
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void unhookEvent(CSource* pSource) {
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   CSource source;
   CReceiver receiver;

   receiver.hookEvent(&source);
   __raise source.MyEvent(123);
   receiver.unhookEvent(&source);
}
```

### <a name="output"></a>Output

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../cpp/event-handling.md)
