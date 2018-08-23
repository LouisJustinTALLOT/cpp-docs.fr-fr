---
title: Simpleactivationfactory, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0820012c8c22de1287fcb09037212b870a4ff7bf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594796"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory (classe)

Fournit un mécanisme fondamental pour créer une classe de base Windows Runtime ou une classe de base COM classique.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Paramètres

*base de*  
Une classe de base.

## <a name="remarks"></a>Notes

La classe de base doit fournir un constructeur par défaut.

L’exemple de code suivant montre comment utiliser SimpleActivationFactory avec la [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) (macro).

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance, méthode](../windows/simpleactivationfactory-activateinstance-method.md)|Crée une instance de l’interface spécifiée.|
|[SimpleActivationFactory::GetRuntimeClassName, méthode](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Obtient le nom de classe d’exécution d’une instance de la classe spécifiée par le *Base* paramètre de modèle de classe.|
|[SimpleActivationFactory::GetTrustLevel, méthode](../windows/simpleactivationfactory-gettrustlevel-method.md)|Obtient le niveau de confiance d’une instance de la classe spécifiée par le *Base* paramètre de modèle de classe.|

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

`ActivationFactory`

`SimpleActivationFactory`

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)