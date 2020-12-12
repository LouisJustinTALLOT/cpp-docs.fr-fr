---
description: 'En savoir plus sur : classe CSimpleMapEqualHelperFalse'
title: CSimpleMapEqualHelperFalse, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: 5bad8232dc1a96fc743a3526acdb86b839601d9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140580"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse, classe

Cette classe est une application d’assistance pour la classe [CSimpleMap](../../atl/reference/csimplemap-class.md) .

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|Statique Teste l’égalité de deux clés.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|Statique Retourne false.|

## <a name="remarks"></a>Notes

Cette classe de traits est un supplément de la `CSimpleMap` classe. Il fournit une méthode pour comparer deux éléments contenus dans l' `CSimpleMap` objet, en particulier deux éléments de valeur ou deux éléments clés.

La comparaison de valeurs retourne toujours false, et en outre, appelle `ATLASSERT` avec un argument false si elle est référencée. Dans les situations où le test d’égalité n’est pas suffisamment défini, cette classe permet à un mappage contenant des paires clé/valeur de fonctionner correctement pour la plupart des méthodes, mais qui échouent de manière bien définie pour les méthodes qui dépendent de comparaisons telles que [CSimpleMap :: FindVal](../../atl/reference/csimplemap-class.md#findval).

## <a name="requirements"></a>Spécifications

**En-tête :** atlsimpcoll. h

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a> CSimpleMapEqualHelperFalse::IsEqualKey

Teste l’égalité de deux clés.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Paramètres

*k1*<br/>
Première clé.

*k2*<br/>
Deuxième clé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si les clés sont égales ; sinon, false.

### <a name="remarks"></a>Notes

Cette méthode appelle [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a> CSimpleMapEqualHelperFalse::IsEqualValue

Retourne false.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne false.

### <a name="remarks"></a>Notes

Cette méthode retourne toujours la valeur false et appelle `ATLASSERT` avec l’argument false si elle est référencée. L’objectif de `CSimpleMapEqualHelperFalse::IsEqualValue` est de forcer les méthodes utilisant des comparaisons à échouer de manière bien définie lorsque les tests d’égalité n’ont pas été correctement définis.

## <a name="see-also"></a>Voir aussi

[CSimpleMapEqualHelper, classe](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
