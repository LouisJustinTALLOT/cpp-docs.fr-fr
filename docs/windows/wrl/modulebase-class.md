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
ms.openlocfilehash: 254796c03d25a77da22c48881c086a41ffbfeb82
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335987"
---
# <a name="modulebase-class"></a>ModuleBase, classe

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Notes

Représente la classe de base de la [Module](module-class.md) classes.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                         | Description
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase::ModuleBase](#modulebase)        | Initialise une instance de la classe `Module`.
[ModuleBase :: ~ ModuleBase](#tilde-modulebase) | Annule l’initialisation de l’instance actuelle de la `Module` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                      | Description
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModuleBase::DecrementObjectCount](#decrementobjectcount) | En cas d’implémentation, décrémente le nombre d’objets suivis par le module.
[ModuleBase::IncrementObjectCount](#incrementobjectcount) | En cas d’implémentation, incrémente le nombre d’objets suivis par le module.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ModuleBase`

## <a name="requirements"></a>Spécifications

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="tilde-modulebase"></a>ModuleBase::~ModuleBase

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Notes

Annule l’initialisation de l’instance actuelle de la `ModuleBase` classe.

## <a name="decrementobjectcount"></a>ModuleBase::DecrementObjectCount

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Valeur de retour

Le nombre avant l’opération de décrémentation.

### <a name="remarks"></a>Notes

En cas d’implémentation, décrémente le nombre d’objets suivis par le module.

## <a name="incrementobjectcount"></a>ModuleBase::IncrementObjectCount

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Valeur de retour

Le nombre avant l’opération d’incrémentation.

### <a name="remarks"></a>Notes

En cas d’implémentation, incrémente le nombre d’objets suivis par le module.

## <a name="modulebase"></a>ModuleBase::ModuleBase

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Notes

Initialise une instance de la classe `Module`.