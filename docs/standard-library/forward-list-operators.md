---
description: 'En savoir plus sur les opérateurs suivants : &lt; forward_list &gt;'
title: '&lt;forward_list&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: 39d3383e0489a544f65f18af3ff3c2b6d8f2e45d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232354"
---
# <a name="ltforward_listgt-operators"></a>&lt;forward_list&gt;, opérateurs

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `forward_list`.

*Oui*\
Objet de type `forward_list`.

### <a name="remarks"></a>Notes

Cette fonction de modèle surcharge `operator==` pour comparer deux objets de la classe template `forward_list` . La fonction retourne `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Vérifie si l’objet de liste forward_list à gauche de l’opérateur n’est pas égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `forward_list`.

*Oui*\
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les listes ne sont pas égales ; **`false`** si les listes sont égales.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(left == right)`.

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est inférieur à l’objet de liste forward_list situé à droite.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `forward_list`.

*Oui*\
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la liste située à gauche de l’opérateur est inférieure mais pas égale à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction de modèle surcharge `operator<` pour comparer deux objets de la classe template `forward_list` . La fonction retourne `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="operatorlt"></a><a name="op_lt_eq"></a> and&lt;=

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est inférieur ou égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `forward_list`.

*Oui*\
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la liste située à gauche de l’opérateur est inférieure ou égale à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(right < left)`.

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est supérieur à l’objet de liste forward_list situé à droite.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `forward_list`.

*Oui*\
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la liste située à gauche de l’opérateur est supérieure à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `right < left`.

## <a name="operatorgt"></a><a name="op_gt_eq"></a> and&gt;=

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est supérieur ou égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `forward_list`.

*Oui*\
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la liste de transferts sur le côté gauche de l’opérateur est supérieure ou égale à la liste de transferts située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La fonction de modèle retourne `!(left < right)`.
