---
title: Ccomautodeletecriticalsection, classe
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: d479adce489e0329be3a93b55a70aa3e58a0e038
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265130"
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

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore.h

## <a name="see-also"></a>Voir aussi

[CComSafeDeleteCriticalSection, classe](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
