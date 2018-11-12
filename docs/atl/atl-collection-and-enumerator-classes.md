---
title: Collections ATL et Classes d’énumérateurs
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: a0d7483cc142377ec4de903e27f23056a9e8dd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495302"
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
|[_Copier](../atl/atl-copy-policy-classes.md)|Classe de stratégie de copie|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Classe de stratégie de copie|
|[CAdapt](../atl/reference/cadapt-class.md)|Classe d’adaptateur (masque **opérateur &** autorisant `CComPtr`, `CComQIPtr`, et `CComBSTR` pour être stockés dans des conteneurs de bibliothèque C++ Standard)|

## <a name="see-also"></a>Voir aussi

[Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)

