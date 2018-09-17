---
title: error_code, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
dev_langs:
- C++
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b454a86957911060e33c82e79832e107313e0300
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703597"
---
# <a name="errorcode-class"></a>error_code, classe

Représente les erreurs système de bas niveau spécifiques de l’implémentation.

## <a name="syntax"></a>Syntaxe

```cpp
class error_code;
```

## <a name="remarks"></a>Notes

Un objet de type `error_code` stocke une valeur de code d’erreur et un pointeur vers un objet qui représente une [catégorie](../standard-library/error-category-class.md) de codes d’erreur décrivant les erreurs système de bas niveau signalées.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[error_code](#error_code)|Construit un objet de type `error_code`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[value_type](#value_type)|Type qui représente la valeur de code d’erreur stockée.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[assign](#assign)|Assigne une valeur de code d’erreur et une catégorie à un code d’erreur.|
|[category](#category)|Retourne la catégorie de l’erreur.|
|[clear](#clear)|Efface la valeur de code d’erreur et la catégorie.|
|[default_error_condition](#default_error_condition)|Retourne la condition d’erreur par défaut.|
|[message](#message)|Retourne le nom du code d’erreur.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator==](#op_eq_eq)|Vérifie l’égalité d’objets `error_code`.|
|[operator!=](#op_neq)|Vérifie l’inégalité d’objets `error_code`.|
|[operator<](#op_lt)|Vérifie si l’objet `error_code` est inférieur à l’objet `error_code` transmis pour la comparaison.|
|[operator=](#op_eq)|Assigne une nouvelle valeur d’énumération à l’objet `error_code`.|
|[operator bool](#op_bool)|Convertit une variable de type `error_code`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<system_error>

**Espace de noms :** std

## <a name="assign"></a>  error_code::assign

Assigne une valeur de code d’erreur et une catégorie à un code d’erreur.

```cpp
void assign(value_type val, const error_category& _Cat);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Val*|Valeur de code d’erreur à stocker dans `error_code`.|
|*_Cat*|Catégorie d’erreur à stocker dans `error_code`.|

### <a name="remarks"></a>Notes

La fonction membre stocke *val* en tant que la valeur de code d’erreur et un pointeur vers *_Cat*.

## <a name="category"></a>  error_code::category

Retourne la catégorie de l’erreur.

```cpp
const error_category& category() const;
```

### <a name="remarks"></a>Notes

## <a name="clear"></a>  error_code::clear

Efface la valeur de code d’erreur et la catégorie.

```cpp
clear();
```

### <a name="remarks"></a>Notes

La fonction membre stocke une valeur de code d’erreur égale à zéro et un pointeur vers l’objet [generic_category](../standard-library/system-error-functions.md#generic_category).

## <a name="default_error_condition"></a>  error_code::default_error_condition

Retourne la condition d’erreur par défaut.

```cpp
error_condition default_error_condition() const;
```

### <a name="return-value"></a>Valeur de retour

[error_condition](../standard-library/error-condition-class.md) spécifié par [default_error_condition](../standard-library/error-category-class.md#default_error_condition).

### <a name="remarks"></a>Notes

La fonction membre retourne `category().default_error_condition(value())`.

## <a name="error_code"></a>  error_code::error_code

Construit un objet de type `error_code`.

```cpp
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Val*|Valeur de code d’erreur à stocker dans `error_code`.|
|*_Cat*|Catégorie d’erreur à stocker dans `error_code`.|
|*_Errcode*|Valeur d’énumération à stocker dans `error_code`.|

### <a name="remarks"></a>Notes

Le premier constructeur stocke une valeur de code d’erreur égale à zéro et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category).

Le deuxième constructeur stocke *val* en tant que la valeur de code d’erreur et un pointeur vers [error_category](../standard-library/error-category-class.md).

Le troisième constructeur stocke `(value_type)_Errcode` comme valeur de code d’erreur et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category).

## <a name="message"></a>  error_code::message

Retourne le nom du code d’erreur.

```cpp
string message() const;
```

### <a name="return-value"></a>Valeur de retour

`string` représentant le nom du code d’erreur.

### <a name="remarks"></a>Notes

La fonction membre retourne `category().message(value())`.

## <a name="op_eq_eq"></a>  error_code::operator==

Vérifie l’égalité d’objets `error_code`.

```cpp
bool operator==(const error_code& right) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*right*|Objet dont l’égalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**true** si les objets sont égaux ; **false** si les objets ne sont pas égaux.

### <a name="remarks"></a>Notes

L’opérateur membre retourne `category() == right.category() && value == right.value()`.

## <a name="op_neq"></a>  error_code::operator!=

Vérifie l’inégalité d’objets `error_code`.

```cpp
bool operator!=(const error_code& right) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*right*|Objet dont l’inégalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**true** si le `error_code` objet n’est pas égal à la `error_code` objet passé dans *droit*; sinon **false**.

### <a name="remarks"></a>Notes

L’opérateur membre retourne `!(*this == right)`.

## <a name="op_lt"></a>  error_code::operator&lt;

Vérifie si l’objet `error_code` est inférieur à l’objet `error_code` transmis pour la comparaison.

```cpp
bool operator<(const error_code& right) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*right*|Objet error_code à comparer.|

### <a name="return-value"></a>Valeur de retour

**true** si l’objet `error_code` est inférieur à l’objet `error_code` transmis pour la comparaison ; sinon, **false**.

### <a name="remarks"></a>Notes

L’opérateur membre retourne `category() < right.category() || category() == right.category() && value < right.value()`.

## <a name="op_eq"></a>  error_code::operator=

Assigne une nouvelle valeur d’énumération à l’objet `error_code`.

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Errcode*|Valeur d’énumération à assigner à l’objet `error_code`.|

### <a name="return-value"></a>Valeur de retour

Référence à l’objet `error_code` auquel la fonction membre assigne la nouvelle valeur d’énumération.

### <a name="remarks"></a>Notes

L’opérateur membre stocke `(value_type)_Errcode` comme valeur de code d’erreur et un pointeur vers [generic_category](../standard-library/system-error-functions.md#generic_category). Il retourne `*this`.

## <a name="op_bool"></a>  error_code::operator bool

Convertit une variable de type `error_code`.

```cpp
explicit operator bool() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur booléenne de l’objet `error_code`.

### <a name="remarks"></a>Notes

L’opérateur retourne une valeur convertible en **true** uniquement si [valeur](#value) n’est pas égal à zéro. Le type de retour est convertible uniquement en **bool**et non en `void *` ou autre type scalaire connu.

## <a name="value"></a>  error_code::value

Retourne la valeur de code d’erreur stockée.

```cpp
value_type value() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de code d’erreur stockée de type [value_type](#value_type).

### <a name="remarks"></a>Notes

## <a name="value_type"></a>  error_code::value_type

Type qui représente la valeur de code d’erreur stockée.

```cpp
typedef int value_type;
```

### <a name="remarks"></a>Notes

Cette définition de type est un synonyme de **int**.

## <a name="see-also"></a>Voir aussi

[error_category, classe](../standard-library/error-category-class.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
