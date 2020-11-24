---
title: Gestion des événements
description: Découvrez comment les extensions Microsoft C++ prennent en charge la gestion des événements COM et natifs.
ms.date: 11/20/2020
helpviewer_keywords:
- event handling [C++]
ms.openlocfilehash: de8cd6dfac2b83e850ec62ff88e192d1c60e427e
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483125"
---
# <a name="event-handling"></a>Gestion des événements

La gestion des événements est principalement prise en charge pour les classes COM (les classes C++ qui implémentent des objets COM, généralement à l’aide de classes ATL ou de l’attribut [coclasse](../windows/attributes/coclass.md) ). Pour plus d’informations, consultez [gestion des événements dans com](../cpp/event-handling-in-com.md).

La gestion des événements est également prise en charge pour les classes C++ natives (classes C++ qui n’implémentent pas d’objets COM). La prise en charge de la gestion des événements C++ natif est déconseillée et sera supprimée dans une version ultérieure. Pour plus d’informations, consultez [gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md).

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode de conformité.

La gestion des événements prend en charge l’utilisation monothread et multithread. Il protège les données de l’accès multithread simultané. Vous pouvez dériver des sous-classes à partir de classes de source ou de récepteur d’événements. Ces sous-classes prennent en charge l’approvisionnement et la réception des événements étendus.

Le compilateur Microsoft C++ comprend des attributs et des mots clés pour déclarer des événements et des gestionnaires d’événements. Les attributs et les mots clés d'événement peuvent être utilisés dans les programmes CLR et dans les programmes C++ natifs.

| Article | Description |
|--|--|
| [`event_source`](../windows/attributes/event-source.md) | Crée une source d'événement. |
| [`event_receiver`](../windows/attributes/event-receiver.md) | Crée un récepteur d'événements (récepteur). |
| [`__event`](../cpp/event.md) | Déclare un événement. |
| [`__raise`](../cpp/raise.md) | Met en évidence le site d'appel d'un événement. |
| [`__hook`](../cpp/hook.md) | Associe une méthode de gestionnaire à un événement. |
| [`__unhook`](../cpp/unhook.md) | Dissocie une méthode de gestionnaire d’un événement. |

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)\
[Mots clés](../cpp/keywords-cpp.md)
