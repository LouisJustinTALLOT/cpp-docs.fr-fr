---
title: Principes fondamentaux des objets ATL COM
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 651413534ed44143e2a0fdaf00bdabd6e5d57010
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319554"
---
# <a name="fundamentals-of-atl-com-objects"></a>Principes fondamentaux des objets ATL COM

L’illustration suivante illustre la relation entre les classes et les interfaces qui sont utilisées pour définir un objet ATL COM.

![Structure ATL](../atl/media/vc307y1.gif "Structure ATL")

> [!NOTE]
> Ce diagramme `CComObject` montre qui `CYourClass` `CComAggObject` est `CComPolyObject` `CYourClass` dérivé de considérant et inclut en tant que variable de membre.

Il existe trois façons de définir un objet ATL COM. L’option standard est `CComObject` d’utiliser `CYourClass`la classe qui est dérivée de . La deuxième option consiste à créer un `CComAggObject` objet agrégé en utilisant la classe. La troisième option est `CComPolyObject` d’utiliser la classe. `CComPolyObject`agit comme un hybride: il `CComObject` peut fonctionner `CComAggObject` comme une classe ou comme une classe, en fonction de la façon dont il est créé pour la première fois. Pour plus d’informations `CComPolyObject` sur la façon d’utiliser la classe, voir [CComPolyObject Class](../atl/reference/ccompolyobject-class.md).

Lorsque vous utilisez ATL COM standard, vous utilisez deux objets : un objet extérieur et un objet intérieur. Les clients externes accèdent à la fonctionnalité de l’objet intérieur grâce aux fonctions d’emballage définies dans l’objet extérieur. L’objet extérieur `CComObject`est de type .

Lorsque vous utilisez un objet agrégé, l’objet extérieur ne fournit pas d’emballages pour la fonctionnalité de l’objet intérieur. Au lieu de cela, l’objet extérieur fournit un pointeur qui est directement accessible par les clients externes. Dans ce scénario, l’objet `CComAggObject`extérieur est de type . L’objet intérieur est une variable de membre de `CYourClass`l’objet extérieur, et il est de type .

Parce que le client n’a pas à passer par l’objet extérieur pour interagir avec l’objet intérieur, les objets agrégés sont généralement plus efficaces. En outre, l’objet extérieur n’a pas à connaître la fonctionnalité de l’objet agrégé, étant donné que l’interface de l’objet agrégé est directement disponible pour le client. Cependant, tous les objets ne peuvent pas être agrégés. Pour qu’un objet soit agrégé, il doit être conçu avec l’agrégation à l’esprit.

ATL implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en deux phases :

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), ou [CComPolyObject](../atl/reference/ccompolyobject-class.md) implémente les `IUnknown` méthodes.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) gère le nombre `IUnknown`de références et les pointeurs extérieurs de .

D’autres aspects de votre objet ATL COM sont gérés par d’autres classes :

- [CComCoClass](../atl/reference/ccomcoclass-class.md) définit l’usine de classe par défaut et le modèle d’agrégation de l’objet.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) fournit une implémentation par défaut de la `IDispatch Interface` partie de toutes les interfaces doubles sur l’objet.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implémente l’interface qui garantit que les `ISupportErrorInfo` informations d’erreur peuvent être propagées correctement la chaîne d’appels.

## <a name="in-this-section"></a>Dans cette section

[Implémentation de CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Afficher l’exemple des `CComObjectRootEx`entrées de carte COM pour la mise en œuvre .

[Implémentation de CComObject, CComAggObject et CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Discute comment le **DECLARE_\*_AGGREGATABLE** macros affectent l’utilisation `CComAggObject`de `CComPolyObject` `CComObject`, , , et .

[Prise en charge d’IDispatch et d’IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Répertorie les classes de `IDispatch` mise `IErrorInfo` en œuvre ATL à utiliser pour prendre en charge les interfaces et les interfaces.

[Prise en charge d’IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
Discute des étapes pour implémenter un point de connexion pour votre classe.

[Modification du modèle d’usine et d’agrégation de classe par défaut](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Montrez quelles macros utiliser pour modifier l’usine et le modèle d’agrégation de la classe par défaut.

[Création d’un objet agrégé](../atl/creating-an-aggregated-object.md)<br/>
Répertorie les étapes pour créer un objet agrégé.

## <a name="related-sections"></a>Sections connexes

[Création d’un projet ATL](../atl/reference/creating-an-atl-project.md)<br/>
Fournit des informations sur la création d’un objet ATL COM.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

## <a name="see-also"></a>Voir aussi

[Concepts liés à la](../atl/active-template-library-atl-concepts.md)
