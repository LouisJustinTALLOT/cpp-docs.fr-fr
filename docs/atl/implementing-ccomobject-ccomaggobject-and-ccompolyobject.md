---
title: Implémentation de CComObject, CComAggObject et CComPolyObject
ms.date: 11/04/2016
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
ms.openlocfilehash: e2413c8fb9f5722f0245883c947067387838e57f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808311"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implémentation de CComObject, CComAggObject et CComPolyObject

Les classes de modèle [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), et [CComPolyObject](../atl/reference/ccompolyobject-class.md) sont toujours les classes les plus dérivées dans la chaîne d’héritage. Il est de leur responsabilité pour gérer toutes les méthodes dans `IUnknown`: `QueryInterface`, `AddRef`, et `Release`. En outre, `CComAggObject` et `CComPolyObject` (lorsqu’il est utilisé pour les objets agrégées) fournissent le décompte des références spéciales et `QueryInterface` sémantique requise pour l’inconnu intérieur.

Si `CComObject`, `CComAggObject`, ou `CComPolyObject` est utilisée dépend de si vous déclarez l’une des macros suivantes (ou aucun) :

|Macro|Effet|
|-----------|------------|
|DECLARE_NOT_AGGREGATABLE|Utilise toujours `CComObject`.|
|DECLARE_AGGREGATABLE|Utilise `CComAggObject` si l’objet est agrégée et `CComObject` si elle n’est pas. `CComCoClass` contient cette macro si aucune des macros DECLARE_ * _AGGREGATABLE n’est déclarée dans votre classe, il s’agit de la valeur par défaut.|
|DECLARE_ONLY_AGGREGATABLE|Utilise toujours `CComAggObject`. Retourne une erreur si l’objet n’est pas agrégée.|
|DECLARE_POLY_AGGREGATABLE|ATL crée une instance de **CComPolyObject\<CYourClass >** lorsque `IClassFactory::CreateInstance` est appelée. Lors de la création, la valeur de l’inconnu extérieur est vérifiée. Si sa valeur est NULL, `IUnknown` est implémentée pour un objet non regroupées en agrégats. Si l’inconnu extérieur n’est pas NULL, `IUnknown` est implémentée pour un objet agrégé.|

L’avantage d’utiliser `CComAggObject` et `CComObject` qui est l’implémentation de `IUnknown` est optimisé pour le type d’objet en cours de création. Par exemple, un objet non regroupées en agrégats doit uniquement un décompte de références, alors qu’un objet agrégé doit un décompte de références pour l’inconnu intérieur et un pointeur vers l’inconnu extérieur.

L’avantage d’utiliser `CComPolyObject` est d’éviter d’avoir à la fois `CComAggObject` et `CComObject` dans votre module pour gérer les cas regroupés et. Un seul `CComPolyObject` objet gère les deux cas. Cela ne signifie qu’une seule copie de vtable et une seule copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, à l’aide de `CComPolyObject` peut entraîner une taille légèrement supérieure de module, car elle n’est pas optimisée pour un objet regroupé ou, comme le sont `CComAggObject` et `CComObject`.

## <a name="see-also"></a>Voir aussi

[Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Agrégation et macros de fabrique de classe](../atl/reference/aggregation-and-class-factory-macros.md)
