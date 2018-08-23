---
title: Simpleclassfactory, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleClassFactory class
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: deb100cfcbb8d2af14501b8b5cf90569a90c2d4d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600489"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory (classe)

Fournit un mécanisme fondamental pour créer une classe de base.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Paramètres

*base de*  
Une classe de base.

## <a name="remarks"></a>Notes

La classe de base doit fournir un constructeur par défaut.

L’exemple de code suivant montre comment utiliser **SimpleClassFactory** avec la [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) (macro).

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance, méthode](../windows/simpleclassfactory-createinstance-method.md)|Crée une instance de l’interface spécifiée.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)