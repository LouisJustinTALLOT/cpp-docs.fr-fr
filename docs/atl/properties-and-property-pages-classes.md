---
description: En savoir plus sur les classes propriétés et pages de propriétés
title: Classes des propriétés et des pages de propriétés (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
ms.openlocfilehash: 1fddb9626afcab908ae6f7ffb085c263b7a84af7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159191"
---
# <a name="properties-and-property-pages-classes"></a>Classes des propriétés et des pages de propriétés

Les classes suivantes prennent en charge les propriétés et les pages de propriétés :

- [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver) Récupère ou définit les propriétés d’un objet par le biais d’un `IDispatch` pointeur.

- [CStockPropImpl](../atl/reference/cstockpropimpl-class.md) Implémente les propriétés stock prises en charge par ATL.

- [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md) Accède aux informations contenues dans les pages de propriétés d’un objet.

- [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md) Stocke les propriétés d’un objet dans un conteneur de propriétés fourni par le client.

- [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md) Gère une page de propriétés particulière dans une feuille de propriétés.

- [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md) Semblable à `IPropertyPageImpl` , mais permet également à un client de sélectionner une propriété spécifique dans une page de propriétés.

- [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md) Obtient les CLSID pour les pages de propriétés prises en charge par un objet.

## <a name="related-articles"></a>Articles connexes

[Tutoriel ATL](../atl/active-template-library-atl-tutorial.md)

[Pages de propriétés ATL COM](../atl/atl-com-property-pages.md)

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../atl/atl-class-overview.md)<br/>
[Macros de mappage de propriétés](../atl/reference/property-map-macros.md)
