---
title: TerminateMap (fonction) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
dev_langs:
- C++
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b4787fec0a6b4b9f55c500b66786372945d9a523
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890347"
---
# <a name="terminatemap-function"></a>TerminateMap, fonction
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
## <a name="parameters"></a>Paramètres  
 `module`  
 A [module](../windows/module-class.md).  
  
 `serverName`  
 Le nom d’un sous-ensemble des fabriques de classes dans le module spécifié par le paramètre `module`.  
  
 `forceTerminate`  
 `true` Pour mettre fin à la classe fabriques, quelle que soit leur sont actifs ; `false` ne pas terminer les fabriques de classe si n’importe quel fabrique est active.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si toutes les fabriques de classe ont été arrêtées ; dans le cas contraire, `false`.  
  
## <a name="remarks"></a>Notes  
 Arrête les fabriques de classe dans le module spécifié.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)