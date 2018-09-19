---
title: __unhook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unhook
- __unhook_cpp
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3efdce5bb7a9ab093a53b6a005492aecd509f560
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117294"
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
Le nom d’interface décroché à partir *récepteur*, uniquement pour les récepteurs d’événements COM dans lequel le *layout_dependent* paramètre de la [event_receiver](../windows/event-receiver.md) attribut est **true**.

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

Pour plus d’informations sur le codage des événements managés dans la nouvelle syntaxe, consultez [événement](../windows/event-cpp-component-extensions.md).

> [!NOTE]
>  Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

Consultez [gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md) et [gestion des événements COM](../cpp/event-handling-in-com.md) pour obtenir des exemples.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/event-source.md)<br/>
[event_receiver](../windows/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)