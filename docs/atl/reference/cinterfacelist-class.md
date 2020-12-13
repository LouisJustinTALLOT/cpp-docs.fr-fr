---
description: 'En savoir plus sur : classe CInterfaceList'
title: CInterfaceList, classe
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 2612ba4700466bb877f84978c55bfd018f1dd286
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141529"
---
# <a name="cinterfacelist-class"></a>CInterfaceList, classe

Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Constructeur de la liste d’interfaces.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et des méthodes dérivées pour la création d’une liste de pointeurs d’interface COM. Utilisez [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) lorsqu’un tableau est requis.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a> CInterfaceList::CInterfaceList

Constructeur de la liste d’interfaces.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Taille de bloc, avec 10 comme valeur par défaut.

### <a name="remarks"></a>Notes

La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Les tailles de bloc plus volumineuses réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.

## <a name="see-also"></a>Voir aussi

[CAtlList, classe](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr, classe](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits, classe](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
