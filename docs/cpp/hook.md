---
title: __hook
description: Découvrez comment utiliser le mot clé d’extension Microsoft C++ `__hook` pour la gestion des événements natifs.
ms.date: 11/20/2020
f1_keywords:
- __hook_cpp
- __hook
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.openlocfilehash: 2a2bde221c53f0e1d420e2ab3a88eb299f6c284c
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483254"
---
# <a name="__hook-keyword"></a>`__hook` mot

Associe une méthode de gestionnaire à un événement.

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode de conformité.

## <a name="syntax"></a>Syntaxe

```cpp
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

*`&SourceClass::EventMethod`*\
Pointeur vers la méthode d'événement à laquelle vous raccordez la méthode de gestionnaire d'événements :

- Événements C++ natifs : *`SourceClass`* est la classe source de l’événement et *`EventMethod`* est l’événement.

- Événements COM : *`SourceClass`* est l’interface source de l’événement et *`EventMethod`* est l’une de ses méthodes.

- Événements managés : *`SourceClass`* est la classe source de l’événement et *`EventMethod`* est l’événement.

*`interface`*\
Nom de l’interface qui est raccordé à *`receiver`* , uniquement pour les récepteurs d’événements com dans lesquels le *`layout_dependent`* paramètre de l' [`event_receiver`](../windows/attributes/event-receiver.md) attribut a la valeur **`true`** .

*`source`*\
Pointeur vers une instance de la source d'événement. Selon le code `type` spécifié dans `event_receiver` , *`source`* peut être l’un des types suivants :

- Un pointeur d'objet source de l'événement natif.

- `IUnknown`Pointeur basé sur (source com).

- Un pointeur d'objet managé (pour les événements managés).

*`&ReceiverClass::HandlerMethod`*\
Pointeur vers la méthode de gestionnaire d'événements à raccorder à un événement. Le gestionnaire est spécifié comme une méthode d’une classe ou une référence au même. Si vous ne spécifiez pas le nom de la classe, **`__hook`** suppose que la classe est celle à partir de laquelle elle est appelée.

- Événements C++ natifs : *`ReceiverClass`* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

- Événements COM : *`ReceiverClass`* est l’interface de récepteur d’événements et *`HandlerMethod`* est l’un de ses gestionnaires.

- Événements managés : *`ReceiverClass`* est la classe de récepteur d’événements et *`HandlerMethod`* est le gestionnaire.

*`receiver`*\
Facultatif Pointeur vers une instance de la classe de récepteur d’événements. Si vous ne spécifiez pas de récepteur, la valeur par défaut est la classe ou la structure du récepteur dans laquelle **`__hook`** est appelé.

## <a name="usage"></a>Usage

Peut s'utiliser dans une portée de fonction quelconque, notamment Main, en dehors de la classe de récepteur d'événements.

## <a name="remarks"></a>Notes

Utilisez la fonction intrinsèque **`__hook`** dans un récepteur d’événements pour associer ou raccorder une méthode de gestionnaire à une méthode d’événement. Le gestionnaire spécifié est ensuite appelé lorsque la source déclenche l'événement spécifié. Vous pouvez raccorder plusieurs gestionnaires à un même événement ou raccorder plusieurs événements à un même gestionnaire.

Il existe deux formes de **`__hook`** . Vous pouvez utiliser la première forme (à quatre arguments) dans la plupart des cas, en particulier pour les récepteurs d’événements COM dans lesquels le paramètre *layout_dependent* de l' [`event_receiver`](../windows/attributes/event-receiver.md) attribut est **`false`** .

Dans ce cas, vous n’avez pas besoin de raccorder toutes les méthodes dans une interface avant de déclencher un événement sur l’une des méthodes. Il vous suffit de raccorder la méthode qui gère l’événement. Vous pouvez utiliser la deuxième forme (à deux arguments) de **`__hook`** uniquement pour un récepteur d’événements com dans lequel *`layout_dependent`* **`= true`** .

**`__hook`** retourne une valeur de type long. Une valeur de retour différente de zéro indique qu'une erreur s'est produite (les événements managés lèvent une exception).

Le compilateur vérifie l'existence d'un événement et la conformité de la signature d'événement à la signature du délégué.

Vous pouvez appeler **`__hook`** et à l' **`__unhook`** extérieur du récepteur d’événements, à l’exception des événements com.

Une alternative à l’utilisation de **`__hook`** est l’utilisation de l’opérateur + =.

Pour plus d’informations sur le codage des événements managés dans la nouvelle syntaxe, consultez [`event`](../extensions/event-cpp-component-extensions.md) .

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

Pour obtenir des exemples, consultez [gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md) et [gestion des événements dans com](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Voir aussi

[Mot](../cpp/keywords-cpp.md)\
[Gestion des événements](../cpp/event-handling.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__event`](../cpp/event.md)\
[`__unhook`](../cpp/unhook.md)\
[`__raise`](../cpp/raise.md)
