---
description: 'En savoir plus sur : plusieurs interfaces doubles'
title: Plusieurs interfaces doubles
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
ms.openlocfilehash: d90c0176b3165cc0e5b976a29ec58b58fd3a7a56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159413"
---
# <a name="multiple-dual-interfaces"></a>Plusieurs interfaces doubles

Vous pouvez combiner les avantages d’une interface double (autrement dit, la flexibilité des liaisons vtable et tardive, rendant ainsi la classe disponible pour les langages de script et C++) avec les techniques d’héritage multiple.

Bien qu’il soit possible d’exposer plusieurs interfaces doubles sur un objet COM unique, ce n’est pas recommandé. S’il existe plusieurs interfaces doubles, une seule interface doit être `IDispatch` exposée. Les techniques disponibles pour s’assurer qu’il s’agit d’un cas de pénalités, telles que la perte de fonction ou l’augmentation de la complexité du code. Le développeur qui envisage cette approche doit soigneusement évaluer les avantages et les inconvénients.

## <a name="exposing-a-single-idispatch-interface"></a>Exposition d’une seule interface IDispatch

Il est possible d’exposer plusieurs interfaces doubles sur un seul objet en dérivant d’au moins deux spécialisations de `IDispatchImpl` . Toutefois, si vous autorisez les clients à interroger l' `IDispatch` interface, vous devez utiliser la macro [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) (ou [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) pour spécifier la classe de base à utiliser pour l’implémentation de `IDispatch` .

[!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]

Étant donné qu’une seule `IDispatch` interface est exposée, les clients qui peuvent accéder uniquement à vos objets par le biais de l’interface ne seront `IDispatch` pas en mesure d’accéder aux méthodes ou propriétés de toute autre interface.

## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Combinaison de plusieurs interfaces doubles en une seule implémentation de IDispatch

ATL ne fournit aucune prise en charge pour combiner plusieurs interfaces doubles en une seule implémentation de `IDispatch` . Toutefois, il existe plusieurs approches connues pour combiner manuellement les interfaces, telles que la création d’une classe basée sur un modèle qui contient une Union des `IDispatch` interfaces distinctes, la création d’un nouvel objet pour exécuter la `QueryInterface` fonction, ou l’utilisation d’une implémentation TypeInfo d’objets imbriqués pour créer l' `IDispatch` interface.

Ces approches présentent des problèmes avec les conflits d’espaces de noms potentiels, ainsi que la complexité et la maintenabilité du code. Il n’est pas recommandé de créer plusieurs interfaces doubles.

## <a name="see-also"></a>Voir aussi

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)
