---
title: Gestion des événements en mode natif C++
ms.date: 11/04/2016
helpviewer_keywords:
- event handling [C++], Visual C++
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: 93bfcc93c680618ea3a51eabd145548a4f47563a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772330"
---
# <a name="event-handling-in-native-c"></a>Gestion des événements en mode natif C++

Dans Gestion des événements C++ native, vous configurez un récepteur d’événements source et les événements à l’aide de la [event_source](../windows/attributes/event-source.md) et [event_receiver](../windows/attributes/event-receiver.md) des attributs, respectivement, en spécifiant `type` = `native`. Ces attributs permettent aux classes auxquelles ils sont appliqués de déclencher et de gérer des événements dans un contexte natif non COM.

## <a name="declaring-events"></a>Déclaration d'événements

Dans une classe de source d’événement, utilisez le [__event](../cpp/event.md) mot clé dans une déclaration de méthode pour déclarer la méthode comme un événement. Veillez à déclarer la méthode, mais ne la définissez pas ; cela générerait une erreur du compilateur, car celui-ci définit la méthode implicitement lorsqu'elle est convertie en événement. Les événements natifs peuvent être des méthodes avec zéro, un ou plusieurs paramètres. Le type de retour peut être void ou un type intégral.

## <a name="defining-event-handlers"></a>Définition de gestionnaires d'événements

Dans une classe de récepteur d'événements, vous définissez des gestionnaires d'événements, qui sont des méthodes avec signatures (types de retour, conventions d'appel et arguments) qui correspondent à l'événement qu'ils doivent gérer.

## <a name="hooking-event-handlers-to-events"></a>Raccordement de gestionnaires d'événements à des événements

Également dans une classe de récepteur d’événements, vous utilisez la fonction intrinsèque [__hook](../cpp/hook.md) pour associer des événements et gestionnaires d’événements et [__unhook](../cpp/unhook.md) pour dissocier des événements à partir des gestionnaires d’événements. Vous pouvez raccorder plusieurs événements à un gestionnaire d'événements, ou plusieurs gestionnaires d'événements à un événement.

## <a name="firing-events"></a>Déclenchement d'événements

Pour déclencher un événement, il vous suffit d'appeler la méthode déclarée comme événement dans la classe de source d'événement. Si des gestionnaires ont été raccordés à l'événement, les gestionnaires sont appelés.

### <a name="native-c-event-code"></a>Code d'événement C++ natif

L'exemple suivant montre comment déclencher un événement en C++ natif. Pour compiler et exécuter l'exemple, consultez les commentaires du code.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```cpp
// evh_native.cpp
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

### <a name="output"></a>Sortie

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../cpp/event-handling.md)