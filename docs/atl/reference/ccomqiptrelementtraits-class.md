---
title: Classe CComQIPtrElraits
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 19f2669c157310be02f746672b22f6c0ed005075
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327408"
---
# <a name="ccomqiptrelementtraits-class"></a>Classe CComQIPtrElraits

Cette classe fournit des méthodes, des fonctions statiques et des types utiles lors de la création de collections de pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>Paramètres

*Ⅰ*<br/>
Une interface COM spécifiant le type de pointeur à stocker.

*piid*<br/>
Un pointeur à l’IID de *I*.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour ajouter des éléments à l’objet de classe de collecte.|

## <a name="remarks"></a>Notes

Cette classe dérive des méthodes et fournit un tapdef utile lors de la création d’une classe de collection d’objets pointeurs d’interface [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM. Cette classe est utilisée par les classes [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) et [CInterfaceList.](../../atl/reference/cinterfacelist-class.md)

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a>CComQIPtrElementTraits::INARGTYPE

Le type de données à utiliser pour ajouter des éléments à l’objet de classe de collecte.

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[Classe CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
