---
title: Classe de valeur Platform::IntPtr
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
ms.openlocfilehash: 8101fa2c82a0ac3e3b573384d14d9a7eff6ecf61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152734"
---
# <a name="platformintptr-value-class"></a>Classe de valeur Platform::IntPtr

Représente un pointeur ou un handle signé dont la taille est propre à la plateforme (32 bits ou 64 bits).

## <a name="syntax"></a>Syntaxe

```cpp
public value struct IntPtr
```

### <a name="members"></a>Membres

IntPtr a les membres suivants :

|Membre|Description|
|------------|-----------------|
|[IntPtr::IntPtr](#ctor)|Initialise une nouvelle instance d'IntPtr.|
|[IntPtr::op_explicit, opérateur](#op-explicit)|Convertit le paramètre spécifié en un IntPtr ou un pointeur en une valeur IntPtr.|
|[IntPtr::ToInt32](#toint32)|Convertit l'IntPtr actif en un entier 32 bits.|

### <a name="requirements"></a>Configuration requise

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd

## <a name="ctor"> </a> IntPtr::IntPtr (constructeur)

Initialise une nouvelle instance d'IntPtr avec la valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Handle ou pointeur 64 bits ou pointeur vers une valeur 64 bits, ou valeur 32 bits qui peut être convertie en valeur 64 bits.

## <a name="op-explicit"> </a> IntPtr::op_explicit, opérateur

Convertit le paramètre spécifié en un IntPtr ou un pointeur en une valeur IntPtr.

### <a name="syntax"></a>Syntaxe

```cpp
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );
```

### <a name="parameters"></a>Paramètres

*value1*<br/>
Pointeur vers un handle ou un IntPtr.

*value2*<br/>
Entier 32 bits qui peut être converti en IntPtr.

*value3*<br/>
Un IntPtr.

### <a name="return-value"></a>Valeur de retour

Le premier et le deuxième opérateur retournent un IntPtr. Le troisième opérateur retourne un pointeur vers la valeur représentée par l'IntPtr actuel.

## <a name="toint32"> </a> IntPtr::ToInt32 (méthode)

Convertit la valeur IntPtr actuelle en un entier 32 bits.

### <a name="syntax"></a>Syntaxe

```cpp
int32 IntPtr::ToInt32();
```

### <a name="return-value"></a>Valeur de retour

Entier 32 bits.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)
