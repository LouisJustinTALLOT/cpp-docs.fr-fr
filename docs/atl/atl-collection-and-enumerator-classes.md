---
title: Collections ATL et Classes d’énumérateurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0ff5fec4749e08826bab5572149c6cd24a204f9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765071"
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

