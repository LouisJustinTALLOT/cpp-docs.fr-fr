---
title: Catlautothreadmodulet, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a54818b839f13ad9114274248cfdbfc74efa033a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883071"
---
# <a name="catlautothreadmodulet-class"></a>Catlautothreadmodulet, classe
Cette classe fournit des méthodes pour implémenter un serveur COM mis en pool de thread, le modèle de cloisonnement.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 La classe qui implémente le serveur COM.  
  
 *ThreadAllocator*  
 La classe de la gestion de sélection de thread. La valeur par défaut est [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
 *dwWait*  
 Spécifie l’intervalle de délai d’attente, en millisecondes. La valeur par défaut est INFINITE, ce qui signifie intervalle de délai d’attente de la méthode jamais à expiration.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Cette fonction statique dynamiquement calcule et retourne le nombre maximal de threads pour le module EXE, en fonction du nombre de processeurs.|  
  
## <a name="remarks"></a>Notes  
 La classe [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) dérive `CAtlAutoThreadModuleT` afin d’implémenter un serveur COM mis en pool de thread, le modèle de cloisonnement. Il remplace la classe obsolète [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
> [!NOTE]
>  Cette classe ne doit pas être utilisée dans une DLL, en tant que la valeur par défaut *dwWait* valeur INFINITE entraîne un blocage lors de la DLL est déchargée.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
  
##  <a name="getdefaultthreads"></a>  CAtlAutoThreadModuleT::GetDefaultThreads  
 Cette fonction statique dynamiquement calcule et retourne le nombre maximal de threads pour le module EXE, en fonction du nombre de processeurs.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de threads à créer dans le module EXE.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode si vous souhaitez utiliser une autre méthode pour calculer le nombre de threads. Par défaut, le nombre de threads est basé sur le nombre de processeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Iatlautothreadmodule, classe](../../atl/reference/iatlautothreadmodule-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Iatlautothreadmodule, classe](../../atl/reference/iatlautothreadmodule-class.md)   
 [Classes de module](../../atl/atl-module-classes.md)
