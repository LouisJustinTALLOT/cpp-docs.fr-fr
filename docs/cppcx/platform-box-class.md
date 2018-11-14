---
title: Platform::Box, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 29cbe852dcd606ea5cf2953c709fc8e47b89e1f1
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327029"
---
# <a name="platformbox-class"></a>Platform::Box, classe

Permet à un type valeur comme `Windows::Foundation::DateTime` ou à un type scalaire comme `int` d’être stocké dans un type `Platform::Object` . Vous n’avez généralement pas besoin d’utiliser `Box` explicitement, car le boxing s’effectue implicitement lors de la conversion d’un type valeur en `Object^`.

### <a name="syntax"></a>Syntaxe

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Configuration requise

**En-tête :** vccorlib.h

**Espace de noms :** Platform

### <a name="members"></a>Membres

|Membre|Description|
|------------|-----------------|
|[Box](#ctor) | Crée un `Box` qui peut encapsuler une valeur du type spécifié. |
|[opérateur boîte&lt;const T&gt;^](#box-const-t) | Permet les conversions par boxing d'une classe value `const` `T` ou d'une classe `enum` `T` en `Box<T>`. |
|[opérateur boîte&lt;const volatile T&gt;^](#box-const-volatile-t) | Permet les conversions par boxing d'une classe value `const volatile` `T` ou d'un type `enum` `T` en `Box<T>`. |
|[opérateur boîte&lt;T&gt;^](#box-t) | Permet les conversions par boxing d'une classe value `T` en `Box<T>`. |
|[opérateur boîte&lt;volatile T&gt;^](#box-volatile-t) | Permet les conversions par boxing d'une classe value `volatile` `T` ou d'un type `enum` `T` en `Box<T>`. |
|[Box::operator T](#t) | Permet les conversions par boxing d'une classe value `T` `enum` ou d'une classe `T` en `Box<T>`. |
|[Valeur de propriété](#value) | Retourne la valeur qui est encapsulée dans l'objet `Box`. |

## <a name="ctor"></a> Box::Box, constructeur

Crée un `Box` qui peut encapsuler une valeur du type spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Paramètres

*valueArg*<br/>
Type de la valeur boxed, par exemple `int`, `bool`, `float64`, `DateTime`.

## <a name="box-const-t"></a> Box::operator Box&lt;const T&gt;^ opérateur

Permet les conversions par boxing d'une classe value `const` `T` ou d'une classe `enum` `T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Toute classe value, tout struct value ou tout type enum. Inclut les types intégrés dans le [par défaut d’espace de noms](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` converti (boxed) d’instance qui représente la valeur d’origine dans une classe ref.

## <a name="box-const-volatile-t"></a> Box::operator Box&lt;const volatile T&gt;^ opérateur

Permet les conversions par boxing d'une classe value `const volatile` `T` ou d'un type `enum` `T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Inclut les types intégrés dans le [par défaut d’espace de noms](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` converti (boxed) d’instance qui représente la valeur d’origine dans une classe ref.

## <a name="box-t"></a> Box::operator Box&lt;T&gt;^ opérateur

Permet les conversions par boxing d'une classe value `T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Inclut les types intégrés dans le [par défaut d’espace de noms](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` converti (boxed) d’instance qui représente la valeur d’origine dans une classe ref.

## <a name="box-volatile-t"></a> Box::operator Box&lt;volatile T&gt;^ opérateur

Permet les conversions par boxing d'une classe value `volatile` `T` ou d'un type `enum` `T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Inclut les types intégrés dans le [par défaut d’espace de noms](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` converti (boxed) d’instance qui représente la valeur d’origine dans une classe ref.

## <a name="t"></a>  Box::operator T, opérateur

Permet les conversions par boxing d'une classe value `T` `enum` ou d'une classe `T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Inclut les types intégrés dans le [par défaut d’espace de noms](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` converti (boxed) d’instance qui représente la valeur d’origine dans une classe ref.

## <a name="value"></a> Box::value, propriété

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
[Conversion boxing](../cppcx/boxing-c-cx.md)