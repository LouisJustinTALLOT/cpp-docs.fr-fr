---
title: Terminatemap, fonction | Microsoft Docs
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
ms.openlocfilehash: de57e03b1e3a150ab96cb72996b48200b153de1c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016705"
---
# <a name="terminatemap-function"></a>TerminateMap, fonction
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
### <a name="parameters"></a>Paramètres  
 *module*  
 Un [module](../windows/module-class.md).  
  
 *Nom du serveur*  
 Le nom d’un sous-ensemble des fabriques de classes dans le module spécifié par le paramètre *module*.  
  
 *forceTerminate*  
 **true** pour mettre fin à la classe fabriques, quel que soit ils sont actifs ; **false** à se termine ne pas les fabriques de classe si n’importe quel factory est active.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si toutes les fabriques de classe ont été terminées ; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Arrête les fabriques de classe dans le module spécifié.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)