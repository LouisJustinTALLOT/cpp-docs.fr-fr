---
description: En savoir plus sur les macros ActivatableClass
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
ms.openlocfilehash: 2b59101373de72ca88338750bb7fe9169376ac65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287942"
---
# <a name="activatableclass-macros"></a>ActivatableClass, macros

Remplit un cache interne qui contient une fabrique qui peut créer une instance de la classe spécifiée.

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

*ClassName*<br/>
Nom de la classe à créer.

*usine*<br/>
Fabrique qui crée une instance de la classe spécifiée.

*serverName*<br/>
Nom qui spécifie un sous-ensemble de fabriques dans le module.

## <a name="remarks"></a>Notes

N’utilisez pas ces macros avec le COM classique, sauf si vous utilisez la `#undef` directive pour vous assurer que la `__WRL_WINRT_STRICT__` définition de macro est supprimée.

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](module-class.md)
