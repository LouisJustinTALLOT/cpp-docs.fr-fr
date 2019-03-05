---
title: Cinterfacearray, classe
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: 2e8714bf40e99a1014d7cd6de82cddb13cbbb9cf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282823"
---
# <a name="cinterfacearray-class"></a>Cinterfacearray, classe

Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Paramètres

*I*<br/>
Une interface COM qui spécifie le type de pointeur à stocker.

*piid*<br/>
Un pointeur vers l’IID de *je*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Le constructeur pour le tableau d’interfaces.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et les méthodes dérivées pour la création d’un tableau de pointeurs d’interface COM. Utilisez [CInterfaceList](../../atl/reference/cinterfacelist-class.md) quand une liste est requise.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll.h

##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray

Constructeur.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Notes

Initialise le tableau de pointeurs intelligents.

## <a name="see-also"></a>Voir aussi

[CAtlArray, classe](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr, classe](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits, classe](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
