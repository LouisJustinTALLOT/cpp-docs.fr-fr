---
description: 'En savoir plus sur : classe CAutoPtrArray'
title: CAutoPtrArray, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 55f9382c82a1e242342d0d740c369a571c43f9ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152577"
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray, classe

Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs intelligents.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

### <a name="parameters"></a>Paramètres

*E*<br/>
Type de pointeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Constructeur.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et dérive les méthodes de [CAtlArray](../../atl/reference/catlarray-class.md) et [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) pour faciliter la création d’un objet de classe de collection qui stocke des pointeurs intelligents.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a> CAutoPtrArray::CAutoPtrArray

Constructeur.

```cpp
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Notes

Initialise le tableau de pointeurs intelligents.

## <a name="see-also"></a>Voir aussi

[Classe CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits, classe](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList, classe](../../atl/reference/cautoptrlist-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
