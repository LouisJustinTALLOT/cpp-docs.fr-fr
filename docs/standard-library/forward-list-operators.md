---
title: '&lt;forward_list&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
dev_langs:
- C++
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: 7966d428dd200f0cbb280c679c4072e1ad75757a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846748"
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list&gt;, opérateurs

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet de type `forward_list`.|
|`right`|Objet de type `forward_list`.|

### <a name="remarks"></a>Notes

Cette fonction de modèle surcharge `operator==` pour comparer deux objets de la classe de modèle `forward_list`. La fonction retourne `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a>  operator!=

Vérifie si l’objet de liste forward_list à gauche de l’opérateur n’est pas égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet de type `forward_list`.|
|`right`|Objet de type `forward_list`.|

### <a name="return-value"></a>Valeur de retour

**true** si les listes ne sont pas égales ; **false** si les listes sont égales.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(left == right)`.

## <a name="op_lt"></a>  operator&lt;

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est inférieur à l’objet de liste forward_list situé à droite.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet de type `forward_list`.|
|`right`|Objet de type `forward_list`.|

### <a name="return-value"></a>Valeur de retour

`true` si la liste à gauche de l’opérateur est inférieure et non égale à la liste à droite de l’opérateur ; sinon, `false`.

### <a name="remarks"></a>Notes

Cette fonction de modèle surcharge `operator<` pour comparer deux objets de la classe de modèle `forward_list`. La fonction retourne `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a>  operator&lt;=

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est inférieur ou égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet de type `forward_list`.|
|`right`|Objet de type `forward_list`.|

### <a name="return-value"></a>Valeur de retour

`true` si la liste à gauche de l’opérateur est inférieure ou égale à la liste à droite de l’opérateur ; sinon, `false`.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(right < left)`.

## <a name="op_gt"></a>  operator&gt;

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est supérieur à l’objet de liste forward_list situé à droite.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet de type `forward_list`.|
|`right`|Objet de type `forward_list`.|

### <a name="return-value"></a>Valeur de retour

`true` si la liste à gauche de l’opérateur est supérieure à la liste à droite de l’opérateur ; sinon, `false`.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `right < left`.

## <a name="op_gt_eq"></a>  operator&gt;=

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est supérieur ou égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet de type `forward_list`.|
|`right`|Objet de type `forward_list`.|

### <a name="return-value"></a>Valeur de retour

`true` si la liste forward_list à gauche de l’opérateur est supérieure ou égale à la liste forward_list à droite de l’opérateur ; sinon, `false`.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `!(left < right)`.

## <a name="see-also"></a>Voir aussi

[<forward_list>](../standard-library/forward-list.md)<br/>
