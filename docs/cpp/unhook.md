---
title: __unhook
description: Découvrez comment utiliser le mot clé d’extension Microsoft C++ `__unhook` pour la gestion des événements natifs.
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.openlocfilehash: 74f8b814ea23c5513b7b73bf90ef59984742a266
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483319"
---
# <a name="__unhook-keyword"></a>`__unhook` mot

Dissocie une méthode de gestionnaire d’un événement.

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode de conformité.

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

### <a name="parameters"></a>Paramètres

*`&SourceClass::EventMethod`*\
Pointeur vers la méthode d'événement à partir de laquelle vous décrochez la méthode de gestionnaire d'événements :

- Événements C++ natifs : *`SourceClass`* est la classe source de l’événement et *`EventMethod`* est l’événement.

- Événements COM : *`SourceClass`* est l’interface source de l’événement et *`EventMethod`* est l’une de ses méthodes.

- Événements managés : *`SourceClass`* est la classe source de l’événement et *`EventMethod`* est l’événement.

*`interface`*\
Nom de l’interface qui est décrochée du *récepteur*, uniquement pour les récepteurs d’événements com dans lesquels le paramètre *layout_dependent* de l' [`event_receiver`](../windows/attributes/event-receiver.md) attribut est **`true`** .

*`source`*\
Pointeur vers une instance de la source d'événement. En fonction du code `type` spécifié dans `event_receiver` , la *source* peut être l’un des types suivants :

- Un pointeur d'objet source de l'événement natif.

- `IUnknown`Pointeur basé sur (source com).

- Un pointeur d'objet managé (pour les événements managés).

*`&ReceiverClass::HandlerMethod`* Pointeur vers la méthode de gestionnaire d’événements à déconnecter d’un événement. Le gestionnaire est spécifié comme une méthode d’une classe ou une référence au même ; Si vous ne spécifiez pas le nom de la classe, **`__unhook`** suppose que la classe est celle dans laquelle elle est appelée.

- Événements C++ natifs : *`ReceiverClass`* est la classe de récepteur d’événements et `HandlerMethod` est le gestionnaire.

- Événements COM : *`ReceiverClass`* est l’interface de récepteur d’événements et *`HandlerMethod`* est l’un de ses gestionnaires.

- Événements managés : *`ReceiverClass`* est la classe de récepteur d’événements et *`HandlerMethod`* est le gestionnaire.

*`receiver`* facultatif Pointeur vers une instance de la classe de récepteur d’événements. Si vous ne spécifiez pas de récepteur, la valeur par défaut est la classe ou la structure du récepteur dans laquelle **`__unhook`** est appelé.

## <a name="usage"></a>Usage

Peut être utilisée dans n’importe quelle portée de fonction, y compris `main` , en dehors de la classe de récepteur d’événements.

## <a name="remarks"></a>Notes

Utilisez la fonction intrinsèque **`__unhook`** dans un récepteur d’événements pour dissocier ou déconnecter une méthode de gestionnaire d’une méthode d’événement.

Il existe trois formes de **`__unhook`** . Vous pouvez utiliser la première forme (à quatre arguments) dans la plupart des cas. Vous pouvez utiliser la deuxième forme (à deux arguments) de **`__unhook`** uniquement pour un récepteur d’événements com ; cela déconnecte l’intégralité de l’interface d’événement. Vous pouvez utiliser la troisième forme (un argument) pour déconnecter tous les délégués de la source spécifiée.

Une valeur de retour différente de zéro indique qu'une erreur s'est produite (les événements managés lèvent une exception).

Si vous appelez **`__unhook`** sur un événement et un gestionnaire d’événements qui ne sont pas déjà raccordés, il n’aura aucun effet.

Au moment de la compilation, le compilateur vérifie que l'événement existe et effectue la vérification du type de paramètre avec le gestionnaire spécifié.

Vous pouvez appeler **`__hook`** et à l' **`__unhook`** extérieur du récepteur d’événements, à l’exception des événements com.

Une alternative à l’utilisation de **`__unhook`** est l’utilisation de l’opérateur-=.

Pour plus d’informations sur le codage des événements managés dans la nouvelle syntaxe, consultez [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

Pour obtenir des exemples, consultez [gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md) et [gestion des événements dans com](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Voir aussi

[Mot](../cpp/keywords-cpp.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__event`](../cpp/event.md)\
[`__hook`](../cpp/hook.md)\
[`__raise`](../cpp/raise.md)
