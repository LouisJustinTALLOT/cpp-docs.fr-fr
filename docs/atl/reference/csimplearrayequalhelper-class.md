---
description: 'En savoir plus sur : classe CSimpleArrayEqualHelper'
title: CSimpleArrayEqualHelper, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: e1a5fd3eea5fd6ef7563febc662c5a7a1bc639c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140762"
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper, classe

Cette classe est une application d’assistance pour la classe [CSimpleArray](../../atl/reference/csimplearray-class.md) .

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleArrayEqualHelper :: IsEqual](#isequal)|Statique Teste l' `CSimpleArray` égalité de deux éléments objet.|

## <a name="remarks"></a>Notes

Cette classe de traits est un supplément de la `CSimpleArray` classe. Il fournit une méthode pour comparer deux éléments stockés dans un `CSimpleArray` objet. Par défaut, les éléments sont comparés à l’aide de **Operator = ()**, mais si le tableau contient des types de données complexes qui n’ont pas leur propre opérateur d’égalité, vous devez substituer cette classe.

## <a name="requirements"></a>Spécifications

**En-tête :** atlsimpcoll. h

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a> CSimpleArrayEqualHelper :: IsEqual

Teste l' `CSimpleArray` égalité de deux éléments objet.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Paramètres

*T1*<br/>
Objet de type T.

*H2*<br/>
Objet de type T.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si les éléments sont égaux, sinon false.

## <a name="see-also"></a>Voir aussi

[CSimpleArray, classe](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse, classe](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
