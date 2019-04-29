---
title: Csimplearrayequalhelperfalse, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 35207fdcbffc0e0367d86682b5f731eef617d761
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277953"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Csimplearrayequalhelperfalse, classe

Cette classe est une application d’assistance pour la [CSimpleArray](../../atl/reference/csimplearray-class.md) classe.

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
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statique) Retourne la valeur false.|

## <a name="remarks"></a>Notes

Cette classe de traits est un complément de la `CSimpleArray` classe. Informatique toujours retourne false et, en outre, appellera `ATLASSERT` avec un argument False s’il est déjà référencé. Dans les situations où le test d’égalité n’est pas suffisamment défini, cette classe permet à un tableau contenant les éléments pour fonctionner correctement pour la plupart des méthodes, mais échouer de manière bien définie pour les méthodes qui dépendent des comparaisons telles que [CSimpleArray :: Rechercher](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual

Retourne false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Valeur de retour

Retourne false.

### <a name="remarks"></a>Notes

Cette méthode retourne toujours false et appellera `ATLASSERT` avec un argument False si référencé. L’objectif de `CSimpleArrayEqualHelperFalse::IsEqual` consiste à forcer les méthodes à l’aide de comparaisons à échouer de manière bien définie lors de tests d’égalité n’ont pas été correctement définies.

## <a name="see-also"></a>Voir aussi

[CSimpleArrayEqualHelper, classe](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
