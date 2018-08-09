---
title: ClassFactory, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
dev_langs:
- C++
helpviewer_keywords:
- ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9a7caba7ccfb8f5764a1f460835ff540c838975
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641039"
---
# <a name="classfactory-class"></a>ClassFactory (classe)
Implémente les fonctionnalités de base de l'interface `IClassFactory`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ClassFactory : public Details::RuntimeClass<  
   typename Details::InterfaceListHelper<IClassFactory,   
   I0,   
   I1,   
   I2,   
   Details::Nil>::TypeT,   
   RuntimeClassFlags<ClassicCom | InhibitWeakReference>,   
      false>;  
```  
  
### <a name="parameters"></a>Paramètres  
 *I0*  
 L’interface de zéro.  
  
 *I1*  
 La première interface.  
  
 *I2*  
 La seconde interface.  
  
## <a name="remarks"></a>Notes  
 Utiliser **ClassFactory** pour fournir une implémentation de fabrique défini par l’utilisateur.  
  
 Le modèle de programmation suivant montre comment utiliser le [implémente](../windows/implements-structure.md) structure pour spécifier plus de trois interfaces sur une fabrique de classe.  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ClassFactory::ClassFactory, constructeur](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ClassFactory::AddRef, méthode](../windows/classfactory-addref-method.md)|Incrémente le décompte de références pour actuel **ClassFactory** objet.|  
|[ClassFactory::LockServer, méthode](../windows/classfactory-lockserver-method.md)|Incrémente ou décrémente le nombre de sous-jacent objets qui sont suivis par le **ClassFactory** objet.|  
|[ClassFactory::QueryInterface, méthode](../windows/classfactory-queryinterface-method.md)|Récupère un pointeur vers l’interface spécifiée par le paramètre.|  
|[ClassFactory::Release, méthode](../windows/classfactory-release-method.md)|Décrémente le décompte de références pour actuel **ClassFactory** objet.|  
  
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
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType, énumération](../windows/runtimeclasstype-enumeration.md)