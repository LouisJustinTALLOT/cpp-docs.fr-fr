---
title: Opérateurs ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: fe5363d3d05123c17e45254898e2210797400022
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168850"
---
# <a name="atl-operators"></a>Opérateurs ATL

Cette section contient les rubriques de référence pour les opérateurs globaux ATL.

|Opérateur|Description|
|--------------|-----------------|
|[opérateur = =](#operator_eq_eq)|Compare l' `CSid` égalité de `SID` deux objets ou structures.|
|[opérateur ! =](#operator_neq)|Compare l' `CSid` inégalité de deux objets ou `SID` structures.|
|[<d’opérateur](#operator_lt)|Teste si `CSid` l’objet `SID` ou la structure situé à gauche de l’opérateur est inférieur à `CSid` l’objet `SID` ou à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).|
|[>d’opérateur](#operator_gt)|Teste si `CSid` l’objet `SID` ou la structure situé à gauche de l’opérateur est supérieur à `CSid` l’objet `SID` ou à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).|
|[<opérateur =](#operator_lt__eq)|Teste si `CSid` l’objet `SID` ou la structure situé à gauche de l’opérateur est inférieur ou égal à l' `CSid` objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).|
|[>opérateur =](#operator_gt__eq)|Teste si `CSid` l’objet `SID` ou la structure situé à gauche de l’opérateur est supérieur ou égal à l' `CSid` objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).|

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>opérateur = =

Compare `CSid` les objets `SID` ou les structures (identificateur de sécurité) pour déterminer leur égalité.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux, FALSe s’ils ne sont pas égaux.

## <a name="operator-"></a><a name="operator_neq"></a>opérateur ! =

Compare `CSid` l’inégalité des objets ou `SID` des structures (identificateur de sécurité).

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets ne sont pas égaux, FALSe s’ils sont égaux.

## <a name="operator-"></a><a name="operator_lt"></a>< d’opérateur

Teste si `CSid` l’objet `SID` ou la structure situé à gauche de l’opérateur est inférieur à `CSid` l’objet `SID` ou à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de l’objet *LHS* est inférieure à l’adresse de l’objet *RHS* ; sinon, false.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de l' `CSid` objet ou `SID` de la structure, et est implémenté pour assurer la compatibilité avec les classes de collection de la bibliothèque standard C++.

## <a name="operator-"></a><a name="operator_gt"></a>> d’opérateur

Teste si `CSid` l’objet `SID` ou la structure situé à gauche de l’opérateur est supérieur à `CSid` l’objet `SID` ou à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de l' *LHS* est supérieure à l’adresse du *RHS*; sinon, false.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de l' `CSid` objet ou `SID` de la structure, et est implémenté pour assurer la compatibilité avec les classes de collection de la bibliothèque standard C++.

## <a name="operator-"></a><a name="operator_lt__eq"></a><opérateur =

Teste si `CSid` l’objet `SID` ou la structure situé à gauche de l’opérateur est inférieur ou égal à l' `CSid` objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de l' *LHS* est inférieure ou égale à l’adresse du *RHS*; sinon, false.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de l' `CSid` objet ou `SID` de la structure, et est implémenté pour assurer la compatibilité avec les classes de collection de la bibliothèque standard C++.

## <a name="operator-"></a><a name="operator_gt__eq"></a>>opérateur =

Teste si `CSid` l’objet `SID` ou la structure situé à gauche de l’opérateur est supérieur ou égal à l' `CSid` objet ou `SID` à la structure sur le côté droit (pour la compatibilité de la bibliothèque standard C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
Deuxième `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de l' *LHS* est supérieure ou égale à l’adresse du *RHS*; sinon, false.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de l' `CSid` objet ou `SID` de la structure, et est implémenté pour assurer la compatibilité avec les classes de collection de la bibliothèque standard C++.
