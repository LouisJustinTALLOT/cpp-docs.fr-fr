---
title: Platform::Box, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 7484bcda3f05a8a9e56a33222d0630d4597e1219
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354759"
---
# <a name="platformbox-class"></a>Platform::Box, classe

Permet à un type valeur comme `Windows::Foundation::DateTime` ou à un type scalaire comme `int` d’être stocké dans un type `Platform::Object` . Vous n’avez généralement pas besoin d’utiliser `Box` explicitement, car le boxing s’effectue implicitement lors de la conversion d’un type valeur en `Object^`.

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
|[opérateur&lt;Box const T&gt;^](#box-const-t) | Permet les conversions par boxing d'une classe value `const``T` ou d'une classe `enum``T` en `Box<T>`. |
|[opérateur&lt;Box const volatile T&gt;^](#box-const-volatile-t) | Permet les conversions par boxing d'une classe value `const volatile``T` ou d'un type `enum``T` en `Box<T>`. |
|[opérateur&lt;Box T&gt;^](#box-t) | Permet les conversions par boxing d'une classe value `T` en `Box<T>`. |
|[opérateur&lt;Box volatile T&gt;^](#box-volatile-t) | Permet les conversions par boxing d'une classe value `volatile``T` ou d'un type `enum``T` en `Box<T>`. |
|[Encadré::opérateur T](#t) | Permet les conversions par boxing d'une classe value `T``enum` ou d'une classe `T` en `Box<T>`. |
|[Propriété de valeur](#value) | Retourne la valeur qui est encapsulée dans l'objet `Box`. |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Boîte::Box Constructor

Crée un `Box` qui peut encapsuler une valeur du type spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Paramètres

*valeurArg*<br/>
Type de la valeur boxed, par exemple `int`, `bool`, `float64`, `DateTime`.

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Boîte::opérateur&lt;Box const T&gt;- Opérateur

Permet les conversions par boxing d'une classe value `const``T` ou d'une classe `enum``T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Toute classe value, tout struct value ou tout type enum. Inclut les types intégrés dans [l’espace nom par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` cas qui représente la valeur originale en boîte dans une classe d’arbitre.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Encadré::opérateur&lt;Box const&gt;volatile T -Opérateur

Permet les conversions par boxing d'une classe value `const volatile``T` ou d'un type `enum``T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Inclut les types intégrés dans [l’espace nom par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` cas qui représente la valeur originale en boîte dans une classe d’arbitre.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Encadré::opérateur&lt;Box&gt;T - Opérateur

Permet les conversions par boxing d'une classe value `T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Inclut les types intégrés dans [l’espace nom par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` cas qui représente la valeur originale en boîte dans une classe d’arbitre.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Encadré::opérateur&lt;Box&gt;volatile T - Opérateur

Permet les conversions par boxing d'une classe value `volatile``T` ou d'un type `enum``T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Inclut les types intégrés dans [l’espace nom par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` cas qui représente la valeur originale en boîte dans une classe d’arbitre.

## <a name="boxoperator-t-operator"></a><a name="t"></a>Encadré::opérateur T Opérateur

Permet les conversions par boxing d'une classe value `T``enum` ou d'une classe `T` en `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Tout type enum, de classe value ou de struct value. Inclut les types intégrés dans [l’espace nom par défaut](../cppcx/default-namespace.md).

### <a name="return-value"></a>Valeur de retour

Un `Platform::Box<T>^` cas qui représente la valeur originale en boîte dans une classe d’arbitre.

## <a name="boxvalue-property"></a><a name="value"></a>Boîte::Valeur Propriété

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

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)<br/>
[Boxing](../cppcx/boxing-c-cx.md)
