---
title: Ccomautodeletecriticalsection, classe | Microsoft Docs
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
ms.openlocfilehash: 53078d740d1051a928b4592d275f33944685e622
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767102"
---
# <a name="ccomautodeletecriticalsection-class"></a>Ccomautodeletecriticalsection, classe

Cette classe fournit des méthodes pour obtenir et de libérer de la propriété d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>Notes

`CComAutoDeleteCriticalSection` dérive de la classe [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Toutefois, `CComAutoDeleteCriticalSection` remplace le [terme](ccomsafedeletecriticalsection-class.md#term) méthode **privé** accès, ce qui force le nettoyage de mémoire interne s’exécute uniquement lorsque les instances de cette classe sont hors de portée ou soient explicitement supprimés à partir de mémoire.  

Cette classe présente des méthodes supplémentaires au fil de sa classe de base. Consultez [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) et [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pour plus d’informations sur les classes d’assistance de section critique.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcore.h

## <a name="see-also"></a>Voir aussi

[Ccomsafedeletecriticalsection, classe](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
