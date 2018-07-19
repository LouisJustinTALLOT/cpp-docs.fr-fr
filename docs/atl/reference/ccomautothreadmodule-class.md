---
title: La classe CComAutoThreadModule | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
dev_langs:
- C++
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbef36927598eb0c91185a02030a1c47d4418079
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880035"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule (classe)
À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class ThreadAllocator = CComSimpleThreadAllocator>  
class CComAutoThreadModule : public CComModule
```  
  
#### <a name="parameters"></a>Paramètres  
 `ThreadAllocator`  
 [in] La classe de la gestion de sélection de thread. La valeur par défaut est [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CreateInstance](#createinstance)|Sélectionne un thread, puis crée un objet dans le compartiment associé.|  
|[GetDefaultThreads](#getdefaultthreads)|(Statique) Calcule dynamiquement le nombre de threads pour le module en fonction du nombre de processeurs.|  
|[Init](#init)|Crée les threads du module.|  
|[Verrou](#lock)|Incrémente le nombre de verrous sur le module et sur le thread actuel.|  
|[Déverrouiller](#unlock)|Décrémente le nombre de verrous sur le module et sur le thread actuel.|  
  
### <a name="data-members"></a>Membres de données  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[dwThreadID](#dwthreadid)|Contient l’identificateur du thread actuel.|  
|[m_Allocator](#m_allocator)|Gère la sélection de thread.|  
|[m_nThreads](#m_nthreads)|Contient le nombre de threads dans le module.|  
|[m_pApartments](#m_papartments)|Gère les cloisonnements de module.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette classe est obsolète, ayant été remplacé par le [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) et [CAtlModule](../../atl/reference/catlmodule-class.md) classes dérivées. Les informations ci-dessous doit être utilisé avec les versions plus anciennes d’ATL.  
  
 `CComAutoThreadModule` dérive de [CComModule](../../atl/reference/ccommodule-class.md) pour implémenter un serveur COM mis en pool de thread, le modèle de cloisonnement pour les services de fichiers exe et Windows. `CComAutoThreadModule` utilise [CComApartment](../../atl/reference/ccomapartment-class.md) pour gérer un cloisonnement pour chaque thread dans le module.  
  
 Dériver votre module à partir de `CComAutoThreadModule` lorsque vous souhaitez créer des objets dans des cloisonnements plusieurs. Vous devez également inclure le [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) macro dans la définition de classe de votre objet pour spécifier [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) car la fabrique de classe.  
  
 Par défaut, l’outil ATL COM AppWizard (l’Assistant de projet ATL dans Visual Studio .NET) dérivera votre module à partir de `CComModule`. Pour utiliser `CComAutoThreadModule`, modifiez la définition de classe. Exemple :  
  
 [!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `IAtlAutoThreadModule`  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 [CComModule](../../atl/reference/ccommodule-class.md)  
  
 `CComAutoThreadModule`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
  
##  <a name="createinstance"></a>  CComAutoThreadModule::CreateInstance  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>Paramètres  
 *pfnCreateInstance*  
 [in] Pointeur vers une fonction de créateur.  
  
 *riid*  
 [in] IID de l’interface demandée.  
  
 *ppvObj*  
 [out] Un pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* est définie sur NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Sélectionne un thread, puis crée un objet dans le compartiment associé.  
  
##  <a name="dwthreadid"></a>  CComAutoThreadModule::dwThreadID  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
DWORD dwThreadID;
```  
  
### <a name="remarks"></a>Notes  
 Contient l’identificateur du thread actuel.  
  
##  <a name="getdefaultthreads"></a>  CComAutoThreadModule::GetDefaultThreads  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de threads à créer dans le module EXE.  
  
### <a name="remarks"></a>Notes  
 Cette fonction statique calcule dynamiquement le nombre maximal de threads pour le module EXE, en fonction du nombre de processeurs. Par défaut, cette valeur de retour est passée à la [Init](#init) méthode pour créer les threads.  
  
##  <a name="init"></a>  CComAutoThreadModule::Init  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```  
  
### <a name="parameters"></a>Paramètres  
 *p*  
 [in] Pointeur vers un tableau d’entrées de mappage d’objet.  
  
 *h*  
 [in] HINSTANCE passé à `DLLMain` ou `WinMain`.  
  
 *plibid*  
 [in] Pointeur vers le LIBID de la bibliothèque de types associé au projet.  
  
 *nThreads*  
 [in] Le nombre de threads doit être créé. Par défaut, *nThreads* est la valeur retournée par [GetDefaultThreads](#getdefaultthreads).  
  
### <a name="remarks"></a>Notes  
 Initialise les membres de données et crée le nombre de threads spécifié par *nThreads*.  
  
##  <a name="lock"></a>  CComAutoThreadModule::Lock  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut-être être utiles pour le diagnostic ou de test.  
  
### <a name="remarks"></a>Notes  
 Effectue un incrément atomique sur le nombre de verrous pour le module et pour le thread actuel. `CComAutoThreadModule` utilise le nombre de verrous du module pour déterminer si tous les clients accèdent à du module. Le nombre de verrous sur le thread actuel est utilisé à des fins statistiques.  
  
##  <a name="m_allocator"></a>  CComAutoThreadModule::m_Allocator  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
ThreadAllocator  m_Allocator;
```     
  
### <a name="remarks"></a>Notes  
 L’objet de gestion de sélection de thread. Par défaut, le `ThreadAllocator` paramètre de modèle de classe [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
##  <a name="m_nthreads"></a>  CComAutoThreadModule::m_nThreads  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
int m_nThreads;
```  
  
### <a name="remarks"></a>Notes  
 Contient le nombre de threads dans le module EXE. Lorsque [Init](#init) est appelée, `m_nThreads` est défini sur le *nThreads* valeur du paramètre. Cloisonnement associé de chaque thread est géré par un [CComApartment](../../atl/reference/ccomapartment-class.md) objet.  
  
##  <a name="m_papartments"></a>  CComAutoThreadModule::m_pApartments  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
CComApartment* m_pApartments;
```  
  
### <a name="remarks"></a>Notes  
 Pointe vers un tableau de [CComApartment](../../atl/reference/ccomapartment-class.md) objets, chacun d’eux gère un cloisonnement dans le module. Le nombre d’éléments dans le tableau est basé sur le [m_nThreads](#m_nthreads) membre.  
  
##  <a name="unlock"></a>  CComAutoThreadModule::Unlock  
 À compter d’ATL 7.0, `CComAutoThreadModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut-être être utiles pour le diagnostic ou de test.  
  
### <a name="remarks"></a>Notes  
 Effectue une décrémentation atomique sur le nombre de verrous pour le module et pour le thread actuel. `CComAutoThreadModule` utilise le nombre de verrous du module pour déterminer si tous les clients accèdent à du module. Le nombre de verrous sur le thread actuel est utilisé à des fins statistiques.  
  
 Lorsque le nombre de verrous du module atteint zéro, le module peut être déchargé.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Classes de module](../../atl/atl-module-classes.md)
