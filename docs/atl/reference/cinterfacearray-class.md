---
description: 'En savoir plus sur : classe CInterfaceArray'
title: CInterfaceArray, classe
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: 6dbe382682b8411d7562d1d0ff75f0ef587396f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141542"
---
# <a name="cinterfacearray-class"></a>CInterfaceArray, classe

Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Paramètres

*Cliqu*<br/>
Interface COM spécifiant le type de pointeur à stocker.

*piid*<br/>
Pointeur vers l’IID de *I*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Constructeur pour le tableau d’interface.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et des méthodes dérivées pour la création d’un tableau de pointeurs d’interface COM. Utilisez [CInterfaceList](../../atl/reference/cinterfacelist-class.md) quand une liste est requise.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cinterfacearraycinterfacearray"></a><a name="cinterfacearray"></a> CInterfaceArray::CInterfaceArray

Constructeur.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Notes

Initialise le tableau de pointeurs intelligents.

## <a name="see-also"></a>Voir aussi

[Classe CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr, classe](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits, classe](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
