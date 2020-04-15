---
title: Classe CComHeapPtr
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: 78cadfff9a278cf080393ab919f3891b201c91aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327774"
---
# <a name="ccomheapptr-class"></a>Classe CComHeapPtr

Une classe de pointeur intelligent pour gérer les pointeurs de tas.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type d’objet à stocker sur le tas.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Constructeur.|

## <a name="remarks"></a>Notes

`CComHeapPtr`dérive de `CHeapPtr`, mais utilise [CComAllocator](../../atl/reference/ccomallocator-class.md) pour allouer la mémoire en utilisant des routines COM. Voir [CHeapPtr](../../atl/reference/cheapptr-class.md) et [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) pour les méthodes disponibles.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHeapPtrBase (en)](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr

Constructeur.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Paramètres

*Pdata*<br/>
Objet `CComHeapPtr` existant.

### <a name="remarks"></a>Notes

Le pointeur de tas peut être `CComHeapPtr` créé en option à l’aide d’un objet existant. Si c’est `CComHeapPtr` le cas, le nouvel objet assume la responsabilité de la gestion du nouveau pointeur et des ressources.

## <a name="see-also"></a>Voir aussi

[Classe CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Classe CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Classe CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
