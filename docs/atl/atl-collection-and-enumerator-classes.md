---
title: Collections ATL et Classes d’énumérateurs
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1ab9a160b01ea278d162a515e5121054bf398f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252323"
---
# <a name="atl-collection-and-enumerator-classes"></a>Collections ATL et Classes d’énumérateurs

ATL fournit les classes suivantes pour vous aider à implémenter des collections et énumérateurs.

|Classe|Description|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implémentation d’interface de collection|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Implémentation d’interface énumérateur (suppose que les données stockées dans un conteneur compatible avec bibliothèque C++ Standard)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Implémentation d’interface énumérateur (suppose que les données stockées dans un tableau)|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implémentation d’objet énumérateur (utilise `IEnumOnSTLImpl`)|
|[CComEnum](../atl/reference/ccomenum-class.md)|Implémentation d’objet énumérateur (utilise `CComEnumImpl`)|
|[_Copy](../atl/atl-copy-policy-classes.md)|Classe de stratégie de copie|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Classe de stratégie de copie|
|[CAdapt](../atl/reference/cadapt-class.md)|Classe d’adaptateur (masque **opérateur &** autorisant `CComPtr`, `CComQIPtr`, et `CComBSTR` pour être stockés dans des conteneurs de bibliothèque C++ Standard)|

## <a name="see-also"></a>Voir aussi

[Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)
