---
title: Opérateurs ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c15daa1d2b12c58323ef5ef75559a2ab911ad93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319232"
---
# <a name="atl-operators"></a>Opérateurs ATL

Cette section contient les sujets de référence pour les opérateurs mondiaux ATL.

|Opérateur|Description|
|--------------|-----------------|
|[opérateur](#operator_eq_eq)|Compare deux `CSid` objets `SID` ou structures pour l’égalité.|
|[opérateur !](#operator_neq)|Compare deux `CSid` objets `SID` ou structures à des fins d’inégalité.|
|[<de l’opérateur](#operator_lt)|Test si `CSid` l’objet ou `SID` la structure du côté `CSid` gauche `SID` de l’opérateur est inférieur à l’objet ou à la structure sur le côté droit (pour la compatibilité de la Bibliothèque standard C).|
|[>de l’opérateur](#operator_gt)|Test si `CSid` l’objet ou `SID` la structure du côté `CSid` gauche `SID` de l’opérateur est supérieur à l’objet ou à la structure sur le côté droit (pour la compatibilité de la Bibliothèque standard de CMD).|
|[<de l’opérateur](#operator_lt__eq)|Test si `CSid` l’objet ou `SID` la structure du côté gauche de `CSid` l’opérateur est inférieur ou égal à l’objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard de CMD).|
|[>de l’opérateur](#operator_gt__eq)|Test si `CSid` l’objet ou `SID` la structure du côté gauche `CSid` de `SID` l’opérateur est supérieur ou égal à l’objet ou à la structure sur le côté droit (pour la compatibilité de la Bibliothèque standard C).|

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>opérateur

Compare `CSid` les `SID` objets ou les structures (identifiantes de sécurité) pour l’égalité.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le `CSid` premier `SID` objet ou structure à comparer.

*rhs*<br/>
Le `CSid` deuxième `SID` objet ou structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si les objets sont égaux, FALSE s’ils ne sont pas égaux.

## <a name="operator-"></a><a name="operator_neq"></a>opérateur !

Compare `CSid` les `SID` objets ou les structures (identifiantes de sécurité) pour les inégalités.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le `CSid` premier `SID` objet ou structure à comparer.

*rhs*<br/>
Le `CSid` deuxième `SID` objet ou structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si les objets ne sont pas égaux, FALSE s’ils sont égaux.

## <a name="operator-"></a><a name="operator_lt"></a>< de l’opérateur

Test si `CSid` l’objet ou `SID` la structure du côté `CSid` gauche `SID` de l’opérateur est inférieur à l’objet ou à la structure sur le côté droit (pour la compatibilité de la Bibliothèque standard C).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le `CSid` premier `SID` objet ou structure à comparer.

*rhs*<br/>
Le `CSid` deuxième `SID` objet ou structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’adresse de *l’objet lhs* est inférieure à l’adresse de l’objet *rhs,* FALSE autrement.

### <a name="remarks"></a>Notes

Cet opérateur agit sur `CSid` l’adresse de l’objet ou `SID` de la structure, et est mis en œuvre pour fournir la compatibilité avec les classes de collecte de la Bibliothèque standard.

## <a name="operator-"></a><a name="operator_gt"></a>> de l’opérateur

Test si `CSid` l’objet ou `SID` la structure du côté `CSid` gauche `SID` de l’opérateur est supérieur à l’objet ou à la structure sur le côté droit (pour la compatibilité de la Bibliothèque standard de CMD).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le `CSid` premier `SID` objet ou structure à comparer.

*rhs*<br/>
Le `CSid` deuxième `SID` objet ou structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’adresse de la *lhs* est plus grande que l’adresse des *rhs*, FALSE autrement.

### <a name="remarks"></a>Notes

Cet opérateur agit sur `CSid` l’adresse de l’objet ou `SID` de la structure, et est mis en œuvre pour fournir la compatibilité avec les classes de collecte de la Bibliothèque standard.

## <a name="operator-"></a><a name="operator_lt__eq"></a><de l’opérateur

Test si `CSid` l’objet ou `SID` la structure du côté gauche de `CSid` l’opérateur est inférieur ou égal à l’objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard de CMD).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le `CSid` premier `SID` objet ou structure à comparer.

*rhs*<br/>
Le `CSid` deuxième `SID` objet ou structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’adresse de la *lhs* est inférieure ou égale à l’adresse des *rhs*, FALSE autrement.

### <a name="remarks"></a>Notes

Cet opérateur agit sur `CSid` l’adresse de l’objet ou `SID` de la structure, et est mis en œuvre pour fournir la compatibilité avec les classes de collecte de la Bibliothèque standard.

## <a name="operator-"></a><a name="operator_gt__eq"></a>>de l’opérateur

Test si `CSid` l’objet ou `SID` la structure du côté gauche `CSid` de `SID` l’opérateur est supérieur ou égal à l’objet ou à la structure sur le côté droit (pour la compatibilité de la Bibliothèque standard C).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le `CSid` premier `SID` objet ou structure à comparer.

*rhs*<br/>
Le `CSid` deuxième `SID` objet ou structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’adresse de la *lhs* est supérieure ou égale à l’adresse des *rhs*, FALSE autrement.

### <a name="remarks"></a>Notes

Cet opérateur agit sur `CSid` l’adresse de l’objet ou `SID` de la structure, et est mis en œuvre pour fournir la compatibilité avec les classes de collecte de la Bibliothèque standard.
