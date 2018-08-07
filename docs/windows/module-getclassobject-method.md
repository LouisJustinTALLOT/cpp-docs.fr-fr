---
title: Module::GetClassObject, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63ff6c63702cda709f4431d9c7e5be5a4bdb8449
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602651"
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject, méthode
Récupère un cache des fabriques de classes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 HRESULT GetClassObject(  
   REFCLSID clsid,  
   REFIID riid,  
   _Deref_out_ void **ppv,  
   wchar_t* serverName = nullptr  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *clsid*  
 ID de classe.  
  
 *riid*  
 ID d’interface que vous demandez.  
  
 *PPV*  
 Pointeur vers l’objet retourné.  
  
 *Nom du serveur*  
 Le nom du serveur qui est spécifié dans le `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, ou `ActivatableClass` macro ; ou **nullptr** pour obtenir le nom du serveur par défaut.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement pour COM, pas l’exécution de Windows. Cette méthode expose uniquement `IClassFactory` méthodes.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)