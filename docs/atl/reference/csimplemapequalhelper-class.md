---
title: Csimplemapequalhelper, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: a530254bbaabce723b97d21313abb81e1b375833
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527386"
---
# <a name="csimplemapequalhelper-class"></a>Csimplemapequalhelper, classe

Cette classe est une application d’assistance pour la [CSimpleMap](../../atl/reference/csimplemap-class.md) classe.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Paramètres

*TKey*<br/>
L’élément clé.

*TVal*<br/>
L’élément de valeur.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statique) Teste l’égalité de deux clés.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statique) Teste l’égalité de deux valeurs.|

## <a name="remarks"></a>Notes

Cette classe de traits constitue un supplément pour le `CSimpleMap` classe. Il fournit des méthodes pour la comparaison de deux `CSimpleMap` éléments (plus précisément, les composants clé et valeur) pour l’égalité de l’objet. Par défaut, les clés et valeurs sont comparées à l’aide de **Operator == ()**, mais si le mappage contient des types de données complexes qui ne disposent pas de leur propre opérateur d’égalité, cette classe peut être substituée pour fournir la fonctionnalité supplémentaire requise.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey

Teste l’égalité de deux clés.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Paramètres

*K1*<br/>
La première clé.

*K2*<br/>
La deuxième clé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les clés sont égales, sinon false.

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

Teste l’égalité de deux valeurs.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Paramètres

*V1*<br/>
Première valeur.

*v2*<br/>
Seconde valeur.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les valeurs sont égales, sinon false.

## <a name="see-also"></a>Voir aussi

[CSimpleMapEqualHelperFalse, classe](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
