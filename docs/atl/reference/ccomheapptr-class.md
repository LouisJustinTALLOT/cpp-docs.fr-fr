---
description: 'En savoir plus sur : classe CComHeapPtr'
title: CComHeapPtr, classe
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: 18865923e86a2392260ab1e6dedde2f37b9b4ea3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146625"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr, classe

Classe de pointeur intelligent pour la gestion des pointeurs de tas.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type d’objet à stocker sur le tas.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Constructeur.|

## <a name="remarks"></a>Notes

`CComHeapPtr` dérive de `CHeapPtr` , mais utilise [CComAllocator](../../atl/reference/ccomallocator-class.md) pour allouer de la mémoire à l’aide de routines com. Consultez [CHeapPtr](../../atl/reference/cheapptr-class.md) et [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) pour connaître les méthodes disponibles.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a> CComHeapPtr::CComHeapPtr

Constructeur.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Paramètres

*pData*<br/>
Objet `CComHeapPtr` existant.

### <a name="remarks"></a>Notes

Le pointeur de tas peut éventuellement être créé à l’aide d’un `CComHeapPtr` objet existant. Dans ce cas, le nouvel `CComHeapPtr` objet assume la responsabilité de la gestion du nouveau pointeur et des ressources.

## <a name="see-also"></a>Voir aussi

[CHeapPtr, classe](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase, classe](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator, classe](../../atl/reference/ccomallocator-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
