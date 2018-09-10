---
title: Classe de valeur Platform::IntPtr | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
dev_langs:
- C++
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0c6f7bc2cdc6b1478aba26c1ce0db48464a9ef2
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104035"
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

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd

## <a name="ctor"> </a> IntPtr::IntPtr (constructeur)

Initialise une nouvelle instance d'IntPtr avec la valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );
```

### <a name="parameters"></a>Paramètres

*valeur*<br/>
Handle ou pointeur 64 bits ou pointeur vers une valeur 64 bits, ou valeur 32 bits qui peut être convertie en valeur 64 bits.

## <a name="op-explicit"> </a> IntPtr::op_explicit, opérateur

Convertit le paramètre spécifié en un IntPtr ou un pointeur en une valeur IntPtr.

### <a name="syntax"></a>Syntaxe

```cpp
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );
```

### <a name="parameters"></a>Paramètres

*Value1*<br/>
Pointeur vers un handle ou un IntPtr.

*Value2*<br/>
Entier 32 bits qui peut être converti en IntPtr.

*valeur3*<br/>
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

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)