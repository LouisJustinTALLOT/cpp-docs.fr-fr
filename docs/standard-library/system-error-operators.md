---
description: 'En savoir plus sur les opérateurs suivants : &lt; system_error &gt;'
title: '&lt;system_error&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 0ebbb4d9de0ef8bf27aaa276dfee14d94c29eabb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259420"
---
# <a name="ltsystem_errorgt-operators"></a>&lt;system_error&gt;, opérateurs

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si l’objet situé à gauche de l’opérateur est égal à l’objet situé à droite.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet dont l’égalité doit être vérifiée.

*Oui*\
Objet dont l’égalité doit être vérifiée.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les objets sont égaux ; **`false`** si les objets ne sont pas égaux.

### <a name="remarks"></a>Notes

Cette fonction retourne `left.category() == right.category() && left.value() == right.value()`.

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet dont l’inégalité doit être vérifiée.

*Oui*\
Objet dont l’inégalité doit être vérifiée.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’objet passé à *gauche* n’est pas égal à l’objet passé à *droite*; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction retourne `!(left == right)`.

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

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

*gauche*\
Objet à comparer.

*Oui*\
Objet à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’objet passé à *gauche* est inférieur à l’objet passé à *droite*; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction permet de tester l'ordre des erreurs.

## <a name="operatorltlt"></a><a name="op_ostream"></a> and&lt;&lt;

```cpp
template <class charT, class traits>
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
