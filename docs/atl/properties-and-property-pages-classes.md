---
title: Propriétés et des Classes de Pages de propriétés (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
ms.openlocfilehash: 05c3a67e278389bb2ab1b07e9d6cf63cbe347c63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249624"
---
# <a name="properties-and-property-pages-classes"></a>Propriétés et des Classes de Pages de propriétés

Les classes suivantes prennent en charge les propriétés et les pages de propriétés :

- [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver) récupère ou définit les propriétés d’un objet via un `IDispatch` pointeur.

- [CStockPropImpl](../atl/reference/cstockpropimpl-class.md) implémente les propriétés stock prises en charge par ATL.

- [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md) accède aux informations dans les pages de propriétés d’un objet.

- [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md) stocke les propriétés d’un objet dans un conteneur de propriétés fourni par le client.

- [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md) gère une page de propriété particulière dans une feuille de propriétés.

- [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md) similaire à `IPropertyPageImpl`, mais permet également à un client sélectionner une propriété spécifique dans une page de propriétés.

- [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md) Obtient les CLSID pour les pages de propriétés pris en charge par un objet.

## <a name="related-articles"></a>Articles connexes

[Didacticiel ATL](../atl/active-template-library-atl-tutorial.md)

[Pages de propriétés ATL COM](../atl/atl-com-property-pages.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)<br/>
[Macros de mappage de propriétés](../atl/reference/property-map-macros.md)
