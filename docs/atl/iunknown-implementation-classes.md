---
title: Classes d’implémentation IUnknown (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
dev_langs:
- C++
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4cd2f2473249271285d6b8812dac1b924e5a172
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848533"
---
# <a name="iunknown-implementation-classes"></a>Classes d’implémentation IUnknown
Les classes suivantes implémentent `IUnknown` et les méthodes associées :  
  
-   [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) gère le décompte de références pour les objets regroupés et agrégées. Vous permet de spécifier un modèle de thread.  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) gère le décompte de références pour les objets regroupés et agrégées. Utilise la valeur par défaut, le modèle du serveur de thread.  
  
-   [CComAggObject](../atl/reference/ccomaggobject-class.md) implémente `IUnknown` pour un objet agrégé.  
  
-   [CComObject](../atl/reference/ccomobject-class.md) implémente `IUnknown` pour un objet non regroupées en agrégats.  
  
-   [CComPolyObject](../atl/reference/ccompolyobject-class.md) implémente `IUnknown` pour les objets regroupés et. À l’aide de `CComPolyObject` évite d’avoir à la fois `CComAggObject` et `CComObject` dans votre module. Un seul `CComPolyObject` objet gère les cas regroupés et.  
  
-   [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) implémente `IUnknown` pour un objet non regroupées en agrégats, sans modifier le nombre de verrous du module.  
  
-   [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) implémente `IUnknown` pour une interface détachable.  
  
-   [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) implémente `IUnknown` pour une interface détachable « mise en cache ».  
  
-   [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) implémente `IUnknown` pour l’objet interne d’une agrégation ou une interface détachable.  
  
-   [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) gère un décompte de références sur le module pour vous assurer de votre objet ne sera pas supprimé.  
  
-   [CComObjectStack](../atl/reference/ccomobjectstack-class.md) crée un objet COM temporaire, à l’aide d’une implémentation squelette de `IUnknown`.  
  
## <a name="related-articles"></a>Articles connexes  
 [Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../atl/atl-class-overview.md)   
 [Agrégation et Macros de fabrique de classe](../atl/reference/aggregation-and-class-factory-macros.md)   
 [Macros de mappage COM](../atl/reference/com-map-macros.md)   
 [Fonctions globales de mappage COM](../atl/reference/com-map-global-functions.md)

