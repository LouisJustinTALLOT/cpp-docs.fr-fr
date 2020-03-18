---
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
ms.openlocfilehash: 1ddfb56c7ff68ec10c7bb56af3495e4042acb83c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421792"
---
# <a name="ltforward_listgt-operators"></a>&lt;forward_list&gt;, opérateurs

## <a name="op_eq_eq"></a>opérateur = =

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `forward_list`.

\ *droit*
Objet de type `forward_list`.

### <a name="remarks"></a>Notes

Cette fonction de modèle surcharge `operator==` pour comparer deux objets de `forward_list`de modèle de classe. La fonction retourne `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a>opérateur ! =

Vérifie si l’objet de liste forward_list à gauche de l’opérateur n’est pas égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `forward_list`.

\ *droit*
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur de retour

**true** si les listes ne sont pas égales ; **false** si les listes sont égales.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(left == right)`.

## <a name="op_lt"></a>, opérateur&lt;

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est inférieur à l’objet de liste forward_list situé à droite.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `forward_list`.

\ *droit*
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur de retour

**true** si la liste située à gauche de l’opérateur est inférieure mais pas égale à la liste située à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction de modèle surcharge `operator<` pour comparer deux objets de `forward_list`de modèle de classe. La fonction retourne `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a>&lt;d’opérateur =

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est inférieur ou égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `forward_list`.

\ *droit*
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur de retour

**true** si la liste située à gauche de l’opérateur est inférieure ou égale à la liste située à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(right < left)`.

## <a name="op_gt"></a>, opérateur&gt;

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est supérieur à l’objet de liste forward_list situé à droite.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `forward_list`.

\ *droit*
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur de retour

**true** si la liste située à gauche de l’opérateur est supérieure à la liste située à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `right < left`.

## <a name="op_gt_eq"></a>&gt;d’opérateur =

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est supérieur ou égal à l’objet de liste forward_list situé à droite.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `forward_list`.

\ *droit*
Objet de type `forward_list`.

### <a name="return-value"></a>Valeur de retour

**true** si la liste de transferts sur le côté gauche de l’opérateur est supérieure ou égale à la liste de transferts à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `!(left < right)`.
