---
title: CComAutoThreadModule, classe
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
ms.openlocfilehash: 405b05548cda2b2d379b849d9278293b8d747d2e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833788"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule, classe

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Paramètres

*ThreadAllocator*<br/>
dans Classe qui gère la sélection des threads. La valeur par défaut est [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Fonction|Description|
|-|-|
|[CreateInstance](#createinstance)|Sélectionne un thread, puis crée un objet dans le cloisonnement associé.|
|[GetDefaultThreads](#getdefaultthreads)|Statique Calcule dynamiquement le nombre de threads pour le module en fonction du nombre de processeurs.|
|[Init](#init)|Crée les threads du module.|
|[Verrouiller](#lock)|Incrémente le nombre de verrous sur le module et sur le thread actuel.|
|[Bloquer](#unlock)|Décrémente le nombre de verrous sur le module et sur le thread actuel.|

### <a name="data-members"></a>Données membres

|Membre de données|Description|
|-|-|
|[dwThreadID](#dwthreadid)|Contient l’identificateur du thread actuel.|
|[m_Allocator](#m_allocator)|Gère la sélection des threads.|
|[m_nThreads](#m_nthreads)|Contient le nombre de threads dans le module.|
|[m_pApartments](#m_papartments)|Gère les cloisonnements du module.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Cette classe est obsolète et a été remplacée par les classes dérivées [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) et [CAtlModule](../../atl/reference/catlmodule-class.md) . Les informations suivantes sont destinées à être utilisées avec les versions antérieures d’ATL.

`CComAutoThreadModule` dérive de [CComModule](../../atl/reference/ccommodule-class.md) pour implémenter un serveur com à pool de threads et de modèle Apartment pour les fichiers exe et Windows. `CComAutoThreadModule` utilise [CComApartment](../../atl/reference/ccomapartment-class.md) pour gérer un cloisonnement pour chaque thread dans le module.

Dérivez votre module de `CComAutoThreadModule` lorsque vous souhaitez créer des objets dans plusieurs cloisons. Vous devez également inclure la macro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) dans la définition de classe de votre objet pour spécifier [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) comme fabrique de classe.

Par défaut, ATL COM AppWizard (l’Assistant Projet ATL dans Visual Studio .NET) dérivera votre module de `CComModule` . Pour utiliser `CComAutoThreadModule` , modifiez la définition de classe. Par exemple :

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

**En-tête :** atlbase. h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a> CComAutoThreadModule :: CreateInstance

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*pfnCreateInstance*<br/>
dans Pointeur vers une fonction Creator.

*riid*<br/>
dans IID de l’interface demandée.

*ppvObj*<br/>
à Pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Sélectionne un thread, puis crée un objet dans le cloisonnement associé.

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a> CComAutoThreadModule ::d wThreadID

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Notes

Contient l’identificateur du thread actuel.

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a> CComAutoThreadModule :: GetDefaultThreads

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de threads à créer dans le module EXE.

### <a name="remarks"></a>Notes

Cette fonction statique calcule dynamiquement le nombre maximal de threads pour le module EXE, en fonction du nombre de processeurs. Par défaut, cette valeur de retour est passée à la méthode [init](#init) pour créer les threads.

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a> CComAutoThreadModule :: init

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers un tableau d’entrées de mappage d’objets.

*h*<br/>
dans HINSTANCE passé à `DLLMain` ou `WinMain` .

*plibid*<br/>
dans Pointeur vers le LIBID de la bibliothèque de types associée au projet.

*nThreads*<br/>
dans Nombre de threads à créer. Par défaut, *nThreads* est la valeur retournée par [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Notes

Initialise des membres de données et crée le nombre de threads spécifié par *nThreads*.

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a> CComAutoThreadModule :: Lock

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
LONG Lock();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui peut être utile pour les diagnostics ou les tests.

### <a name="remarks"></a>Notes

Effectue un incrément atomique sur le nombre de verrous du module et du thread en cours. `CComAutoThreadModule` utilise le nombre de verrous de module pour déterminer si des clients accèdent au module. Le nombre de verrous sur le thread actuel est utilisé à des fins statistiques.

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a> CComAutoThreadModule :: m_Allocator

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Notes

Objet gérant la sélection des threads. Par défaut, le `ThreadAllocator` paramètre de modèle de classe est [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a> CComAutoThreadModule :: m_nThreads

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
int m_nThreads;
```

### <a name="remarks"></a>Notes

Contient le nombre de threads dans le module EXE. Lorsque [init](#init) est appelé, `m_nThreads` la valeur du paramètre *nThreads* est définie. Le cloisonnement associé à chaque thread est géré par un objet [CComApartment](../../atl/reference/ccomapartment-class.md) .

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a> CComAutoThreadModule :: m_pApartments

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Notes

Pointe vers un tableau d’objets [CComApartment](../../atl/reference/ccomapartment-class.md) , chacun d’eux gérant un cloisonnement dans le module. Le nombre d’éléments dans le tableau est basé sur le membre [m_nThreads](#m_nthreads) .

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a> CComAutoThreadModule :: Unlock

À partir de ATL 7,0, `CComAutoThreadModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
LONG Unlock();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui peut être utile pour les diagnostics ou les tests.

### <a name="remarks"></a>Notes

Effectue une décrémentation atomique sur le nombre de verrous du module et du thread en cours. `CComAutoThreadModule` utilise le nombre de verrous de module pour déterminer si des clients accèdent au module. Le nombre de verrous sur le thread actuel est utilisé à des fins statistiques.

Lorsque le nombre de verrous de module atteint zéro, le module peut être déchargé.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
