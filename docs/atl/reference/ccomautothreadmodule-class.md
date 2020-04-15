---
title: Classe CComAutoThreadModule
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: 391354c5672cf15c0286491619a13c6005493cfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321067"
---
# <a name="ccomautothreadmodule-class"></a>Classe CComAutoThreadModule

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Paramètres

*ThreadAllocator (en)*<br/>
[dans] La sélection de thread de gestion de classe. La valeur par défaut est [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CréerInstance](#createinstance)|Sélectionne un thread, puis crée un objet dans l’appartement associé.|
|[GetDefaultThreads](#getdefaultthreads)|(Statique) Calcule dynamiquement le nombre de threads pour le module en fonction du nombre de processeurs.|
|[Init](#init)|Crée les fils du module.|
|[Verrouiller](#lock)|Incréments le compte de verrouillage sur le module et sur le fil actuel.|
|[Déverrouiller](#unlock)|Décroisse le compte de verrouillage sur le module et sur le fil actuel.|

### <a name="data-members"></a>Données membres

### <a name="data-members"></a>Données membres

|||
|-|-|
|[dwThreadID](#dwthreadid)|Contient l’identifiant du thread actuel.|
|[m_Allocator](#m_allocator)|Gère la sélection des threads.|
|[m_nThreads](#m_nthreads)|Contient le nombre de threads dans le module.|
|[m_pApartments](#m_papartments)|Gère les appartements du module.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Cette classe est obsolète, après avoir été remplacée par les classes [dérivées CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) et [CAtlModule.](../../atl/reference/catlmodule-class.md) L’information qui suit est pour une utilisation avec les versions plus anciennes de ATL.

`CComAutoThreadModule`dérive de [CComModule](../../atl/reference/ccommodule-class.md) pour implémenter un serveur COM de type appartement pooled pour les EXEs et les services Windows. `CComAutoThreadModule`utilise [CComApartment](../../atl/reference/ccomapartment-class.md) pour gérer un appartement pour chaque thread du module.

Dérivez votre `CComAutoThreadModule` module à partir de quand vous voulez créer des objets dans plusieurs appartements. Vous devez également inclure la macro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) dans la définition de classe de votre objet pour spécifier [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) comme usine de classe.

Par défaut, l’APPWizard ATL COM (l’ATL Project Wizard dans `CComModule`Visual Studio .NET) tirera votre module de . Pour `CComAutoThreadModule`utiliser, modifier la définition de la classe. Par exemple :

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThreadModule::CréerInstance

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*pfnCreateInstance*<br/>
[dans] Un pointeur pour une fonction de créateur.

*riid*<br/>
[dans] L’IID de l’interface demandée.

*ppvObj*<br/>
[out] Un pointeur au pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Sélectionne un thread, puis crée un objet dans l’appartement associé.

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Notes

Contient l’identifiant du thread actuel.

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de threads à créer dans le module EXE.

### <a name="remarks"></a>Notes

Cette fonction statique calcule dynamiquement le nombre maximum de threads pour le module EXE, en fonction du nombre de processeurs. Par défaut, cette valeur de retour est transmise à la méthode [Init](#init) pour créer les threads.

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThreadModule::Init

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Un pointeur à un tableau d’entrées de carte d’objet.

*h*<br/>
[dans] Le HINSTANCE `DLLMain` est `WinMain`passé à ou .

*plibid*<br/>
[dans] Un pointeur pour le LIBID de la bibliothèque de type associée au projet.

*nThreads*<br/>
[dans] Le nombre de threads à créer. Par défaut, *nThreads* est la valeur retournée par [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Notes

Initialise les membres des données et crée le nombre de threads spécifiés par *nThreads*.

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThreadModule::Lock

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
LONG Lock();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic ou les tests.

### <a name="remarks"></a>Notes

Effectue une incrément atomique sur le compte de verrouillage pour le module et pour le thread actuel. `CComAutoThreadModule`utilise le compte de verrouillage du module pour déterminer si des clients accèdent au module. Le compte de verrouillage sur le thread actuel est utilisé à des fins statistiques.

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a>CComAutoThreadModule::m_Allocator

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Notes

L’objet de gestion de la sélection des fils. Par défaut, `ThreadAllocator` le paramètre du modèle de classe est [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
int m_nThreads;
```

### <a name="remarks"></a>Notes

Contient le nombre de threads dans le module EXE. Lorsque [Init](#init) est `m_nThreads` appelé, est réglé à la valeur de paramètres *nThreads.* L’appartement associé de chaque thread est géré par un objet [CComApartment.](../../atl/reference/ccomapartment-class.md)

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a>CComAutoThreadModule::m_pApartments

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Notes

Points à une gamme d’objets [CComApartment,](../../atl/reference/ccomapartment-class.md) dont chacun gère un appartement dans le module. Le nombre d’éléments dans le tableau est basé sur le [m_nThreads](#m_nthreads) membre.

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThreadModule::Unlock

En date de ATL 7.0, `CComAutoThreadModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
LONG Unlock();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic ou les tests.

### <a name="remarks"></a>Notes

Effectue une décroissation atomique sur le nombre de verrouillage pour le module et pour le thread actuel. `CComAutoThreadModule`utilise le compte de verrouillage du module pour déterminer si des clients accèdent au module. Le compte de verrouillage sur le thread actuel est utilisé à des fins statistiques.

Lorsque le nombre de verrous du module atteint zéro, le module peut être déchargé.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de modules](../../atl/atl-module-classes.md)
