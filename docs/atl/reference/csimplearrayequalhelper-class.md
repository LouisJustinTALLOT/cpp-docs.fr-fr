---
title: Classe CSimpleArrayEqualHelper
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 386b005777b3e31dd74916a41bc5af2ab82df210
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330877"
---
# <a name="csimplearrayequalhelper-class"></a>Classe CSimpleArrayEqualHelper

Cette classe est une aide pour la classe [CSimpleArray.](../../atl/reference/csimplearray-class.md)

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Une classe dérivée.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statique) Teste `CSimpleArray` deux éléments d’objet pour l’égalité.|

## <a name="remarks"></a>Notes

Cette classe de traits `CSimpleArray` est un supplément à la classe. Il fournit une méthode pour comparer `CSimpleArray` deux éléments stockés dans un objet. Par défaut, les éléments sont comparés à l’aide **de l’opérateur,** mais si le tableau contient des types de données complexes qui n’ont pas leur propre opérateur d’égalité, vous devrez passer outre à cette classe.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpcoll.h

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual

Teste `CSimpleArray` deux éléments d’objet pour l’égalité.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Paramètres

*T1*<br/>
Objet de type T.

*t2*<br/>
Objet de type T.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si les éléments sont égaux, faux autrement.

## <a name="see-also"></a>Voir aussi

[Classe CSimpleArray](../../atl/reference/csimplearray-class.md)<br/>
[Classe CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
