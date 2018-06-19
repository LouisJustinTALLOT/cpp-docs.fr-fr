---
title: Module::registerwinrtobject, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 097bf70ebd280d9494ff70ea1d80f53615f3d898
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874952"
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject, méthode
Inscrit un ou plusieurs objets Windows Runtime pour d’autres applications peuvent s’y connecter.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `serverName`  
 Nom qui spécifie un sous-ensemble des objets affectés par cette opération.  
  
 `activatableClassIds`  
 Tableau de CLSID activables à inscrire.  
  
 `cookie`  
 Une valeur qui identifie les objets de classe qui ont été enregistrés. Cette valeur est utilisée ultérieurement pour révoquer l’inscription.  
  
 `count`  
 Le nombre d’objets à inscrire.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, une erreur HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)