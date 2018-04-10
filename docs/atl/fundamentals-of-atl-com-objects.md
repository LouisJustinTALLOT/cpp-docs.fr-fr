---
title: Notions de base des objets ATL COM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a5a43af31a88420c154d7a57d27d2b69787d11d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="fundamentals-of-atl-com-objects"></a>Notions de base des objets ATL COM
L’illustration suivante représente la relation entre les classes et les interfaces qui sont utilisées pour définir un objet COM ATL.  
  
 ![Structure ATL](../atl/media/vc307y1.gif "vc307y1")  
  
> [!NOTE]
>  Ce diagramme montre que `CComObject` est dérivée de `CYourClass` tandis que `CComAggObject` et `CComPolyObject` incluent `CYourClass` qu’une variable membre.  
  
 Il existe trois façons de définir un objet COM ATL. L’option standard consiste à utiliser le `CComObject` classe qui est dérivée de `CYourClass`. La deuxième option consiste à créer un objet à l’aide de la `CComAggObject` classe. La troisième option consiste à utiliser la `CComPolyObject` classe. `CComPolyObject`agit comme un hybride : il peut fonctionner comme un `CComObject` classe ou comme un `CComAggObject` (classe), selon la façon dont il est créé en premier. Pour plus d’informations sur l’utilisation de la `CComPolyObject` de classe, consultez [CComPolyObject classe](../atl/reference/ccompolyobject-class.md).  
  
 Lorsque vous utilisez COM ATL standard, vous utilisez deux objets : un objet externe et un objet interne. Les clients externes accéder aux fonctionnalités de l’objet interne via les fonctions wrapper qui sont définies dans l’objet externe. L’objet externe est de type `CComObject`.  
  
 Lorsque vous utilisez un objet, l’objet externe ne fournit pas de wrappers pour les fonctionnalités de l’objet interne. Au lieu de cela, l’objet externe fournit un pointeur qui est directement accessible par les clients externes. Dans ce scénario, l’objet externe est de type `CComAggObject`. L’objet interne est une variable membre de l’objet externe, et il est de type `CYourClass`.  
  
 Étant donné que le client n’a pas à passer par l’objet externe pour interagir avec l’objet interne, les objets agrégées sont généralement plus efficaces. En outre, l’objet externe est inutile de connaître les fonctionnalités de l’objet agrégée, étant donné que l’interface de l’objet agrégé est directement accessible pour le client. Toutefois, tous les objets ne peuvent être agrégées. Pour un objet à agréger, il doit être conçu avec une agrégation à l’esprit.  
  
 ATL implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) en deux phases :  
  
-   [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), ou [CComPolyObject](../atl/reference/ccompolyobject-class.md) implémente la **IUnknown** méthodes.  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) gère le décompte de références et les pointeurs externes de **IUnknown**.  
  
 Les autres aspects de votre objet ATL COM sont gérés par d’autres classes :  
  
-   [CComCoClass](../atl/reference/ccomcoclass-class.md) définit classe modèle par défaut en usine et d’agrégation l’objet.  
  
-   [IDispatchImpl](../atl/reference/idispatchimpl-class.md) fournit une implémentation par défaut de la `IDispatch Interface` partie de toutes les interfaces doubles sur l’objet.  
  
-   [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implémente la **ISupportErrorInfo** interface qui garantit que les informations d’erreur permettre se propager correctement la chaîne d’appel.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation de CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)  
 Afficher les entrées de mappage COM pour l’implémentation exemple `CComObjectRootEx`.  
  
 [Implémentation de CComObject, CComAggObject et CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)  
 Explique comment la **macros DECLARE_\*_AGGREGATABLE** macros affectent l’utilisation de `CComObject`, `CComAggObject`, et `CComPolyObject`.  
  
 [Prise en charge d’IDispatch et IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)  
 Répertorie les classes d’implémentation ATL à utiliser pour prendre en charge la `IDispatch` et **IErrorInfo** interfaces.  
  
 [Prise en charge d’IDispEventImpl](../atl/supporting-idispeventimpl.md)  
 Décrit les étapes pour implémenter un point de connexion pour votre classe.  
  
 [Modification de la fabrique de classe et du modèle d’agrégation par défaut](../atl/changing-the-default-class-factory-and-aggregation-model.md)  
 Afficher les macros à utiliser pour modifier le modèle de fabrique et l’agrégation de la classe par défaut.  
  
 [Création d’un objet agrégé](../atl/creating-an-aggregated-object.md)  
 Répertorie les étapes de création d’un objet.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un projet ATL](../atl/reference/creating-an-atl-project.md)  
 Fournit des informations sur la création d’un objet COM ATL.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)

