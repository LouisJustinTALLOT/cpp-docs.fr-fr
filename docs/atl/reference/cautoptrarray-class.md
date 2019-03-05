---
title: Cautoptrarray, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: beb0184a9945990b8d92efe03d4f54baa76ca380
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298904"
---
# <a name="cautoptrarray-class"></a>Cautoptrarray, classe

Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs intelligents.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Paramètres

*E*<br/>
Le type de pointeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Constructeur.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et est dérivée des méthodes à partir de [CAtlArray](../../atl/reference/catlarray-class.md) et [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) afin de faciliter la création d’un objet de classe de collection stocker les pointeurs intelligents.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll.h

##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray

Constructeur.

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Notes

Initialise le tableau de pointeurs intelligents.

## <a name="see-also"></a>Voir aussi

[CAtlArray, classe](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits, classe](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList, classe](../../atl/reference/cautoptrlist-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
