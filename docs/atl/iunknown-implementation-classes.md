---
description: 'En savoir plus sur : classes d’implémentation IUnknown'
title: Classes d’implémentation IUnknown (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
ms.openlocfilehash: a28bd14be86501fd6566b8038b73a51efcc1c18d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147652"
---
# <a name="iunknown-implementation-classes"></a>Classes d’implémentation IUnknown

Les classes suivantes implémentent les `IUnknown` méthodes et associées :

- [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) Gère le comptage des références pour les objets agrégés et non agrégés. Vous permet de spécifier un modèle de thread.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) Gère le comptage des références pour les objets agrégés et non agrégés. Utilise le modèle de thread par défaut du serveur.

- [CComAggObject](../atl/reference/ccomaggobject-class.md) Implémente `IUnknown` pour un objet agrégé.

- [CComObject](../atl/reference/ccomobject-class.md) Implémente `IUnknown` pour un objet non agrégé.

- [CComPolyObject](../atl/reference/ccompolyobject-class.md) Implémente `IUnknown` pour les objets agrégés et non agrégés. L’utilisation `CComPolyObject` de évite d’avoir à `CComAggObject` la fois et `CComObject` dans votre module. Un objet unique gère à la `CComPolyObject` fois les cas agrégés et les cas imagrégés.

- [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) Implémente `IUnknown` pour un objet non agrégé, sans modifier le nombre de verrous de module.

- [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) Implémente `IUnknown` pour une interface détachée.

- [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) Implémente `IUnknown` pour une interface détachée « mise en cache ».

- [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) Implémente `IUnknown` pour l’objet interne d’une agrégation ou d’une interface détachée.

- [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) Gère un décompte de références sur le module pour garantir que votre objet ne sera pas supprimé.

- [CComObjectStack](../atl/reference/ccomobjectstack-class.md) Crée un objet COM temporaire, à l’aide d’une implémentation squelettique de `IUnknown` .

## <a name="related-articles"></a>Articles connexes

[Notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md)

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../atl/atl-class-overview.md)<br/>
[Agrégation et macros de fabrique de classes](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[Macros de mappage COM](../atl/reference/com-map-macros.md)<br/>
[Fonctions globales de mappage COM](../atl/reference/com-map-global-functions.md)
