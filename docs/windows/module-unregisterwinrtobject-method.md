---
title: Module::unregisterwinrtobject, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterWinRTObject method
ms.assetid: 32334aa7-2293-40d2-9a89-4b02e2e31f3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5bf681acc485b08448fcb4e936ca1096a8137384
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607470"
---
# <a name="moduleunregisterwinrtobject-method"></a>Module::UnregisterWinRTObject, méthode
Annule l’inscription d’un ou plusieurs objets Windows Runtime afin que les autres applications ne peuvent pas s’y connecter.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual HRESULT UnregisterWinRTObject(  
   unsigned int,  
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Cookie*  
 Pointeur vers une valeur qui identifie l’objet de classe dont l’inscription doit être révoqué.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)