---
title: __unhook
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
ms.openlocfilehash: e8f42c35024995c026ae10fc7f0ab3db77d1e5dc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769522"
---
# <a name="unhook"></a>__unhook

Dissocie une méthode de gestionnaire d'un événement.

## <a name="syntax"></a>Syntaxe

```cpp
long  __unhook(
   &SourceClass::EventMethod,
   source,
   &ReceiverClass::HandlerMethod
   [, receiver = this]
);
long  __unhook(
   interface,
   source
);
long  __unhook(
   source
);
```

#### <a name="parameters"></a>Paramètres

**&** *SourceClass* `::` *EventMethod* un pointeur vers la méthode d’événement à partir de laquelle vous décrochez la méthode de gestionnaire d’événements :

- Événements natifs C++ : *SourceClass* est la classe source d’événements et *EventMethod* est l’événement.

- Événements COM : *SourceClass* est l’interface de source d’événements et *EventMethod* est une de ses méthodes.

- Événements managés : *SourceClass* est la classe source d’événements et *EventMethod* est l’événement.

*interface*<br/>
Le nom d’interface décroché à partir *récepteur*, uniquement pour les récepteurs d’événements COM dans lequel le *layout_dependent* paramètre de la [event_receiver](../windows/attributes/event-receiver.md) attribut est **true**.

*source*<br/>
Pointeur vers une instance de la source d'événement. En fonction du code `type` spécifié dans `event_receiver`, *source* peut prendre l’une des opérations suivantes :

- Un pointeur d'objet source de l'événement natif.

- Un `IUnknown`-en fonction de pointeur (source COM).

- Un pointeur d'objet managé (pour les événements managés).

**&** *ReceiverClass* `::` `HandlerMethod` un pointeur vers la méthode de gestionnaire d’événements à décrocher d’un événement. Le gestionnaire est spécifié en tant que méthode d’une classe ou une référence à la même ; Si vous ne spécifiez pas le nom de classe, **__unhook** part du principe que la classe est que dans lequel elle est appelée.

- Événements natifs C++ : *ReceiverClass* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

- Événements COM : *ReceiverClass* est l’interface de récepteur d’événements et `HandlerMethod` est un de ses gestionnaires.

- Événements managés : *ReceiverClass* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

*récepteur*(facultatif) un pointeur vers une instance de la classe de récepteur d’événements. Si vous ne spécifiez pas un récepteur, la valeur par défaut est la classe de récepteur ou d’une structure dans laquelle **__unhook** est appelée.

## <a name="usage"></a>Utilisation

Peut s'utiliser dans une portée de fonction quelconque, notamment Main, en dehors de la classe de récepteur d'événements.

## <a name="remarks"></a>Notes

Utilisez la fonction intrinsèque **__unhook** dans un récepteur d’événements pour dissocier ou une méthode de gestionnaire à partir d’une méthode d’événement « décrocher ».

Il existe trois formes de **__unhook**. Vous pouvez utiliser la première forme (à quatre arguments) dans la plupart des cas. Vous pouvez utiliser la deuxième forme (à deux arguments) de **__unhook** uniquement pour un récepteur d’événements COM ; cela déconnecte l’interface d’événement complet. Vous pouvez utiliser la troisième forme (un argument) pour déconnecter tous les délégués de la source spécifiée.

Une valeur de retour différente de zéro indique qu'une erreur s'est produite (les événements managés lèvent une exception).

Si vous appelez **__unhook** sur un événement et un gestionnaire d’événements qui ne sont pas déjà raccordé, il n’a aucun effet.

Au moment de la compilation, le compilateur vérifie que l'événement existe et effectue la vérification du type de paramètre avec le gestionnaire spécifié.

À l’exception des événements COM, **__hook** et **__unhook** peut être appelée en dehors du récepteur d’événements.

Une alternative à l’utilisation de **__unhook** consiste à utiliser l’opérateur-=.

Pour plus d’informations sur le codage des événements managés dans la nouvelle syntaxe, consultez [événement](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
>  Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

Consultez [gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md) et [gestion des événements COM](../cpp/event-handling-in-com.md) pour obtenir des exemples.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)