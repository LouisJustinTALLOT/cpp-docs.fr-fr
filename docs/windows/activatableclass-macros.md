---
title: ActivatableClass, macros
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: 1b50d9ba59ef8aebe4eca388ee30449f4ddd53de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660666"
---
# <a name="activatableclass-macros"></a>ActivatableClass, macros

Remplit un cache interne qui contient une fabrique pouvant créer une instance de la classe spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>Paramètres

*nom de classe*<br/>
Nom de la classe à créer.

*fabrique*<br/>
Fabrique qui crée une instance de la classe spécifiée.

*Nom du serveur*<br/>
Nom qui spécifie un sous-ensemble des fabriques de dans le module.

## <a name="remarks"></a>Notes

N’utilisez pas ces macros avec COM classique, sauf si vous utilisez le `#undef` directive pour vous assurer que le `__WRL_WINRT_STRICT__` définition de macro est supprimée.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](../windows/module-class.md)