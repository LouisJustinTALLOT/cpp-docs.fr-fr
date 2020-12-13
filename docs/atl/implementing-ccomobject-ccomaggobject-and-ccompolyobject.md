---
description: 'En savoir plus sur : implémentation de CComObject, CComAggObject et CComPolyObject'
title: Implémentation de CComObject, CComAggObject et CComPolyObject
ms.date: 11/04/2016
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
ms.openlocfilehash: e0cc8a6b65ec9d85249cd47e2f43cf1bec2b8ce2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147769"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implémentation de CComObject, CComAggObject et CComPolyObject

Les classes de modèle [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)et [CComPolyObject](../atl/reference/ccompolyobject-class.md) sont toujours les classes les plus dérivées dans la chaîne d’héritage. Il incombe de gérer toutes les méthodes dans `IUnknown` : `QueryInterface` , `AddRef` et `Release` . En outre, `CComAggObject` et `CComPolyObject` (en cas d’utilisation pour les objets agrégés) fournissent le décompte de références spécial et la `QueryInterface` sémantique requis pour le interne inconnu.

Le fait de savoir si `CComObject` , `CComAggObject` ou `CComPolyObject` est utilisé varie selon que vous déclarez une (ou aucune) des macros suivantes :

|Macro|Résultat|
|-----------|------------|
|DECLARE_NOT_AGGREGATABLE|Utilise toujours `CComObject` .|
|DECLARE_AGGREGATABLE|Utilise `CComAggObject` si l’objet est agrégé et `CComObject` si ce n’est pas le cas. `CComCoClass` contient cette macro de sorte que si aucune des macros DECLARE_ * _AGGREGATABLE n’est déclarée dans votre classe, il s’agit de la valeur par défaut.|
|DECLARE_ONLY_AGGREGATABLE|Utilise toujours `CComAggObject` . Retourne une erreur si l’objet n’est pas agrégé.|
|DECLARE_POLY_AGGREGATABLE|ATL crée une instance de **CComPolyObject \<CYourClass>** quand `IClassFactory::CreateInstance` est appelé. Pendant la création, la valeur de l’externe Unknown est vérifiée. Si la valeur est NULL, `IUnknown` est implémenté pour un objet non agrégé. Si le inconnu externe n’est pas NULL, `IUnknown` est implémenté pour un objet agrégé.|

L’avantage de l’utilisation de `CComAggObject` et de `CComObject` est que l’implémentation de `IUnknown` est optimisée pour le type d’objet en cours de création. Par exemple, un objet non agrégé a uniquement besoin d’un nombre de références, tandis qu’un objet agrégé a besoin à la fois d’un décompte de références pour le interne inconnu et d’un pointeur vers l’extérieur inconnu.

L’avantage de l’utilisation de `CComPolyObject` est que vous évitez que `CComAggObject` et `CComObject` dans votre module ne gèrent les cas agrégés et non agrégés. Un seul `CComPolyObject` objet gère les deux cas. Cela signifie qu’une seule copie de la vtable et une copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, l’utilisation de `CComPolyObject` peut entraîner une taille de module légèrement supérieure, car elle n’est pas optimisée pour un objet agrégé ou non agrégé, comme c’est le cas `CComAggObject` et `CComObject` .

## <a name="see-also"></a>Voir aussi

[Notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Agrégation et macros de fabrique de classes](../atl/reference/aggregation-and-class-factory-macros.md)
