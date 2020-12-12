---
description: 'En savoir plus sur : Collections ATL et classes Enumerator'
title: Collections ATL et classes Enumerator
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1f30aabb4908b0299a927f92a6d5ee4e9370a09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166042"
---
# <a name="atl-collection-and-enumerator-classes"></a>Collections ATL et classes Enumerator

ATL fournit les classes suivantes pour vous aider à implémenter des collections et des énumérateurs.

|Classe|Description|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implémentation de l’interface de collection|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Implémentation de l’interface d’énumérateur (suppose que les données sont stockées dans un conteneur compatible avec la bibliothèque standard C++)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Implémentation de l’interface d’énumérateur (suppose que les données sont stockées dans un tableau)|
|[CComEnumOnSTL ainsi que](../atl/reference/ccomenumonstl-class.md)|Implémentation de l’objet énumérateur (utilise `IEnumOnSTLImpl` )|
|[CComEnum](../atl/reference/ccomenum-class.md)|Implémentation de l’objet énumérateur (utilise `CComEnumImpl` )|
|[_Copy](../atl/atl-copy-policy-classes.md)|Copier la classe de stratégie|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Copier la classe de stratégie|
|[CAdapt](../atl/reference/cadapt-class.md)|Classe d’adaptateur (masque l' **opérateur &** permettant `CComPtr` `CComQIPtr` d’enregistrer, et de `CComBSTR` stocker dans des conteneurs de bibliothèque standard C++)|

## <a name="see-also"></a>Voir aussi

[Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)
