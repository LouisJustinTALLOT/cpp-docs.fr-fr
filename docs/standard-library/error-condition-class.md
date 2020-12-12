---
description: 'En savoir plus sur : classe error_condition'
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
ms.openlocfilehash: 6567a4406271147eadfdc9e9443ba333d931afba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232679"
---
# <a name="error_condition-class"></a>error_condition, classe

Représente les codes d’erreur définis par l’utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
class error_condition;
```

## <a name="remarks"></a>Notes

Un objet de type `error_condition` stocke une valeur de code d’erreur et un pointeur vers un objet qui représente une [catégorie](../standard-library/error-category-class.md) de codes d’erreur que vous utilisez pour signaler les erreurs définies par l’utilisateur.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[error_condition](#error_condition)|Construit un objet de type `error_condition`.|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|[value_type](#value_type)|Type qui représente la valeur de code d’erreur stockée.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[assign](#assign)|Assigne une valeur de code d’erreur et une catégorie à une condition d’erreur.|
|[category](#category)|Retourne la catégorie de l’erreur.|
|[clear](#clear)|Efface la valeur de code d’erreur et la catégorie.|
|[message](#message)|Retourne le nom du code d’erreur.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur = =](#op_eq_eq)|Vérifie l’égalité d’objets `error_condition`.|
|[opérateur ! =](#op_neq)|Vérifie l’inégalité d’objets `error_condition`.|
|[<d’opérateur ](#op_lt)|Vérifie si l’objet `error_condition` est inférieur à l’objet `error_code` transmis pour la comparaison.|
|[opérateur =](#op_eq)|Assigne une nouvelle valeur d’énumération à l’objet `error_condition`.|
|[bool, opérateur](#op_bool)|Convertit une variable de type `error_condition`.|

### <a name="assign"></a><a name="assign"></a> assignés

Assigne une valeur de code d’erreur et une catégorie à une condition d’erreur.

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>Paramètres

*multiples*\
Valeur de code d’erreur à stocker dans `error_code`.

*_Cat*\
Catégorie d’erreur à stocker dans `error_code`.

#### <a name="remarks"></a>Notes

La fonction membre stocke *Val* comme valeur de code d’erreur et un pointeur vers *_Cat*.

### <a name="category"></a><a name="category"></a> catégorie

Retourne la catégorie de l’erreur.

```cpp
const error_category& category() const;
```

#### <a name="return-value"></a>Valeur renvoyée

Référence à la catégorie d’erreur stockée

#### <a name="remarks"></a>Notes

### <a name="clear"></a><a name="clear"></a> effacé

Efface la valeur de code d’erreur et la catégorie.

```cpp
clear();
```

#### <a name="remarks"></a>Notes

La fonction membre stocke une valeur de code d’erreur égale à zéro et un pointeur vers l’objet [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="error_condition"></a><a name="error_condition"></a> error_condition

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

*multiples*\
Valeur de code d’erreur à stocker dans `error_condition`.

*_Cat*\
Catégorie d’erreur à stocker dans `error_condition`.

*_Errcode*\
Valeur d’énumération à stocker dans `error_condition`.

#### <a name="remarks"></a>Notes

Le premier constructeur stocke une valeur de code d’erreur égale à zéro et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category).

Le deuxième constructeur stocke *Val* comme valeur de code d’erreur et un pointeur vers [error_category](../standard-library/error-category-class.md).

Le troisième constructeur stocke `(value_type)_Errcode` comme valeur de code d’erreur et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="message"></a><a name="message"></a> Message

Retourne le nom du code d’erreur.

```cpp
string message() const;
```

#### <a name="return-value"></a>Valeur renvoyée

`string` représentant le nom du code d’erreur.

#### <a name="remarks"></a>Notes

La fonction membre retourne `category().message(value())`.

### <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Vérifie l’égalité d’objets `error_condition`.

```cpp
bool operator==(const error_condition& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet dont l’égalité doit être vérifiée.

#### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les objets sont égaux ; **`false`** si les objets ne sont pas égaux.

#### <a name="remarks"></a>Notes

L’opérateur membre retourne `category() == right.category() && value == right.value()`.

### <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Vérifie l’inégalité d’objets `error_condition`.

```cpp
bool operator!=(const error_condition& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet dont l’inégalité doit être vérifiée.

#### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l' `error_condition` objet n’est pas égal à l' `error_condition` objet passé à *droite*; sinon, **`false`** .

#### <a name="remarks"></a>Notes

L’opérateur membre retourne `!(*this == right)`.

### <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

Vérifie si l’objet `error_condition` est inférieur à l’objet `error_code` transmis pour la comparaison.

```cpp
bool operator<(const error_condition& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet `error_condition` à comparer.

#### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l' `error_condition` objet est inférieur à l' `error_condition` objet passé pour la comparaison ; Sinon, **`false`** .

#### <a name="remarks"></a>Notes

L’opérateur membre retourne `category() < right.category() || category() == right.category() && value < right.value()`.

### <a name="operator"></a><a name="op_eq"></a> opérateur =

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

#### <a name="return-value"></a>Valeur renvoyée

Référence à l’objet `error_condition` auquel la fonction membre assigne la nouvelle valeur d’énumération.

#### <a name="remarks"></a>Notes

L’opérateur membre stocke `(value_type)error` comme valeur de code d’erreur et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category). Elle retourne **`*this`** .

### <a name="operator-bool"></a><a name="op_bool"></a> bool, opérateur

Convertit une variable de type `error_condition`.

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Valeur renvoyée

Valeur booléenne de l’objet `error_condition`.

#### <a name="remarks"></a>Notes

L’opérateur retourne une valeur convertible en **`true`** uniquement si la [valeur](#value) n’est pas égale à zéro. Le type de retour est convertible uniquement en **`bool`** , pas en ou en d' `void *` autres types scalaires connus.

### <a name="value"></a>Valeur <a name="value"></a>

Retourne la valeur de code d’erreur stockée.

```cpp
value_type value() const;
```

#### <a name="return-value"></a>Valeur renvoyée

Valeur de code d’erreur stockée de type [value_type](#value_type).

#### <a name="remarks"></a>Notes

### <a name="value_type"></a><a name="value_type"></a> value_type

Type qui représente la valeur de code d’erreur stockée.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Notes

La définition de type est un synonyme de **`int`** .
