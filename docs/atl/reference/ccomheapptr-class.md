---
title: CComHeapPtr, classe
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: eaa21700f63ae07565dba4b8b3b5dabac69e0168
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553732"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr, classe

Une classe de pointeur intelligent pour la gestion des pointeurs de tas.

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

`CComHeapPtr` dérive de `CHeapPtr`, mais utilise [CComAllocator](../../atl/reference/ccomallocator-class.md) d’allocation de mémoire à l’aide des routines de COM. Consultez [CHeapPtr](../../atl/reference/cheapptr-class.md) et [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) pour les méthodes disponibles.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="ccomheapptr"></a>  CComHeapPtr::CComHeapPtr

Constructeur.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Paramètres

*pData*<br/>
Objet `CComHeapPtr` existant.

### <a name="remarks"></a>Notes

Le pointeur de segment de mémoire peut éventuellement être créé à l’aide d’un existant `CComHeapPtr` objet. Dans ce cas, la nouvelle `CComHeapPtr` objet assume la responsabilité de gérer le nouveau pointeur et les ressources.

## <a name="see-also"></a>Voir aussi

[CHeapPtr, classe](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase, classe](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator, classe](../../atl/reference/ccomallocator-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
