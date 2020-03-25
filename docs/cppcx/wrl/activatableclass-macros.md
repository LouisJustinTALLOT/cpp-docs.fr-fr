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
ms.openlocfilehash: 7bc3d789d6c0d304aa170d59dff23a97a67061d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214266"
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

*NomClasse*<br/>
Nom de la classe à créer.

*fabrique*<br/>
Fabrique qui crée une instance de la classe spécifiée.

*serverName*<br/>
Nom qui spécifie un sous-ensemble de fabriques dans le module.

## <a name="remarks"></a>Notes

N’utilisez pas ces macros avec le COM classique, sauf si vous utilisez la directive `#undef` pour vous assurer que la définition de la macro `__WRL_WINRT_STRICT__` est supprimée.

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](module-class.md)
