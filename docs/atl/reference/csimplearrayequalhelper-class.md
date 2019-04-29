---
title: Csimplearrayequalhelper, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 8b7e32ddab5b2f0667b17b0f127ac2e7e5d9a426
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277992"
---
# <a name="csimplearrayequalhelper-class"></a>Csimplearrayequalhelper, classe

Cette classe est une application d’assistance pour la [CSimpleArray](../../atl/reference/csimplearray-class.md) classe.

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
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statique) Teste si deux `CSimpleArray` éléments pour l’égalité de l’objet.|

## <a name="remarks"></a>Notes

Cette classe de traits constitue un supplément pour le `CSimpleArray` classe. Il fournit une méthode de comparaison de deux éléments stockés dans un `CSimpleArray` objet. Par défaut, les éléments sont comparés à l’aide de **operator=()**, mais si le tableau contient les types de données complexes qui ne disposent pas de leur propre opérateur d’égalité, vous devez substituer cette classe.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual

Teste si deux `CSimpleArray` éléments pour l’égalité de l’objet.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Paramètres

*t1*<br/>
Un objet de type T.

*t2*<br/>
Un objet de type T.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les éléments sont égaux, sinon false.

## <a name="see-also"></a>Voir aussi

[CSimpleArray, classe](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse, classe](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
