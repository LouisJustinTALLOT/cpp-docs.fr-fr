---
title: Les fonctions globales WinModule | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs: C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 290566c27fa5698c4a00a323a8c2431681b69d88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="winmodule-global-functions"></a>Fonctions globales WinModule
Ces fonctions fournissent la prise en charge de `_AtlCreateWndData` les opérations de la structure.  
  
> [!IMPORTANT]
>  Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Cette fonction est utilisée pour initialiser et ajouter une structure `_AtlCreateWndData`.|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Appelez cette fonction pour extraire une structure `_AtlCreateWndData` existante.|  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
  `            
##  <a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData  
 Cette fonction est utilisée pour initialiser et ajouter une structure `_AtlCreateWndData`.  
   
```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWinModule`  
 Pointeur vers un module [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) structure.  
  
 `pData`  
 Pointeur vers le [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) structure devant être initialisé et ajoutées au module actuel.  
  
 `pObject`  
 Pointeur vers un objet **cela** pointeur.  
  
### <a name="remarks"></a>Notes  
 Initialise une `_AtlCreateWndData` structure, qui est utilisé pour stocker le **cela** pointeur utilisé pour faire référence à des instances de classe et l’ajoute à la liste référencée par un module `_ATL_WIN_MODULE70` structure. Appelé par [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData  
 Appelez cette fonction pour extraire une structure `_AtlCreateWndData` existante.  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWinModule`  
 Pointeur vers un module [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) structure.  
  
### <a name="remarks"></a>Notes  
 Cette fonction extrait existant `_AtlCreateWndData` structure à partir de la liste référencée par un module `_ATL_WIN_MODULE70` structure.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../atl/reference/atl-functions.md)
