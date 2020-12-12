---
description: 'En savoir plus sur : classe ModuleBase'
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
ms.openlocfilehash: 6540068cee62da5d1a9039a15bcb5bd53ff3aea2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186244"
---
# <a name="modulebase-class"></a>ModuleBase, classe

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Notes

Représente la classe de base des classes de [module](module-class.md) .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                         | Description
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase :: ModuleBase](#modulebase)        | Initialise une instance de la classe `Module`.
[ModuleBase :: ~ ModuleBase](#tilde-modulebase) | Désinitialise l’instance actuelle de la `Module` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                      | Description
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModuleBase ::D ecrementObjectCount](#decrementobjectcount) | En cas d’implémentation, décrémente le nombre d’objets suivis par le module.
[ModuleBase :: Incrementobjectcount,](#incrementobjectcount) | En cas d’implémentation, incrémente le nombre d’objets suivis par le module.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ModuleBase`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a> ModuleBase :: ~ ModuleBase

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Notes

Désinitialise l’instance actuelle de la `ModuleBase` classe.

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a> ModuleBase ::D ecrementObjectCount

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre avant l’opération de décrémentation.

### <a name="remarks"></a>Notes

En cas d’implémentation, décrémente le nombre d’objets suivis par le module.

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a> ModuleBase :: Incrementobjectcount,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre avant l’opération d’incrémentation.

### <a name="remarks"></a>Notes

En cas d’implémentation, incrémente le nombre d’objets suivis par le module.

## <a name="modulebasemodulebase"></a><a name="modulebase"></a> ModuleBase :: ModuleBase

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Notes

Initialise une instance de la classe `Module`.
