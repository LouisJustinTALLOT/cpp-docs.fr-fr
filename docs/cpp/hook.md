---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: c4887d85e01344c171fb0fdfe957f2d8a669ff6a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58771667"
---
# <a name="hook"></a>__hook

Associe une méthode de gestionnaire à un événement.

## <a name="syntax"></a>Syntaxe

```
long __hook(
    &SourceClass::EventMethod,
    source,
    &ReceiverClass::HandlerMethod
    [, receiver = this]
);
long __hook(
    interface,
    source
);
```

### <a name="parameters"></a>Paramètres

*&SourceClass::EventMethod*<br/>
Pointeur vers la méthode d'événement à laquelle vous raccordez la méthode de gestionnaire d'événements :

- Événements natifs C++ : *SourceClass* est la classe source d’événements et *EventMethod* est l’événement.

- Événements COM : *SourceClass* est l’interface de source d’événements et *EventMethod* est une de ses méthodes.

- Événements managés : *SourceClass* est la classe source d’événements et *EventMethod* est l’événement.

*interface*<br/>
Le nom d’interface raccordé à *récepteur*, uniquement pour les récepteurs d’événements COM dans lequel le *layout_dependent* paramètre de la [event_receiver](../windows/attributes/event-receiver.md) attribut est **true**.

*source*<br/>
Pointeur vers une instance de la source d'événement. En fonction du code `type` spécifié dans `event_receiver`, *source* peut prendre l’une des opérations suivantes :

- Un pointeur d'objet source de l'événement natif.

- Un `IUnknown`-en fonction de pointeur (source COM).

- Un pointeur d'objet managé (pour les événements managés).

*&ReceiverClass::HandlerMethod*<br/>
Pointeur vers la méthode de gestionnaire d'événements à raccorder à un événement. Le gestionnaire est spécifié en tant que méthode d’une classe ou une référence à la même ; Si vous ne spécifiez pas le nom de classe, **__hook** part du principe que la classe est que dans lequel elle est appelée.

- Événements natifs C++ : *ReceiverClass* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

- Événements COM : *ReceiverClass* est l’interface de récepteur d’événements et `HandlerMethod` est un de ses gestionnaires.

- Événements managés : *ReceiverClass* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

*receiver*<br/>
(Facultatif) Pointeur vers une instance de la classe de récepteur d’événements. Si vous ne spécifiez pas un récepteur, la valeur par défaut est la classe de récepteur ou d’une structure dans laquelle **__hook** est appelée.

## <a name="usage"></a>Utilisation

Peut s'utiliser dans une portée de fonction quelconque, notamment Main, en dehors de la classe de récepteur d'événements.

## <a name="remarks"></a>Notes

Utilisez la fonction intrinsèque **__hook** dans un récepteur d’événements pour associer ou raccorder une méthode de gestionnaire à une méthode d’événement. Le gestionnaire spécifié est ensuite appelé lorsque la source déclenche l'événement spécifié. Vous pouvez raccorder plusieurs gestionnaires à un même événement ou raccorder plusieurs événements à un même gestionnaire.

Il existe deux formes de **__hook**. Vous pouvez utiliser la première forme (à quatre arguments) dans la plupart des cas, en particulier, pour les récepteurs d’événements COM dans lequel le *layout_dependent* paramètre de la [event_receiver](../windows/attributes/event-receiver.md) attribut est **false** .

Dans ces cas-là, vous n'avez pas besoin de raccorder toutes les méthodes dans une interface avant de déclencher un événement sur l'une des méthodes ; seule la méthode qui gère l'événement doit être raccordée. Vous pouvez utiliser la deuxième forme (à deux arguments) de **__hook** uniquement pour un récepteur d’événements COM dans lequel *layout_dependent* **= true**.

**__hook** retourne une valeur longue. Une valeur de retour différente de zéro indique qu'une erreur s'est produite (les événements managés lèvent une exception).

Le compilateur vérifie l'existence d'un événement et la conformité de la signature d'événement à la signature du délégué.

À l’exception des événements COM, **__hook** et **__unhook** peut être appelée en dehors du récepteur d’événements.

Une alternative à l’utilisation de **__hook** consiste à utiliser l’opérateur +=.

Pour plus d’informations sur le codage des événements managés dans la nouvelle syntaxe, consultez [événement](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

Consultez [gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md) et [gestion des événements COM](../cpp/event-handling-in-com.md) pour obtenir des exemples.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Gestion des événements](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
