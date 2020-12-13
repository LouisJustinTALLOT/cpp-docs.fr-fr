---
description: 'En savoir plus sur : classe CComQIPtrElementTraits'
title: CComQIPtrElementTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 9aa96c5b926263d6ed58125a28f5d0a12d8107d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142335"
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtrElementTraits, classe

Cette classe fournit des méthodes, des fonctions statiques et des typedefs utiles lors de la création de collections de pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>Paramètres

*Cliqu*<br/>
Interface COM spécifiant le type de pointeur à stocker.

*piid*<br/>
Pointeur vers l’IID de *I*.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe dérive des méthodes et fournit un typedef utile lors de la création d’une classe de collection d’objets de pointeur d’interface com [CComQIPtr](../../atl/reference/ccomqiptr-class.md) . Cette classe est utilisée par les classes [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) et [CInterfaceList](../../atl/reference/cinterfacelist-class.md) .

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a> CComQIPtrElementTraits::INARGTYPE

Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
