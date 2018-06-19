---
title: Interfaces doubles multiples | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e23682bd0b7c923a1e377463405f84a6c6ee1221
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356717"
---
# <a name="multiple-dual-interfaces"></a>Interfaces doubles multiples
Vous pouvez souhaiter combiner les avantages d’une interface double (autrement dit, la souplesse de vtable et liaison tardive, ce qui la classe rend disponible pour les langages de script, ainsi que C++) avec les techniques de l’héritage multiple.  
  
 Bien qu’il soit possible d’exposer plusieurs interfaces doubles sur un objet COM, il n’est pas recommandé. S’il existe plusieurs interfaces doubles, il doit y avoir qu’un seul `IDispatch` interface exposée. Les techniques disponibles pour vous assurer que c’est le cas entraînent une perte de fonction ou de la complexité accrue du code. Le développeur que vous envisagez cette approche doit, évaluez les avantages et inconvénients.  
  
## <a name="exposing-a-single-idispatch-interface"></a>Exposition d’une Interface IDispatch unique  
 Il est possible d’exposer plusieurs interfaces doubles sur un seul objet en dérivant de deux ou plusieurs spécialisations de `IDispatchImpl`. Toutefois, si vous permettez aux clients d’interroger pour les `IDispatch` interface, vous devez utiliser le [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) macro (ou [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) pour spécifier la classe de base à utiliser pour le implémentation de `IDispatch`.  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]  
  
 Étant donné que seul `IDispatch` interface est exposée, clients peuvent accéder uniquement aux objets via la `IDispatch` interface ne sera pas en mesure d’accéder aux méthodes ou propriétés dans n’importe quel autre interface.  
  
## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Combinaison de plusieurs Interfaces doubles en une seule implémentation de IDispatch  
 ATL ne fournit aucune prise en charge pour la combinaison de plusieurs interfaces doubles en une seule implémentation de `IDispatch`. Toutefois, plusieurs approches sont possibles connus à combiner manuellement les interfaces, telles que la création d’une classe de modèle qui contient une union de particulières `IDispatch` interfaces, créer un nouvel objet pour effectuer le `QueryInterface` (fonction), ou en utilisant un implémentation typeinfo d’objets imbriqués pour créer le `IDispatch` interface.  
  
 Ces approches ont des problèmes avec des collisions d’espace de noms potentiels, ainsi que la complexité du code et la facilité de maintenance. Il n’est pas recommandé que vous créez plusieurs interfaces doubles.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)

