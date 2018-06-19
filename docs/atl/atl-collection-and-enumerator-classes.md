---
title: Classes des énumérateurs et des collections ATL | Documents Microsoft
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
ms.openlocfilehash: a47525bb21b896b0fef8393cab66142ed40311ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354444"
---
# <a name="atl-collection-and-enumerator-classes"></a>Classes des énumérateurs et des collections ATL
ATL fournit les classes suivantes pour vous aider à implémenter des collections et énumérateurs.  
  
|Classe|Description|  
|-----------|-----------------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implémentation d’interface de collection|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Implémentation d’interface énumérateur (suppose que les données stockées dans un conteneur compatible de bibliothèque C++ Standard)|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Implémentation d’interface énumérateur (Cela suppose que les données stockées dans un tableau)|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implémentation d’objet énumérateur (utilise `IEnumOnSTLImpl`)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|Implémentation d’objet énumérateur (utilise `CComEnumImpl`)|  
|[_Copy](../atl/atl-copy-policy-classes.md)|Classe de stratégie de copie|  
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Classe de stratégie de copie|  
|[CAdapt](../atl/reference/cadapt-class.md)|Classe d’adaptateur (masque **opérateur &** autorisant `CComPtr`, `CComQIPtr`, et `CComBSTR` à stocker dans les conteneurs de bibliothèque C++ Standard)|  
  
## <a name="see-also"></a>Voir aussi  
 [Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)

