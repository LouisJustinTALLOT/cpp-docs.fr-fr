---
description: 'En savoir plus sur : classe Platform :: Box'
title: Platform::Box, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: cbfe8ec70f2ef4c58bf2c9459f2d0c4722817810
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284055"
---
# <a name="platformbox-class"></a>Platform::Box, classe

Permet à un type valeur tel que `Windows::Foundation::DateTime` ou un type scalaire comme **`int`** d’être stocké dans un `Platform::Object` type. Vous n’avez généralement pas besoin d’utiliser `Box` explicitement, car le boxing s’effectue implicitement lors de la conversion d’un type valeur en `Object^`.

### <a name="syntax"></a>Syntaxe

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Spécifications

**En-tête** : vccorlib.h

**Espace de noms :** Platform

### <a name="members"></a>Membres

|Membre|Description|
|------------|-----------------|
|[Box](#ctor) | Crée un `Box` qui peut encapsuler une valeur du type spécifié. |
|[Zone d’opérateur &lt; const T&gt;^](#box-const-t) | Permet les conversions boxing d’une classe **`const`** value `T` ou **`enum`** d’une classe `T` en `Box<T>` . |
|[Zone d’opérateur &lt; const volatile T&gt;^](#box-const-volatile-t) | Permet les conversions boxing d’une **`const volatile`** classe value `T` ou d’un **`enum`** type `T` en `Box<T>` . |
|[Zone d’opérateur &lt; T&gt;^](#box-t) | Permet les conversions par boxing d'une classe value `T` en `Box<T>`. |
|[Zone d’opérateur &lt; volatile T&gt;^](#box-volatile-t) | Permet les conversions boxing d’une **`volatile`** classe value `T` ou d’un **`enum`** type `T` en `Box<T>` . |
|[Box :: Operator T](#t) | Permet les conversions boxing d’une classe value `T` ou **`enum`** d’une classe `T` en `Box<T>` . |
|[Value (propriété)](#value) | Retourne la valeur qui est encapsulée dans l'objet `Box`. |

## <a name="boxbox-constructor"></a><a name="ctor"></a> Box :: Box, constructeur

Crée un `Box` qui peut encapsuler une valeur du type spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Paramètres

*valueArg*<br/>
Type de valeur à convertir (par exemple,,,,) **`int`** **`bool`** `float64` `DateTime` .

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a> Box :: Operator Box, &lt; opérateur const T &gt; ^

Permet les conversions boxing d’une classe **`const`** value `T` ou **`enum`** d’une classe `T` en `Box<T>` .

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Toute classe value, tout struct value ou tout type enum. Comprend les types intégrés dans l’espace de [noms par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur renvoyée

`Platform::Box<T>^`Instance qui représente la valeur d’origine convertie dans une classe ref.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a> Box :: Operator Box, &lt; opérateur volatile T &gt; ^, opérateur

Permet les conversions boxing d’une **`const volatile`** classe value `T` ou d’un **`enum`** type `T` en `Box<T>` .

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Comprend les types intégrés dans l’espace de [noms par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur renvoyée

`Platform::Box<T>^`Instance qui représente la valeur d’origine convertie dans une classe ref.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a> Box :: Operator Box &lt; T &gt; ^, opérateur

Permet les conversions par boxing d'une classe value `T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Comprend les types intégrés dans l’espace de [noms par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur renvoyée

`Platform::Box<T>^`Instance qui représente la valeur d’origine convertie dans une classe ref.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a> Box :: Operator Box, &lt; opérateur T &gt; ^ volatile

Permet les conversions boxing d’une **`volatile`** classe value `T` ou d’un **`enum`** type `T` en `Box<T>` .

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Comprend les types intégrés dans l’espace de [noms par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur renvoyée

`Platform::Box<T>^`Instance qui représente la valeur d’origine convertie dans une classe ref.

## <a name="boxoperator-t-operator"></a><a name="t"></a> Box :: Operator T, opérateur

Permet les conversions boxing d’une classe value `T` ou **`enum`** d’une classe `T` en `Box<T>` .

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Comprend les types intégrés dans l’espace de [noms par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur renvoyée

`Platform::Box<T>^`Instance qui représente la valeur d’origine convertie dans une classe ref.

## <a name="boxvalue-property"></a><a name="value"></a> Box :: value, propriété

Retourne la valeur qui est encapsulée dans l'objet `Box`.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur boxed avec le même type que celui avant la conversion par boxing.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)<br/>
[Boxing](../cppcx/boxing-c-cx.md)
