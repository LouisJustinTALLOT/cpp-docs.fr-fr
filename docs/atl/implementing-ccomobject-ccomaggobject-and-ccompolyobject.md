---
title: Implémentation de CComObject, CComAggObject et CComPolyObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CComPolyObject
- CComAggObject
- CComObject
dev_langs:
- C++
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ac45a6edbe606ba445ed3ae58cfde348f83e4de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356339"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implémentation de CComObject, CComAggObject et CComPolyObject
Les classes de modèle [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), et [CComPolyObject](../atl/reference/ccompolyobject-class.md) sont toujours les classes les plus dérivées dans la chaîne d’héritage. Il est leur responsabilité de gérer toutes les méthodes dans **IUnknown**: `QueryInterface`, `AddRef`, et **version**. En outre, `CComAggObject` et `CComPolyObject` (lorsque utilisé pour les objets regroupés en agrégats) fournissent le décompte des références spéciales et `QueryInterface` sémantique requise pour l’inconnu intérieur.  
  
 Si `CComObject`, `CComAggObject`, ou `CComPolyObject` est utilisée dépend de si vous déclarez l’une des macros suivantes (ou aucun) :  
  
|Macro|Effet|  
|-----------|------------|  
|`DECLARE_NOT_AGGREGATABLE`|Utilise toujours `CComObject`.|  
|`DECLARE_AGGREGATABLE`|Utilise `CComAggObject` si l’objet est agrégée et `CComObject` si elle n’est pas. `CComCoClass` contient cette macro si aucun de la **macros DECLARE_\*_AGGREGATABLE** macros sont déclarés dans votre classe, il s’agit de la valeur par défaut.|  
|`DECLARE_ONLY_AGGREGATABLE`|Utilise toujours `CComAggObject`. Retourne une erreur si l’objet n’est pas agrégée.|  
|`DECLARE_POLY_AGGREGATABLE`|ATL crée une instance de **CComPolyObject\<CYourClass >** lorsque **IClassFactory::CreateInstance** est appelée. Lors de la création, la valeur de l’inconnu extérieur est vérifiée. S’il s’agit **NULL**, **IUnknown** est implémenté pour un objet brutes et non agrégée. Si l’inconnu extérieur n’est pas **NULL**, **IUnknown** est implémenté pour un objet.|  
  
 L’avantage d’utiliser `CComAggObject` et `CComObject` qui est l’implémentation de **IUnknown** est optimisé pour le type d’objet en cours de création. Par exemple, un objet brutes et non agrégée doit uniquement un décompte de références, tant qu’un objet nécessite un décompte de références pour l’inconnu interne et un pointeur vers l’inconnu extérieur.  
  
 L’avantage d’utiliser `CComPolyObject` est que vous n’avez pas à la fois `CComAggObject` et `CComObject` dans votre module pour gérer les cas regroupés et. Un seul `CComPolyObject` objet gère les deux cas. Cela ne signifie qu’une seule copie de vtable et une seule copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, à l’aide de `CComPolyObject` peut entraîner une taille légèrement supérieure de module, car il n’est pas optimisée pour un objet regroupé ou, comme le sont `CComAggObject` et `CComObject`.  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)   
 [Agrégation et macros de fabrique de classe](../atl/reference/aggregation-and-class-factory-macros.md)

