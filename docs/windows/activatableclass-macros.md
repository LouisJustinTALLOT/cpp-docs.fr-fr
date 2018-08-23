---
title: Activatableclass, Macros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs:
- C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398149d0d65b0dcf4c914d8f35e4c6faf209173f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606985"
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

*nom de classe*  
Nom de la classe à créer.

*fabrique*  
Fabrique qui crée une instance de la classe spécifiée.

*Nom du serveur*  
Nom qui spécifie un sous-ensemble des fabriques de dans le module.

## <a name="remarks"></a>Notes

N’utilisez pas ces macros avec COM classique, sauf si vous utilisez le `#undef` directive pour vous assurer que le `__WRL_WINRT_STRICT__` définition de macro est supprimée.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](../windows/module-class.md)