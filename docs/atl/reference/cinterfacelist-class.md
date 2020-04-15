---
title: Classe CInterfaceList
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 0a7fd781c63e4ea084cf078e49fc9efb9cfa2d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326789"
---
# <a name="cinterfacelist-class"></a>Classe CInterfaceList

Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Le constructeur de la liste d’interfaces.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et des méthodes dérivées pour créer une liste de pointeurs d’interface COM. Utilisez [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) lorsqu’un tableau est nécessaire.

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a>CInterfaceList::CInterfaceList

Le constructeur de la liste d’interfaces.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
La taille du bloc, avec un défaut de 10.

### <a name="remarks"></a>Notes

La taille du bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est nécessaire. De plus grandes tailles de blocs réduisent les appels aux routines d’allocation de mémoire, mais utilisent plus de ressources.

## <a name="see-also"></a>Voir aussi

[Classe CAtlList](../../atl/reference/catllist-class.md)<br/>
[Classe CComQIPtr](../../atl/reference/ccomqiptr-class.md)<br/>
[Classe CComQIPtrElraits](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
