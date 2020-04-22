---
title: Classe CThreadPool
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: 5e52868f23883836919b96be9aec1815bc1c17b3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747451"
---
# <a name="cthreadpool-class"></a>Classe CThreadPool

Cette classe fournit un pool de fils de travailleur qui traitent une file d’attente d’éléments de travail.

## <a name="syntax"></a>Syntaxe

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Paramètres

*Travailleur*<br/>
La classe conforme à [l’archétype du travailleur](../../atl/reference/worker-archetype.md) fournissant le code utilisé pour traiter les éléments de travail en file d’attente sur le pool de threads.

*ThreadTraits*<br/>
La classe fournissant la fonction utilisée pour créer les fils dans la piscine.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Le constructeur pour la piscine de fil.|
|[CThreadPool: :CThreadPool](#dtor)|Le destructeur pour le pool de fil.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Implémentation de `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Appelez cette méthode pour obtenir le nombre de threads dans la piscine.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Appelez cette méthode pour obtenir la poignée du port d’achèvement de l’OO utilisé pour faire la queue des articles de travail.|
|[CThreadPool::GetSize](#getsize)|Appelez cette méthode pour obtenir le nombre de threads dans la piscine.|
|[CThreadPool::GetTimeout](#gettimeout)|Appelez cette méthode pour obtenir le temps maximum en millisecondes que le pool de thread attendra pour un thread pour s’éteindre.|
|[CThreadPool::Initialize](#initialize)|Appelez cette méthode pour initialiser le pool de threads.|
|[CThreadPool::QueryInterface](#queryinterface)|Implémentation de `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Appelez cette méthode pour faire la queue d’un élément de travail à manipuler par un thread dans la piscine.|
|[CThreadPool::Libération](#release)|Implémentation de `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Appelez cette méthode pour définir le nombre de threads dans le pool.|
|[CThreadPool::SetTimeout](#settimeout)|Appelez cette méthode pour définir le temps maximum en millisecondes que le pool de thread attendra qu’un fil s’arrête.|
|[CThreadPool::Shutdown](#shutdown)|Appelez cette méthode pour arrêter le pool de thread.|

## <a name="remarks"></a>Notes

Les fils de la piscine sont créés et détruits lorsque la piscine est parascée, resized ou fermée. Un exemple de *travailleur* de classe sera créé sur la pile de chaque fil de travailleur dans la piscine. Chaque instance vivra toute la durée du fil.

Immédiatement après la création d’un fil, *Travailleur*::`Initialize` sera appelé sur l’objet associé à ce fil. Immédiatement avant la destruction d’un fil, *Travailleur*::`Terminate` sera appelé. Les deux méthodes doivent accepter un argument **nul.** <strong>\*</strong> La valeur de cet argument est passé à la piscine de fil par le paramètre *pvWorkerParam* de [CThreadPool::Initialize](#initialize).

Lorsqu’il y a des éléments de travail dans la file d’attente et des `Execute` fils de travailleur disponibles pour le travail, un thread de travailleur retirera un élément de la file d’attente et appelle la méthode de *l’objet de travailleur* pour ce fil. Trois éléments sont ensuite transmis à la méthode: `pvWorkerParam` l’élément de `Initialize` la file d’attente, le même passé à *Worker::* et *Travailleur::* `Terminate`, et un pointeur à la structure [OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) utilisé pour la file d’attente du port d’achèvement de l’OO.

La classe *de travailleurs* déclare le type d’articles qui seront mis en file `RequestType`d’attente sur le pool de threads en fournissant un typedef, *Travailleur*:: . Ce type doit être capable d’être jeté vers et à partir d’une ULONG_PTR.

Un exemple d’une classe *de travailleurs* est [CNonStatelessWorker Class](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool::AddRef

Implémentation de `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

### <a name="remarks"></a>Notes

Cette classe ne met pas en œuvre le contrôle à vie en utilisant le comptage des références.

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool

Le constructeur pour la piscine de fil.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Notes

Initialise la valeur de délai d’attente à ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Le délai par défaut est de 36 secondes. Si nécessaire, vous pouvez définir votre propre valeur positive d’intégrant pour ce symbole avant d’inclure atlutil.h.

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool: :CThreadPool

Le destructeur pour le pool de fil.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Notes

Appels [CThreadPool:Shutdown](#shutdown).

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads

Appelez cette méthode pour obtenir le nombre de threads dans la piscine.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de threads dans la piscine.

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool::GetQueueHandle

Appelez cette méthode pour obtenir la poignée du port d’achèvement de l’OO utilisé pour faire la queue des articles de travail.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la poignée de file d’attente ou NULL si le pool de thread n’a pas été paraminé.

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool::GetSize

Appelez cette méthode pour obtenir le nombre de threads dans la piscine.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Paramètres

*pnNumThreads (en)*<br/>
[out] Adresse de la variable qui, sur le succès, reçoit le nombre de threads dans le pool.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout

Appelez cette méthode pour obtenir le temps maximum en millisecondes que le pool de thread attendra pour un thread pour s’éteindre.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Paramètres

*pdwMaxWait*<br/>
[out] Adresse de la variable qui, sur le succès, reçoit le temps maximum en millisecondes que le pool de thread attendra pour un thread pour s’éteindre.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette valeur de délai d’attente est utilisée par [CThreadPool::Shutdown](#shutdown) si aucune autre valeur n’est fournie à cette méthode.

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool::Initialize

Appelez cette méthode pour initialiser le pool de threads.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Paramètres

*pvWorkerParam*<br/>
Le paramètre du travailleur à transmettre `Initialize`à `Execute`l’objet de fil de travail, et `Terminate` les méthodes.

*nNumThreads (en)*<br/>
Le nombre demandé de fils dans la piscine.

Si *nNumThreads* est négatif, sa valeur absolue sera multipliée par le nombre de processeurs dans la machine pour obtenir le nombre total de threads.

Si *nNumThreads* est nul, ATLS_DEFAULT_THREADSPERPROC sera multipliée par le nombre de processeurs dans la machine pour obtenir le nombre total de threads.  La valeur par défaut est de 2 threads par processeur. Si nécessaire, vous pouvez définir votre propre valeur positive d’intégrant pour ce symbole avant d’inclure atlutil.h.

*dwStackSize*<br/>
La taille de pile pour chaque thread dans la piscine.

*hCompletion*<br/>
La poignée d’un objet à associer au port d’achèvement.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool::QueryInterface

Implémentation de `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Notes

Les objets de cette classe peuvent `IUnknown` être interrogés avec succès pour les interfaces et [IThreadPoolConfig.](../../atl/reference/ithreadpoolconfig-interface.md)

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest

Appelez cette méthode pour faire la queue d’un élément de travail à manipuler par un thread dans la piscine.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Paramètres

*requête*<br/>
La demande d’être en file d’attente.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode ajoute un élément de travail à la file d’attente. Les fils de la piscine sélectionnent les articles de la file d’attente dans l’ordre dans lequel ils sont reçus.

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool::Libération

Implémentation de `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

### <a name="remarks"></a>Notes

Cette classe ne met pas en œuvre le contrôle à vie en utilisant le comptage des références.

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool::SetSize

Appelez cette méthode pour définir le nombre de threads dans le pool.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Paramètres

*nNumThreads (en)*<br/>
Le nombre demandé de fils dans la piscine.

Si *nNumThreads* est négatif, sa valeur absolue sera multipliée par le nombre de processeurs dans la machine pour obtenir le nombre total de threads.

Si *nNumThreads* est nul, ATLS_DEFAULT_THREADSPERPROC sera multipliée par le nombre de processeurs dans la machine pour obtenir le nombre total de threads. La valeur par défaut est de 2 threads par processeur. Si nécessaire, vous pouvez définir votre propre valeur positive d’intégrant pour ce symbole avant d’inclure atlutil.h.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Si le nombre de threads spécifiés est inférieur au nombre de threads actuellement dans le pool, l’objet met un message d’arrêt sur la file d’attente pour être capté par un fil d’attente. Lorsqu’un fil d’attente tire le message de la file d’attente, il informe le pool de thread et quitte la procédure de thread. Ce processus est répété jusqu’à ce que le nombre de threads dans le pool atteigne le nombre spécifié ou jusqu’à ce qu’aucun thread n’ait quitté dans la période spécifiée par [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). Dans ce cas, la méthode retournera un HRESULT correspondant à WAIT_TIMEOUT et le message d’arrêt en attente est annulé.

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool::SetTimeout

Appelez cette méthode pour définir le temps maximum en millisecondes que le pool de thread attendra qu’un fil s’arrête.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Paramètres

*dwMaxWait*<br/>
Le temps maximum demandé en millisecondes que le pool de fil attendra pour un fil pour s’arrêter.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Le délai d’attente est parasé à ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Le délai par défaut est de 36 secondes. Si nécessaire, vous pouvez définir votre propre valeur positive d’intégrant pour ce symbole avant d’inclure atlutil.h.

Notez que *dwMaxWait* est le moment où la piscine attendra un seul thread pour s’éteindre. Le temps maximum qui pourrait être pris pour supprimer plusieurs threads de la piscine pourrait être légèrement inférieur *à dwMaxWait* multiplié par le nombre de threads.

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool::Shutdown

Appelez cette méthode pour arrêter le pool de thread.

```cpp
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Paramètres

*dwMaxWait*<br/>
Le temps maximum demandé en millisecondes que le pool de fil attendra pour un fil pour s’arrêter. Si 0 ou aucune valeur est fournie, cette méthode utilisera le délai d’attente défini par [CThreadPool::SetTimeout](#settimeout).

### <a name="remarks"></a>Notes

Cette méthode affiche une demande d’arrêt à tous les threads de la piscine. Si le délai d’attente expire, cette méthode appellera [TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) sur n’importe quel thread qui n’est pas sorti. Cette méthode est appelée automatiquement à partir du destructeur de la classe.

## <a name="see-also"></a>Voir aussi

[IThreadPoolConfig Interface](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DéfautThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Classes](../../atl/reference/atl-classes.md)
