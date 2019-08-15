---
title: Notions de base des objets COM ATL
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: ec83539b2d7101c534bbc1df33577df422e76152
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492369"
---
# <a name="fundamentals-of-atl-com-objects"></a>Notions de base des objets COM ATL

L’illustration suivante représente la relation entre les classes et les interfaces utilisées pour définir un objet COM ATL.

![Structure ATL](../atl/media/vc307y1.gif "Structure ATL")

> [!NOTE]
>  Ce diagramme montre que `CComObject` est dérivé de `CYourClass` tandis `CComPolyObject` `CComAggObject` que `CYourClass` et inclut comme variable membre.

Il existe trois façons de définir un objet COM ATL. L’option standard consiste à utiliser la `CComObject` classe dérivée de. `CYourClass` La deuxième option consiste à créer un objet agrégé à l’aide de `CComAggObject` la classe. La troisième option consiste à utiliser la `CComPolyObject` classe. `CComPolyObject`agit comme un hybride: il peut fonctionner comme une `CComObject` classe ou comme une `CComAggObject` classe, selon la façon dont il est créé pour la première fois. Pour plus d’informations sur l’utilisation de `CComPolyObject` la classe, consultez la [classe CComPolyObject](../atl/reference/ccompolyobject-class.md).

Lorsque vous utilisez la bibliothèque COM ATL standard, vous utilisez deux objets: un objet externe et un objet interne. Les clients externes accèdent aux fonctionnalités de l’objet interne via les fonctions wrapper qui sont définies dans l’objet externe. L’objet externe est de type `CComObject`.

Lorsque vous utilisez un objet agrégé, l’objet externe ne fournit pas de wrappers pour les fonctionnalités de l’objet interne. Au lieu de cela, l’objet externe fournit un pointeur accessible directement par les clients externes. Dans ce scénario, l’objet externe est de type `CComAggObject`. L’objet interne est une variable membre de l’objet externe et est de type `CYourClass`.

Étant donné que le client n’a pas besoin de traverser l’objet externe pour interagir avec l’objet interne, les objets agrégés sont généralement plus efficaces. En outre, l’objet externe n’a pas besoin de connaître les fonctionnalités de l’objet agrégé, étant donné que l’interface de l’objet agrégé est directement disponible pour le client. Toutefois, tous les objets ne peuvent pas être agrégés. Pour qu’un objet soit agrégé, il doit être conçu avec l’agrégation à l’esprit.

ATL implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en deux phases:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)ou [CComPolyObject](../atl/reference/ccompolyobject-class.md) implémente les `IUnknown` méthodes.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) gère le décompte de références et les pointeurs externes de `IUnknown`.

D’autres aspects de votre objet ATL COM sont gérés par d’autres classes:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) définit la fabrique de classe et le modèle d’agrégation par défaut de l’objet.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) fournit une implémentation par défaut de `IDispatch Interface` la partie des interfaces doubles sur l’objet.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implémente l' `ISupportErrorInfo` interface qui garantit que les informations d’erreur peuvent être propagées correctement vers le haut de la chaîne d’appel.

## <a name="in-this-section"></a>Dans cette section

[Implémentation de CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Affiche des exemples d’entrées de mappage `CComObjectRootEx`com pour l’implémentation de.

[Implémentation de CComObject, CComAggObject et CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Explique comment les macros **_AGGREGATABLE DECLARE_\*** affectent l’utilisation de `CComObject`, `CComAggObject`et `CComPolyObject`.

[Prise en charge d’IDispatch et IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Répertorie les classes d’implémentation ATL à utiliser pour `IDispatch` la `IErrorInfo` prise en charge des interfaces et.

[Prise en charge d’IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
Décrit les étapes à suivre pour implémenter un point de connexion pour votre classe.

[Modification de la fabrique de classe et du modèle d’agrégation par défaut](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Affichez les macros à utiliser pour modifier la fabrique de classe et le modèle d’agrégation par défaut.

[Création d’un objet agrégé](../atl/creating-an-aggregated-object.md)<br/>
Répertorie les étapes de création d’un objet agrégé.

## <a name="related-sections"></a>Rubriques connexes

[Création d’un projet ATL](../atl/reference/creating-an-atl-project.md)<br/>
Fournit des informations sur la création d’un objet ATL COM.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)
