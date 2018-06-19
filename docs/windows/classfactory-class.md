---
title: ClassFactory, classe | Documents Microsoft
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
ms.openlocfilehash: 6294634652ffc6a53a577ccd75c348ed63c502e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858391"
---
# <a name="classfactory-class"></a>ClassFactory (classe)
Implémente les fonctionnalités de base de l’interface IClassFactory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Paramètres  
 `I0`  
 L’interface de zéro.  
  
 `I1`  
 La première interface.  
  
 `I2`  
 La seconde interface.  
  
## <a name="remarks"></a>Notes  
 Utiliser `ClassFactory` pour fournir une implémentation de paramètres d’usine définie par l’utilisateur.  
  
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
|[ClassFactory::AddRef, méthode](../windows/classfactory-addref-method.md)|Incrémente le décompte de références pour l’objet ClassFactory actuel.|  
|[ClassFactory::LockServer, méthode](../windows/classfactory-lockserver-method.md)|Incrémente ou décrémente le nombre de sous-jacent des objets qui sont suivies par l’objet ClassFactory actuel.|  
|[ClassFactory::QueryInterface, méthode](../windows/classfactory-queryinterface-method.md)|Récupère un pointeur vers l’interface spécifiée par le paramètre.|  
|[ClassFactory::Release, méthode](../windows/classfactory-release-method.md)|Décrémente le décompte de références pour l’objet ClassFactory actuel.|  
  
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType, énumération](../windows/runtimeclasstype-enumeration.md)