---
title: Gestion des événements
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: cf16ea0e6e14981f1105456a5f17d68c05a9c3fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189206"
---
# <a name="event-handling"></a>Gestion des événements

La gestion des événements est principalement prise en chargeC++ pour les classes COM (classes qui implémentent des objets com, généralement à l’aide de classes ATL ou de l’attribut [coclasse](../windows/coclass.md) ). Pour plus d’informations, consultez [gestion des événements dans com](../cpp/event-handling-in-com.md).

La gestion des événements est également prise en charge pour les classes C++ natives (les classes C++ qui n'implémentent pas les objets COM). Cependant, cette prise en charge est déconseillée et sera supprimée dans une version ultérieure.  Pour plus d’informations, consultez [gestion des événements C++en mode natif ](../cpp/event-handling-in-native-cpp.md).

La gestion des événements prend en charge l'utilisation de thread unique et multithread et protège les données de l'accès multithread simultané. Elle vous permet également de dériver des sous-classes de classes de sources d'événements ou de récepteurs, et de prendre en charge la source/réception d'événements étendue dans la classe dérivée.

Le compilateur C++ Microsoft comprend des attributs et des mots clés pour déclarer des événements et des gestionnaires d’événements. Les attributs et les mots clés d'événement peuvent être utilisés dans les programmes CLR et dans les programmes C++ natifs.

|Rubrique|Description|
|-----------|-----------------|
|[event_source](../windows/attributes/event-source.md)|Crée une source d'événement.|
|[event_receiver](../windows/attributes/event-receiver.md)|Crée un récepteur d'événements (récepteur).|
|[__event](../cpp/event.md)|Déclare un événement.|
|[__raise](../cpp/raise.md)|Met en évidence le site d'appel d'un événement.|
|[__hook](../cpp/hook.md)|Associe une méthode de gestionnaire à un événement.|
|[__unhook](../cpp/unhook.md)|Dissocie une méthode de gestionnaire d'un événement.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
