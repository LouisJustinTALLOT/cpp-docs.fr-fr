---
title: Cautoptrarray, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23cc8e519fc47173efe413cc687ef48c0dc39945
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025163"
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

## <a name="requirements"></a>Configuration requise

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
