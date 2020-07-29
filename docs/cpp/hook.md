---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: 5a0eaf0a3bc0617dbcd1f43805af8a95291e7e47
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188165"
---
# <a name="__hook"></a>__hook

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

*&SourceClass :: EventMethod*<br/>
Pointeur vers la méthode d'événement à laquelle vous raccordez la méthode de gestionnaire d'événements :

- Événements C++ natifs : *SourceClass* est la classe de la source de l’événement et *EventMethod* est l’événement.

- Événements COM : *SourceClass* est l’interface de la source de l’événement et *EventMethod* est l’une de ses méthodes.

- Événements managés : *SourceClass* est la classe de la source de l’événement et *EventMethod* est l’événement.

*interface*<br/>
Nom de l’interface qui est raccordé au *récepteur*, uniquement pour les récepteurs d’événements com dans lesquels le paramètre *layout_dependent* de l’attribut [event_receiver](../windows/attributes/event-receiver.md) est **`true`** .

*source*<br/>
Pointeur vers une instance de la source d'événement. En fonction du code `type` spécifié dans `event_receiver` , la *source* peut être l’une des suivantes :

- Un pointeur d'objet source de l'événement natif.

- `IUnknown`Pointeur basé sur (source com).

- Un pointeur d'objet managé (pour les événements managés).

*&ReceiverClass :: HandlerMethod*<br/>
Pointeur vers la méthode de gestionnaire d'événements à raccorder à un événement. Le gestionnaire est spécifié comme une méthode d’une classe ou une référence au même ; Si vous ne spécifiez pas le nom de la classe, **`__hook`** suppose que la classe est celle dans laquelle elle est appelée.

- Événements C++ natifs : *ReceiverClass* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

- Événements COM : *ReceiverClass* est l’interface du récepteur d’événements et `HandlerMethod` est l’un de ses gestionnaires.

- Événements managés : *ReceiverClass* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

*distillat*<br/>
Facultatif Pointeur vers une instance de la classe de récepteur d’événements. Si vous ne spécifiez pas de récepteur, la valeur par défaut est la classe ou la structure du récepteur dans laquelle **`__hook`** est appelé.

## <a name="usage"></a>Usage

Peut s'utiliser dans une portée de fonction quelconque, notamment Main, en dehors de la classe de récepteur d'événements.

## <a name="remarks"></a>Notes

Utilisez la fonction intrinsèque **`__hook`** dans un récepteur d’événements pour associer ou raccorder une méthode de gestionnaire à une méthode d’événement. Le gestionnaire spécifié est ensuite appelé lorsque la source déclenche l'événement spécifié. Vous pouvez raccorder plusieurs gestionnaires à un même événement ou raccorder plusieurs événements à un même gestionnaire.

Il existe deux formes de **`__hook`** . Vous pouvez utiliser la première forme (à quatre arguments) dans la plupart des cas, en particulier pour les récepteurs d’événements COM dans lesquels le paramètre *layout_dependent* de l’attribut [event_receiver](../windows/attributes/event-receiver.md) est **`false`** .

Dans ces cas-là, vous n'avez pas besoin de raccorder toutes les méthodes dans une interface avant de déclencher un événement sur l'une des méthodes ; seule la méthode qui gère l'événement doit être raccordée. Vous pouvez utiliser la deuxième forme (à deux arguments) de **`__hook`** uniquement pour un récepteur d’événements com dans lequel *layout_dependent* **= true**.

**`__hook`** retourne une valeur de type long. Une valeur de retour différente de zéro indique qu'une erreur s'est produite (les événements managés lèvent une exception).

Le compilateur vérifie l'existence d'un événement et la conformité de la signature d'événement à la signature du délégué.

À l’exception des événements COM, **`__hook`** et **`__unhook`** peuvent être appelés en dehors du récepteur d’événements.

Une alternative à l’utilisation de **`__hook`** est l’utilisation de l’opérateur + =.

Pour plus d’informations sur le codage des événements managés dans la nouvelle syntaxe, consultez [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

Pour obtenir des exemples, consultez [gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md) et [gestion des événements dans com](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Gestion des événements](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
