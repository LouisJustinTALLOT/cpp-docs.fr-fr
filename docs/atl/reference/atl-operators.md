---
description: 'En savoir plus sur : opérateurs ATL'
title: Opérateurs ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c336732aeee9146b89e300580c0fbee506ec343
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158684"
---
# <a name="atl-operators"></a>Opérateurs ATL

Cette section contient les rubriques de référence pour les opérateurs globaux ATL.

|Opérateur|Description|
|--------------|-----------------|
|[opérateur = =](#operator_eq_eq)|Compare l' `CSid` égalité de deux objets ou `SID` structures.|
|[opérateur ! =](#operator_neq)|Compare l' `CSid` `SID` inégalité de deux objets ou structures.|
|[<d’opérateur ](#operator_lt)|Teste si l' `CSid` objet ou la `SID` structure situé à gauche de l’opérateur est inférieur à l' `CSid` objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).|
|[>d’opérateur ](#operator_gt)|Teste si l' `CSid` objet ou la `SID` structure situé à gauche de l’opérateur est supérieur à l' `CSid` objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).|
|[<opérateur =](#operator_lt__eq)|Teste si l' `CSid` objet ou la `SID` structure situé à gauche de l’opérateur est inférieur ou égal à l' `CSid` objet ou à la `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).|
|[>opérateur =](#operator_gt__eq)|Teste si l' `CSid` objet ou la `SID` structure situé à gauche de l’opérateur est supérieur ou égal à l' `CSid` objet ou à la `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).|

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h.

## <a name="operator-"></a><a name="operator_eq_eq"></a> opérateur = =

Compare `CSid` les objets ou `SID` les structures (identificateur de sécurité) pour déterminer leur égalité.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si les objets sont égaux, FALSe s’ils ne sont pas égaux.

## <a name="operator-"></a><a name="operator_neq"></a> opérateur ! =

Compare l' `CSid` `SID` inégalité des objets ou des structures (identificateur de sécurité).

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si les objets ne sont pas égaux, FALSe s’ils sont égaux.

## <a name="operator-"></a><a name="operator_lt"></a> < d’opérateur

Teste si l' `CSid` objet ou la `SID` structure situé à gauche de l’opérateur est inférieur à l' `CSid` objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’adresse de l’objet *LHS* est inférieure à l’adresse de l’objet *RHS* ; sinon, false.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de l' `CSid` objet ou de la `SID` structure, et est implémenté pour assurer la compatibilité avec les classes de collection de la bibliothèque standard C++.

## <a name="operator-"></a><a name="operator_gt"></a> > d’opérateur

Teste si l' `CSid` objet ou la `SID` structure situé à gauche de l’opérateur est supérieur à l' `CSid` objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’adresse de l' *LHS* est supérieure à l’adresse du *RHS*; sinon, false.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de l' `CSid` objet ou de la `SID` structure, et est implémenté pour assurer la compatibilité avec les classes de collection de la bibliothèque standard C++.

## <a name="operator-"></a><a name="operator_lt__eq"></a> <opérateur =

Teste si l' `CSid` objet ou la `SID` structure situé à gauche de l’opérateur est inférieur ou égal à l' `CSid` objet ou à la `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’adresse de l' *LHS* est inférieure ou égale à l’adresse du *RHS*; sinon, false.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de l' `CSid` objet ou de la `SID` structure, et est implémenté pour assurer la compatibilité avec les classes de collection de la bibliothèque standard C++.

## <a name="operator-"></a><a name="operator_gt__eq"></a> >opérateur =

Teste si l' `CSid` objet ou la `SID` structure situé à gauche de l’opérateur est supérieur ou égal à l' `CSid` objet ou à la `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’adresse de l' *LHS* est supérieure ou égale à l’adresse du *RHS*; sinon, false.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de l' `CSid` objet ou de la `SID` structure, et est implémenté pour assurer la compatibilité avec les classes de collection de la bibliothèque standard C++.
