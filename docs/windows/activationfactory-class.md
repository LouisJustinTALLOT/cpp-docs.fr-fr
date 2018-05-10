---
title: Activationfactory, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6775e9466ed337a070b6a234a4d65bb949a009e4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="activationfactory-class"></a>ActivationFactory (classe)
Permet à une ou plusieurs classes d'être activées par le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `I0`  
 L’interface de zéro.  
  
 `I1`  
 La première interface.  
  
 `I2`  
 La seconde interface.  
  
## <a name="remarks"></a>Notes  
 ActivationFactory fournit les méthodes d’inscription et fonctionnalités de base pour l’interface IActivationFactory. ActivationFactory vous permet également de fournir une implémentation de la fabrique personnalisée.  
  
 Symboliquement, le fragment de code suivant illustre comment utiliser ActivationFactory.  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 Le fragment de code suivant montre comment utiliser le [implémente](../windows/implements-structure.md) structure pour spécifier l’ID d’interface plus de trois.  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory, constructeur](../windows/activationfactory-activationfactory-constructor.md)|Initialise la classe ActivationFactory.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ActivationFactory::AddRef, méthode](../windows/activationfactory-addref-method.md)|Incrémente le décompte de références de l’objet ActivationFactory actuel.|  
|[ActivationFactory::GetIids, méthode](../windows/activationfactory-getiids-method.md)|Récupère un tableau d’ID d’interface implémentée.|  
|[ActivationFactory::GetRuntimeClassName, méthode](../windows/activationfactory-getruntimeclassname-method.md)|Obtient le nom de la classe runtime de l’objet qui instancie la ActivationFactory actuel.|  
|[ActivationFactory::GetTrustLevel, méthode](../windows/activationfactory-gettrustlevel-method.md)|Obtient le niveau de confiance de l’objet qui instancie la ActivationFactory actuel.|  
|[ActivationFactory::QueryInterface, méthode](../windows/activationfactory-queryinterface-method.md)|Récupère un pointeur vers l’interface spécifiée.|  
|[ActivationFactory::Release, méthode](../windows/activationfactory-release-method.md)|Décrémente le décompte de références de l’objet ActivationFactory actuel.|  
  
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)