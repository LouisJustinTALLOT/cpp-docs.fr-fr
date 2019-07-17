---
title: '&lt;system_error&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5cf6a455beb5654ef65f7411db4783a32c71d625
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246213"
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error&gt;, opérateurs

## <a name="op_eq_eq"></a> operator==

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

*Gauche*\
Objet dont l’égalité doit être vérifiée.

*Oui*\
Objet dont l’égalité doit être vérifiée.

### <a name="return-value"></a>Valeur de retour

**true** si les objets sont égaux ; **false** si les objets ne sont pas égaux.

### <a name="remarks"></a>Notes

Cette fonction retourne `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a> opérateur ! =

Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet dont l’inégalité doit être vérifiée.

*Oui*\
Objet dont l’inégalité doit être vérifiée.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet passé dans *gauche* n’est pas égal à l’objet passé dans *droit*; sinon **false**.

### <a name="remarks"></a>Notes

Cette fonction retourne `!(left == right)`.

## <a name="op_lt"></a>, opérateur&lt;

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

*Gauche*\
Objet à comparer.

*Oui*\
Objet à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet passé dans *gauche* est inférieur à l’objet passé dans *droite*; Sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction permet de tester l'ordre des erreurs.

## <a name="op_ostream"></a> Opérateur&lt;&lt;

```cpp
template <class charT, class traits> 
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
