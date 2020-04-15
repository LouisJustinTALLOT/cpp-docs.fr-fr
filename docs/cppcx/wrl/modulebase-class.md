---
title: ModuleBase, classe
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 13a8ceef3133e9946524e1fcd02e96535eccd7fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371270"
---
# <a name="modulebase-class"></a>ModuleBase, classe

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Notes

Représente la classe de base des classes [module.](module-class.md)

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                         | Description
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase::ModuleBase](#modulebase)        | Initialise une instance de la classe `Module`.
[ModuleBase::ModuleBase](#tilde-modulebase) | Désinitialise l’instance actuelle `Module` de la classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                      | Description
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModuleBase::DecrementObjectCount](#decrementobjectcount) | Une fois mis en œuvre, décrète le nombre d’objets suivis par le module.
[ModuleBase::IncrementObjectCount](#incrementobjectcount) | Une fois mis en œuvre, incréments le nombre d’objets suivis par le module.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ModuleBase`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace nom:** Microsoft::WRL::Details

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a>ModuleBase::ModuleBase

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Notes

Désinitialise l’instance actuelle `ModuleBase` de la classe.

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a>ModuleBase::DecrementObjectCount

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Valeur de retour

Le compte avant l’opération de décroissement.

### <a name="remarks"></a>Notes

Une fois mis en œuvre, décrète le nombre d’objets suivis par le module.

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a>ModuleBase::IncrementObjectCount

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Valeur de retour

Le compte avant l’opération d’incrément.

### <a name="remarks"></a>Notes

Une fois mis en œuvre, incréments le nombre d’objets suivis par le module.

## <a name="modulebasemodulebase"></a><a name="modulebase"></a>ModuleBase::ModuleBase

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Notes

Initialise une instance de la classe `Module`.
