---
title: Module::unregisterobjects, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterObjects
dev_langs:
- C++
helpviewer_keywords:
- UnregisterObjects method
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b711338c436eda3e64d9b51ef0d3137975d834a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874117"
---
# <a name="moduleunregisterobjects-method"></a>Module::UnregisterObjects, méthode
Annule l’enregistrement des objets dans le module spécifié afin que les autres applications ne peuvent pas s’y connecter.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UnregisterObjects(  
   ModuleBase* module,  
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `module`  
 Pointeur vers un module.  
  
 `serverName`  
 Nom de qualification qui spécifie un sous-ensemble des objets affectés par cette opération.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si cette opération a réussi ; Sinon, une erreur HRESULT qui indique la raison pour laquelle cette opération a échoué.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)