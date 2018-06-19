---
title: Module::GetClassObject, méthode | Documents Microsoft
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
ms.openlocfilehash: 9205b04fc27e1c6e0e6133a08c3c2f69ffdfc314
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878536"
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
  
#### <a name="parameters"></a>Paramètres  
 `clsid`  
 ID de classe.  
  
 `riid`  
 ID d’interface que vous demandez.  
  
 `ppv`  
 Pointeur vers l’objet retourné.  
  
 `serverName`  
 Le nom du serveur qui est spécifié dans le `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, ou `ActivatableClass` macro ; ou `nullptr` pour obtenir le nom du serveur par défaut.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement pour COM, pas le Windows Runtime. Cette méthode expose uniquement les méthodes IClassFactory.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)