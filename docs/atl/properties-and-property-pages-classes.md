---
title: Classes (ATL) des Pages de propriétés et propriété | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.properties
dev_langs:
- C++
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29400fc2e47b419587b81164aa5a7720a7ef134b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065710"
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

