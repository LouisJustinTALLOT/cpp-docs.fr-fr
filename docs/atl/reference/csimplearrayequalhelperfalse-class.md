---
description: 'En savoir plus sur : classe CSimpleArrayEqualHelperFalse'
title: CSimpleArrayEqualHelperFalse, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 196f7873f72799408a629bc784cb343966801d79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140723"
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse, classe

Cette classe est une application d’assistance pour la classe [CSimpleArray](../../atl/reference/csimplearray-class.md) .

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse :: IsEqual](#isequal)|Statique Retourne false.|

## <a name="remarks"></a>Notes

Cette classe de traits est un complément de la `CSimpleArray` classe. Elle retourne toujours la valeur false et, en outre, appelle `ATLASSERT` avec un argument false si elle est référencée. Dans les situations où le test d’égalité n’est pas suffisamment défini, cette classe permet à un tableau contenant des éléments de fonctionner correctement pour la plupart des méthodes, mais qui échouent de manière bien définie pour les méthodes qui dépendent de comparaisons telles que [CSimpleArray :: find](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Spécifications

**En-tête :** atlsimpcoll. h

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a> CSimpleArrayEqualHelperFalse :: IsEqual

Retourne false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne false.

### <a name="remarks"></a>Notes

Cette méthode retourne toujours la valeur false et appelle `ATLASSERT` avec l’argument false s’il est référencé. L’objectif de `CSimpleArrayEqualHelperFalse::IsEqual` est de forcer les méthodes utilisant des comparaisons à échouer de manière bien définie lorsque les tests d’égalité n’ont pas été correctement définis.

## <a name="see-also"></a>Voir aussi

[CSimpleArrayEqualHelper, classe](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
