---
title: '&lt;system_error&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
dev_langs:
- C++
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: d0a556505370078f599d6d667fa856723d9bac8f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856796"
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error&gt;, opérateurs

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&lt;](#op_lt)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

Teste si l’objet situé à gauche de l’opérateur est égal à l’objet situé à droite.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet dont l’égalité doit être vérifiée.|
|`right`|Objet dont l’égalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**true** si les objets sont égaux ; **false** si les objets ne sont pas égaux.

### <a name="remarks"></a>Notes

Cette fonction retourne `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a>  operator!=

Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.

```cpp
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet dont l’inégalité doit être vérifiée.|
|`right`|Objet dont l’inégalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**true** si l’objet passé dans `left` n’est pas égal à l’objet passé dans `right` ; sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction retourne `!(left == right)`.

## <a name="op_lt"></a>  operator&lt;

Vérifie si un objet est inférieur à l'objet passé en vue de leur comparaison.

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet à comparer.|
|`right`|Objet à comparer.|

### <a name="return-value"></a>Valeur de retour

**true** si l’objet passé dans `left` est inférieur à l’objet passé dans `right` ; sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction permet de tester l'ordre des erreurs.

## <a name="see-also"></a>Voir aussi

[<system_error>](../standard-library/system-error.md)<br/>
