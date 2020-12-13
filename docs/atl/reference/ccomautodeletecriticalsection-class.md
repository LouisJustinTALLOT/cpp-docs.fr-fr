---
description: 'En savoir plus sur : classe CComAutoDeleteCriticalSection'
title: CComAutoDeleteCriticalSection, classe
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: 3c65108917b28b9e4e17210afc54eab6814302b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152332"
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection, classe

Cette classe fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>Notes

`CComAutoDeleteCriticalSection` dérive de la classe [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Toutefois, `CComAutoDeleteCriticalSection` substitue la méthode [term](ccomsafedeletecriticalsection-class.md#term) à **`private`** Access, ce qui force le nettoyage de la mémoire interne uniquement lorsque les instances de cette classe sont hors de portée ou sont supprimées de la mémoire de manière explicite.

Cette classe n’introduit aucune méthode supplémentaire sur sa classe de base. Pour plus d’informations sur les classes d’assistance de section critique, consultez [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) et [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="see-also"></a>Voir aussi

[CComSafeDeleteCriticalSection, classe](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
