---
title: Classe de CComAutoDeleteCriticalSection | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5153520b5a5648f8352465031264c223ffd97c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360062"
---
# <a name="ccomautodeletecriticalsection-class"></a>Classe de CComAutoDeleteCriticalSection
Cette classe fournit des méthodes pour obtenir et de libérer la possession d’un objet de section critique.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>Notes  
 `CComAutoDeleteCriticalSection` dérive de la classe [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Toutefois, `CComAutoDeleteCriticalSection` remplace le [terme](ccomsafedeletecriticalsection-class.md#term) méthode `private` accès, ce qui force le nettoyage de mémoire interne se produit uniquement lorsque les instances de cette classe sont hors de portée ou soient explicitement supprimés de la mémoire.  

  
 Cette classe n’introduit aucune des méthodes supplémentaires sur sa classe de base. Consultez [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) et [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pour plus d’informations sur les classes d’assistance de section critique.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcore.h  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [Classe de CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
