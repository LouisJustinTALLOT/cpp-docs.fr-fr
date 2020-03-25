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
ms.openlocfilehash: 2a259b80b941e37e0c3040ad55894c114fe4bc82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160526"
---
# <a name="__unhook"></a>__unhook

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

- Événements C++ natifs : *SourceClass* est la classe de la source de l’événement et *EventMethod* est l’événement.

- Événements COM : *SourceClass* est l’interface de la source de l’événement et *EventMethod* est l’une de ses méthodes.

- Événements managés : *SourceClass* est la classe de la source de l’événement et *EventMethod* est l’événement.

*interface*<br/>
Nom de l’interface qui n’est pas raccordé du *récepteur*, uniquement pour les récepteurs d’événements com dans lesquels le paramètre *layout_dependent* de l’attribut [event_receiver](../windows/attributes/event-receiver.md) a la **valeur true**.

*source*<br/>
Pointeur vers une instance de la source d'événement. Selon le `type` de code spécifié dans `event_receiver`, la *source* peut être l’une des suivantes :

- Un pointeur d'objet source de l'événement natif.

- Pointeur basé sur `IUnknown`(source COM).

- Un pointeur d'objet managé (pour les événements managés).

**&** *ReceiverClass* `::` `HandlerMethod` un pointeur vers la méthode de gestionnaire d’événements à déconnecter d’un événement. Le gestionnaire est spécifié comme une méthode d’une classe ou une référence au même ; Si vous ne spécifiez pas le nom de la classe, **__unhook** suppose que la classe est celle dans laquelle elle est appelée.

- Événements C++ natifs : *ReceiverClass* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

- Événements COM : *ReceiverClass* est l’interface du récepteur d’événements et `HandlerMethod` est l’un de ses gestionnaires.

- Événements managés : *ReceiverClass* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

*Receiver*(facultatif) pointeur vers une instance de la classe de récepteur d’événements. Si vous ne spécifiez pas de récepteur, la valeur par défaut est la classe ou la structure du récepteur dans laquelle **__unhook** est appelée.

## <a name="usage"></a>Usage

Peut s'utiliser dans une portée de fonction quelconque, notamment Main, en dehors de la classe de récepteur d'événements.

## <a name="remarks"></a>Notes

Utilisez la fonction intrinsèque **__unhook** dans un récepteur d’événements pour dissocier ou déconnecter une méthode de gestionnaire d’une méthode d’événement.

Il existe trois formes de **__unhook**. Vous pouvez utiliser la première forme (à quatre arguments) dans la plupart des cas. Vous pouvez utiliser la deuxième forme (à deux arguments) de **__unhook** uniquement pour un récepteur d’événements com ; Cela décroche l’intégralité de l’interface d’événement. Vous pouvez utiliser la troisième forme (un argument) pour déconnecter tous les délégués de la source spécifiée.

Une valeur de retour différente de zéro indique qu'une erreur s'est produite (les événements managés lèvent une exception).

Si vous appelez **__unhook** sur un événement et un gestionnaire d’événements qui ne sont pas encore reliés, il n’aura aucun effet.

Au moment de la compilation, le compilateur vérifie que l'événement existe et effectue la vérification du type de paramètre avec le gestionnaire spécifié.

À l’exception des événements COM, **__hook** et **__unhook** peuvent être appelées en dehors du récepteur d’événements.

Une alternative à l’utilisation de **__unhook** consiste à utiliser l’opérateur-=.

Pour plus d’informations sur le codage des événements managés dans la nouvelle syntaxe, consultez [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
>  Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

Pour obtenir des exemples, consultez [gestion des événements dans C++ ](../cpp/event-handling-in-native-cpp.md) les gestion native et [des événements dans com](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
