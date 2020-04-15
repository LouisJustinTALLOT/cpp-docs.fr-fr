---
title: Classe CInterfaceArray
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: e6efe31989b06f0977ecff156a8f64053dc64ad1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326797"
---
# <a name="cinterfacearray-class"></a>Classe CInterfaceArray

Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Paramètres

*Ⅰ*<br/>
Une interface COM spécifiant le type de pointeur à stocker.

*piid*<br/>
Un pointeur à l’IID de *I*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Le constructeur pour le tableau d’interface.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et des méthodes dérivées pour créer un tableau de pointeurs d’interface COM. Utilisez [CInterfaceList](../../atl/reference/cinterfacelist-class.md) lorsqu’une liste est requise.

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="cinterfacearraycinterfacearray"></a><a name="cinterfacearray"></a>CInterfaceArray::CInterfaceArray

Constructeur.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Notes

Initialise le tableau de pointeurs intelligents.

## <a name="see-also"></a>Voir aussi

[Classe CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[Classe CComQIPtr](../../atl/reference/ccomqiptr-class.md)<br/>
[Classe CComQIPtrElraits](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
