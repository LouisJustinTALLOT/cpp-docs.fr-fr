---
title: error_condition, classe
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
ms.openlocfilehash: cbadf6a22871cc9a23d37c095a398490c8a4c72c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245801"
---
# <a name="errorcondition-class"></a>error_condition, classe

Représente des codes d’erreur définis par l’utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
class error_condition;
```

## <a name="remarks"></a>Notes

Un objet de type `error_condition` stocke une valeur de code d’erreur et un pointeur vers un objet qui représente une [catégorie](../standard-library/error-category-class.md) de codes d’erreur que vous utilisez pour signaler les erreurs définies par l’utilisateur.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[error_condition](#error_condition)|Construit un objet de type `error_condition`.|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[value_type](#value_type)|Type qui représente la valeur de code d’erreur stockée.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[assign](#assign)|Assigne une valeur de code d’erreur et une catégorie à une condition d’erreur.|
|[category](#category)|Retourne la catégorie de l’erreur.|
|[clear](#clear)|Efface la valeur de code d’erreur et la catégorie.|
|[message](#message)|Retourne le nom du code d’erreur.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator==](#op_eq_eq)|Vérifie l’égalité d’objets `error_condition`.|
|[!=, opérateur](#op_neq)|Vérifie l’inégalité d’objets `error_condition`.|
|[operator<](#op_lt)|Vérifie si l’objet `error_condition` est inférieur à l’objet `error_code` transmis pour la comparaison.|
|[operator=](#op_eq)|Assigne une nouvelle valeur d’énumération à l’objet `error_condition`.|
|[operator bool](#op_bool)|Convertit une variable de type `error_condition`.|

### <a name="assign"></a> Affecter

Assigne une valeur de code d’erreur et une catégorie à une condition d’erreur.

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>Paramètres

*Val*\
Valeur de code d’erreur à stocker dans `error_code`.

*_Cat*\
Catégorie d’erreur à stocker dans `error_code`.

#### <a name="remarks"></a>Notes

La fonction membre stocke *val* en tant que la valeur de code d’erreur et un pointeur vers *_Cat*.

### <a name="category"></a> Catégorie

Retourne la catégorie de l’erreur.

```cpp
const error_category& category() const;
```

#### <a name="return-value"></a>Valeur de retour

Référence à la catégorie d’erreur stockée

#### <a name="remarks"></a>Notes

### <a name="clear"></a> Effacer

Efface la valeur de code d’erreur et la catégorie.

```cpp
clear();
```

#### <a name="remarks"></a>Notes

La fonction membre stocke une valeur de code d’erreur égale à zéro et un pointeur vers l’objet [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="error_condition"></a> error_condition

Construit un objet de type `error_condition`.

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Paramètres

*Val*\
Valeur de code d’erreur à stocker dans `error_condition`.

*_Cat*\
Catégorie d’erreur à stocker dans `error_condition`.

*_Errcode*\
Valeur d’énumération à stocker dans `error_condition`.

#### <a name="remarks"></a>Notes

Le premier constructeur stocke une valeur de code d’erreur égale à zéro et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category).

Le deuxième constructeur stocke *val* en tant que la valeur de code d’erreur et un pointeur vers [error_category](../standard-library/error-category-class.md).

Le troisième constructeur stocke `(value_type)_Errcode` comme valeur de code d’erreur et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="message"></a> Message

Retourne le nom du code d’erreur.

```cpp
string message() const;
```

#### <a name="return-value"></a>Valeur de retour

`string` représentant le nom du code d’erreur.

#### <a name="remarks"></a>Notes

La fonction membre retourne `category().message(value())`.

### <a name="op_eq_eq"></a> operator==

Vérifie l’égalité d’objets `error_condition`.

```cpp
bool operator==(const error_condition& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet dont l’égalité doit être vérifiée.

#### <a name="return-value"></a>Valeur de retour

**true** si les objets sont égaux ; **false** si les objets ne sont pas égaux.

#### <a name="remarks"></a>Notes

L’opérateur membre retourne `category() == right.category() && value == right.value()`.

### <a name="op_neq"></a> opérateur ! =

Vérifie l’inégalité d’objets `error_condition`.

```cpp
bool operator!=(const error_condition& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet dont l’inégalité doit être vérifiée.

#### <a name="return-value"></a>Valeur de retour

**true** si le `error_condition` objet n’est pas égal à la `error_condition` objet passé dans *droit*; sinon **false**.

#### <a name="remarks"></a>Notes

L’opérateur membre retourne `!(*this == right)`.

### <a name="op_lt"></a>, opérateur&lt;

Vérifie si l’objet `error_condition` est inférieur à l’objet `error_code` transmis pour la comparaison.

```cpp
bool operator<(const error_condition& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet `error_condition` à comparer.

#### <a name="return-value"></a>Valeur de retour

**true** si l’objet `error_condition` est inférieur à l’objet `error_condition` transmis pour la comparaison ; sinon, **false**.

#### <a name="remarks"></a>Notes

L’opérateur membre retourne `category() < right.category() || category() == right.category() && value < right.value()`.

### <a name="op_eq"></a> opérateur =

Assigne une nouvelle valeur d’énumération à l’objet `error_condition`.

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
    operator=(Enum _Errcode);
```

#### <a name="parameters"></a>Paramètres

*_Errcode*\
Valeur d’énumération à assigner à l’objet `error_condition`.

#### <a name="return-value"></a>Valeur de retour

Référence à l’objet `error_condition` auquel la fonction membre assigne la nouvelle valeur d’énumération.

#### <a name="remarks"></a>Notes

L’opérateur membre stocke `(value_type)error` comme valeur de code d’erreur et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category). Il retourne `*this`.

### <a name="op_bool"></a> opérateur bool

Convertit une variable de type `error_condition`.

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Valeur de retour

Valeur booléenne de l’objet `error_condition`.

#### <a name="remarks"></a>Notes

L’opérateur retourne une valeur convertible en **true** uniquement si [valeur](#value) n’est pas égal à zéro. Le type de retour est convertible uniquement en **bool**et non en `void *` ou autre type scalaire connu.

### <a name="value"></a> Valeur

Retourne la valeur de code d’erreur stockée.

```cpp
value_type value() const;
```

#### <a name="return-value"></a>Valeur de retour

Valeur de code d’erreur stockée de type [value_type](#value_type).

#### <a name="remarks"></a>Notes

### <a name="value_type"></a> Value_type

Type qui représente la valeur de code d’erreur stockée.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Notes

La définition de type est un synonyme de **int**.
