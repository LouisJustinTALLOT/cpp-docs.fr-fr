---
title: Simpleactivationfactory, classe | Documents Microsoft
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
ms.openlocfilehash: 2d10544a08fa6faebb1434cd00ca80ac30d4570a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889840"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory (classe)
Fournit un mécanisme fondamental pour créer une classe de base Windows Runtime ou une classe de base COM classique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Base>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Base`  
 Classe de base.  
  
## <a name="remarks"></a>Notes  
 La classe de base doit fournir un constructeur par défaut.  
  
 L’exemple de code suivant montre comment utiliser SimpleActivationFactory avec la [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) (macro).  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[SimpleActivationFactory::ActivateInstance, méthode](../windows/simpleactivationfactory-activateinstance-method.md)|Crée une instance de l’interface spécifiée.|  
|[SimpleActivationFactory::GetRuntimeClassName, méthode](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Obtient le nom de classe d’exécution d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.|  
|[SimpleActivationFactory::GetTrustLevel, méthode](../windows/simpleactivationfactory-gettrustlevel-method.md)|Obtient le niveau de confiance d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.|  
  
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)