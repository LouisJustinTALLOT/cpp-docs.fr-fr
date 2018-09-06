---
title: Interfaces doubles multiples | Microsoft Docs
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
ms.openlocfilehash: 80bc2d4cc112c87c5c7a4e7d30f680631c1a1506
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758285"
---
# <a name="multiple-dual-interfaces"></a>Interfaces doubles multiples

Vous pouvez souhaiter combiner les avantages d’une interface double (autrement dit, la flexibilité de vtable et liaison tardive, ce qui la classe rend disponibles pour les langages de script, ainsi que C++) avec les techniques de l’héritage multiple.

Bien qu’il soit possible d’exposer plusieurs interfaces doubles sur un seul objet COM, il n’est pas recommandé. S’il existe plusieurs interfaces doubles, il doit y avoir qu’un seul `IDispatch` interface exposée. Les techniques disponibles pour vous assurer que c’est le cas entraînent une perte de fonction ou de la complexité croissante du code. Le développeur que vous envisagez cette approche doit évaluer avec soin les avantages et inconvénients.

## <a name="exposing-a-single-idispatch-interface"></a>Exposant une Interface IDispatch unique

Il est possible d’exposer plusieurs interfaces doubles sur un seul objet en dérivant à partir de deux ou plusieurs des spécialisations de `IDispatchImpl`. Toutefois, si vous autorisez les clients à interroger le `IDispatch` interface, vous devez utiliser le [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) macro (ou [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) pour spécifier quelle classe de base à utiliser pour le implémentation de `IDispatch`.

[!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]

Étant donné que qu’une seule `IDispatch` interface est exposée, les clients qui peuvent accéder uniquement aux objets via le `IDispatch` interface ne sera pas en mesure d’accéder aux méthodes ou propriétés dans n’importe quel autre interface.

## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Combinaison de plusieurs Interfaces doubles en une seule implémentation de IDispatch

ATL ne fournit aucune prise en charge pour la combinaison de plusieurs interfaces doubles en une seule implémentation de `IDispatch`. Toutefois, il existe plusieurs approches permettent de combiner manuellement les interfaces, telles que la création d’une classe de modèle qui contient une union du indépendamment `IDispatch` interfaces, créant un nouvel objet pour effectuer le `QueryInterface` (fonction), ou en utilisant un implémentation typeinfo d’objets imbriqués pour créer le `IDispatch` interface.

Ces approches présentent des problèmes avec les éventuelles collisions d’espace de noms, ainsi que la complexité du code et la facilité de maintenance. Il n’est pas recommandé que vous créez des interfaces doubles multiples.

## <a name="see-also"></a>Voir aussi

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)

