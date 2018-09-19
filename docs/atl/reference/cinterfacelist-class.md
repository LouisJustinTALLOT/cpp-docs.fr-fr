---
title: Cinterfacelist, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac378e0a923e2a906bf99995432bfc87e39b8d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032430"
---
# <a name="cinterfacelist-class"></a>Cinterfacelist, classe

Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Le constructeur de la liste d’interfaces.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et les méthodes dérivées pour la création d’une liste de pointeurs d’interface COM. Utilisez [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) lorsqu’un tableau est requis.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList

Le constructeur de la liste d’interfaces.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
La taille de bloc, avec une valeur par défaut de 10.

### <a name="remarks"></a>Notes

La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.

## <a name="see-also"></a>Voir aussi

[CAtlList, classe](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr, classe](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits, classe](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
