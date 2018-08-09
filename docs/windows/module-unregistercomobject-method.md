---
title: Module::unregistercomobject, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 240ab47099b9e97e9a6bb794083858fe042605d2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018693"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject, méthode
Annule l’inscription d’un ou plusieurs objets COM, ce qui empêche les autres applications de se connecter à leur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
### <a name="parameters"></a>Paramètres  
 *Nom du serveur*  
 (Non utilisé)  
  
 *Cookies*  
 Un tableau de pointeurs vers des valeurs qui identifient les objets de classe doit être annulée. Le tableau a été créé par le [RegisterCOMObject](../windows/module-registercomobject-method.md) (méthode).  
  
 *count*  
 Le nombre de classes pour annuler l’inscription.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si cette opération est réussie ; Sinon, une erreur HRESULT qui indique la raison pour laquelle l’opération a échoué.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)