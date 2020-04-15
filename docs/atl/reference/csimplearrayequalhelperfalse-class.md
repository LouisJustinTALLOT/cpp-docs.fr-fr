---
title: Classe CSimpleArrayEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 5eca3145d64895e34b599fbf83834af142b65973
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330890"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Classe CSimpleArrayEqualHelperFalse

Cette classe est une aide pour la classe [CSimpleArray.](../../atl/reference/csimplearray-class.md)

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Une classe dérivée.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statique) Retourne faux.|

## <a name="remarks"></a>Notes

Cette classe de traits `CSimpleArray` est un complément à la classe. Il retourne toujours faux, et `ATLASSERT` en outre, appellera avec un argument de faux si jamais il est référencé. Dans les situations où le test d’égalité n’est pas suffisamment défini, cette classe permet à un tableau contenant des éléments de fonctionner correctement pour la plupart des méthodes, mais échoue d’une manière bien définie pour les méthodes qui dépendent de comparaisons telles que [CSimpleArray::Trouver](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpcoll.h

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual

Retourne false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Valeur de retour

Retourne false.

### <a name="remarks"></a>Notes

Cette méthode revient toujours `ATLASSERT` faux, et appellera avec un argument de faux s’il est référencé. Le but `CSimpleArrayEqualHelperFalse::IsEqual` est de forcer les méthodes utilisant des comparaisons à échouer d’une manière bien définie lorsque les tests d’égalité n’ont pas été correctement définis.

## <a name="see-also"></a>Voir aussi

[Classe CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
