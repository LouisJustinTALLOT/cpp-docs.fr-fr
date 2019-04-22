---
title: Gestion des événements
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [C++], event handling
- intrinsic functions [C++], event handling
- event handling [C++], Visual C++
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: 4c6701f04544b336de97196e8b65f4d0cd4be296
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769470"
---
# <a name="event-handling"></a>Gestion des événements

Gestion des événements sont principalement prise en charge pour les classes COM (classes C++ qui implémentent des objets COM, généralement à l’aide de classes ATL ou [coclasse](../windows/coclass.md) attribut). Pour plus d’informations, consultez [gestion des événements COM](../cpp/event-handling-in-com.md).

La gestion des événements est également prise en charge pour les classes C++ natives (les classes C++ qui n'implémentent pas les objets COM). Cependant, cette prise en charge est déconseillée et sera supprimée dans une version ultérieure.  Pour plus d’informations, consultez [gestion des événements en C++ natif](../cpp/event-handling-in-native-cpp.md).

La gestion des événements prend en charge l'utilisation de thread unique et multithread et protège les données de l'accès multithread simultané. Elle vous permet également de dériver des sous-classes de classes de sources d'événements ou de récepteurs, et de prendre en charge la source/réception d'événements étendue dans la classe dérivée.

Visual C++ inclut des attributs et des mots clés pour déclarer des événements et des gestionnaires d'événements. Les attributs et les mots clés d'événement peuvent être utilisés dans les programmes CLR et dans les programmes C++ natifs.

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