---
title: error_category, classe
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: ced6046b93a8d5140118e1e9de848df13a8c29c4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224875"
---
# <a name="error_category-class"></a>error_category, classe

Représente la base commune abstraite d’objets qui décrit une catégorie des codes d’erreur.

## <a name="syntax"></a>Syntaxe

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>Notes

Deux objets prédéfinis implémentent `error_category` : [generic_category](../standard-library/system-error-functions.md#generic_category) et [system_category](../standard-library/system-error-functions.md#system_category).

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Type qui représente la valeur de code d’erreur stockée.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[default_error_condition](#default_error_condition)|Stocke la valeur de code d’erreur d’un objet de condition d’erreur.|
|[identique](#equivalent)|Retourne une valeur qui spécifie si les objets d’erreur sont équivalents.|
|[generic_category](#generic)||
|[message](#message)|Retourne le nom du code d’erreur spécifié.|
|[name](#name)|Retourne le nom de la catégorie.|
|[system_category](#system)||

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](#op_as)||
|[opérateur = =](#op_eq_eq)|Vérifie l’égalité d’objets `error_category`.|
|[opérateur ! =](#op_neq)|Vérifie l’inégalité d’objets `error_category`.|
|[<d’opérateur](#op_lt)|Vérifie si l’objet [error_category](../standard-library/error-category-class.md) est inférieur à l’objet `error_category` transmis pour la comparaison.|

## <a name="default_error_condition"></a><a name="default_error_condition"></a>default_error_condition

Stocke la valeur de code d’erreur d’un objet de condition d’erreur.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Paramètres

`_Errval`\
Valeur de code d’erreur à stocker dans [error_condition](../standard-library/error-condition-class.md).

### <a name="return-value"></a>Valeur de retour

Retourne `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Notes

### <a name="equivalent"></a><a name="equivalent"></a>identique

Retourne une valeur qui spécifie si les objets d’erreur sont équivalents.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>Paramètres

*_Errval*\
Valeur de code d’erreur à comparer.

*_Cond*\
Objet [error_condition](../standard-library/error-condition-class.md) à comparer.

*_Code*\
Objet [error_code](../standard-library/error-code-class.md) à comparer.

#### <a name="return-value"></a>Valeur de retour

**`true`** Si la catégorie et la valeur sont égales ; Sinon, **`false`** .

#### <a name="remarks"></a>Notes

La première fonction membre retourne `*this == _Cond.category() && _Cond.value() == _Errval`.

La deuxième fonction membre retourne `*this == _Code.category() && _Code.value() == _Errval`.

### <a name="generic_category"></a><a name="generic"></a>generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a>Message

Retourne le nom du code d’erreur spécifié.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>Paramètres

*multiples*\
Valeur de code d’erreur à décrire.

#### <a name="return-value"></a>Valeur de retour

Retourne un nom descriptif du code d’erreur *Val* pour la catégorie. Si le code d’erreur n’est pas reconnu, retourne `"unknown error"` .

#### <a name="remarks"></a>Notes

### <a name="name"></a>Nom <a name="name"></a>

Retourne le nom de la catégorie.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>Valeur de retour

Retourne le nom de la catégorie sous forme de chaîne d’octets terminée par un caractère null.

### <a name="operator"></a><a name="op_as"></a>opérateur =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a>opérateur = =

Vérifie l’égalité d’objets `error_category`.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet dont l’égalité doit être vérifiée.

#### <a name="return-value"></a>Valeur de retour

**`true`** Si les objets sont égaux ; **`false`** si les objets ne sont pas égaux.

#### <a name="remarks"></a>Notes

Cet opérateur membre retourne `this == &right`.

### <a name="operator"></a><a name="op_neq"></a>opérateur ! =

Vérifie l’inégalité d’objets `error_category`.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet dont l’inégalité doit être vérifiée.

#### <a name="return-value"></a>Valeur de retour

**`true`** Si l' `error_category` objet n’est pas égal à l' `error_category` objet passé à *droite*; sinon, **`false`** .

#### <a name="remarks"></a>Notes

L’opérateur membre retourne `(!*this == right)`.

### <a name="operatorlt"></a><a name="op_lt"></a>and&lt;

Vérifie si l’objet [error_category](../standard-library/error-category-class.md) est inférieur à l’objet `error_category` transmis pour la comparaison.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Objet `error_category` à comparer.

#### <a name="return-value"></a>Valeur de retour

**`true`** Si l' `error_category` objet est inférieur à l' `error_category` objet passé pour la comparaison ; Sinon, **`false`** .

#### <a name="remarks"></a>Notes

L’opérateur membre retourne `this < &right`.

### <a name="system_category"></a><a name="system"></a>system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a>value_type

Type qui représente la valeur de code d’erreur stockée.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Notes

Cette définition de type est un synonyme de **`int`** .
