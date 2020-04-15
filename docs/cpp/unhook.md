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
ms.openlocfilehash: 221ffc30a9b8a40c44f8009dfa511b72aa160e01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337562"
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

**&***SourceClass* `::` *EventMethod* Un pointeur à la méthode de l’événement à partir de laquelle vous démélisez la méthode du gestionnaire d’événements:

- Événements natifs : *SourceClass* est la classe source de l’événement et *EventMethod* est l’événement.

- ÉVÉNEMENTS COM: *SourceClass* est l’interface source de l’événement et *EventMethod* est l’une de ses méthodes.

- Événements gérés : *SourceClass* est la classe source de l’événement et *EventMethod* est l’événement.

*interface*<br/>
Le nom de l’interface étant décom détaché du *récepteur*, uniquement pour *les* récepteurs d’événements COM dans lequel le layout_dependent paramètre de [l’attribut event_receiver](../windows/attributes/event-receiver.md) est **vrai**.

*Source*<br/>
Pointeur vers une instance de la source d'événement. Selon le `type` code `event_receiver`spécifié dans , *la source* peut être l’une des suivantes:

- Un pointeur d'objet source de l'événement natif.

- Un `IUnknown`pointeur basé sur le com.

- Un pointeur d'objet managé (pour les événements managés).

**&***ReceiverClassE* `::` `HandlerMethod` Un pointeur à la méthode du gestionnaire d’événements à démêler d’un événement. Le gestionnaire est spécifié comme méthode d’une classe ou une référence à la même chose; si vous ne spécifiez pas le nom de classe, **__unhook** suppose que la classe est celle dans laquelle elle s’appelle.

- Événements natifs de CMD : *ReceiverClass* est la classe des récepteurs d’événements et `HandlerMethod` le gestionnaire.

- ÉVÉNEMENTS COM : *ReceiverClass* est `HandlerMethod` l’interface du récepteur d’événements et est l’un de ses gestionnaires.

- Événements gérés : *ReceiverClass* est `HandlerMethod` la classe de récepteur d’événements et le gestionnaire.

*récepteur*(facultatif) Un pointeur à une instance de la classe de récepteur d’événement. Si vous ne spécifiez pas un récepteur, le défaut est la classe ou la structure du récepteur dans laquelle **__unhook** est appelée.

## <a name="usage"></a>Usage

Peut s'utiliser dans une portée de fonction quelconque, notamment Main, en dehors de la classe de récepteur d'événements.

## <a name="remarks"></a>Notes

Utilisez la fonction intrinsèque **__unhook** dans un récepteur d’événement pour dissocier ou « démooker » une méthode de gestionnaire d’une méthode d’événement.

Il existe trois formes de **__unhook**. Vous pouvez utiliser la première forme (à quatre arguments) dans la plupart des cas. Vous pouvez utiliser la deuxième forme (à deux arguments) de **__unhook** uniquement pour un récepteur d’événements COM; cela décodait toute l’interface de l’événement. Vous pouvez utiliser la troisième forme (un argument) pour déconnecter tous les délégués de la source spécifiée.

Une valeur de retour différente de zéro indique qu'une erreur s'est produite (les événements managés lèvent une exception).

Si vous appelez **__unhook** sur un gestionnaire d’événements et d’événements qui ne sont pas déjà accrochés, il n’aura aucun effet.

Au moment de la compilation, le compilateur vérifie que l'événement existe et effectue la vérification du type de paramètre avec le gestionnaire spécifié.

À l’exception des événements COM, **__hook** et **__unhook** peuvent être appelés en dehors du récepteur de l’événement.

Une alternative à l’utilisation **de __unhook** est d’utiliser l’opérateur.

Pour plus d’informations sur le codage des événements gérés dans la nouvelle syntaxe, voir [événement](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

Voir [la manipulation d’événements dans le C et](../cpp/event-handling-in-native-cpp.md) la manipulation [d’événements autochtones dans COM](../cpp/event-handling-in-com.md) pour les échantillons.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
