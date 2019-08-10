---
title: CThreadPool (classe)
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
ms.openlocfilehash: 07fd470a6aeab0575f2733d72650bd695b8e2752
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915688"
---
# <a name="cthreadpool-class"></a>CThreadPool (classe)

Cette classe fournit un pool de threads de travail qui traitent une file d’attente d’éléments de travail.

## <a name="syntax"></a>Syntaxe

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Paramètres

*Collabor*<br/>
La classe conforme aux [archétype de travail](../../atl/reference/worker-archetype.md) qui fournissent le code utilisé pour traiter les éléments de travail mis en file d’attente dans le pool de threads.

*ThreadTraits*<br/>
Classe fournissant la fonction utilisée pour créer les threads dans le pool.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Constructeur pour le pool de threads.|
|[CThreadPool::~CThreadPool](#dtor)|Destructeur du pool de threads.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Implémentation de `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Appelez cette méthode pour connaître le nombre de threads dans le pool.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Appelez cette méthode pour récupérer le handle du port de terminaison d’e/s utilisé pour mettre en file d’attente les éléments de travail.|
|[CThreadPool::GetSize](#getsize)|Appelez cette méthode pour connaître le nombre de threads dans le pool.|
|[CThreadPool::GetTimeout](#gettimeout)|Appelez cette méthode pour obtenir la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.|
|[CThreadPool::Initialize](#initialize)|Appelez cette méthode pour initialiser le pool de threads.|
|[CThreadPool::QueryInterface](#queryinterface)|Implémentation de `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Appelez cette méthode pour mettre en file d’attente un élément de travail à gérer par un thread dans le pool.|
|[CThreadPool::Release](#release)|Implémentation de `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Appelez cette méthode pour définir le nombre de threads dans le pool.|
|[CThreadPool::SetTimeout](#settimeout)|Appelez cette méthode pour définir la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.|
|[CThreadPool::Shutdown](#shutdown)|Appelez cette méthode pour arrêter le pool de threads.|

## <a name="remarks"></a>Notes

Les threads du pool sont créés et détruits lors de l’initialisation, du redimensionnement ou de l’arrêt du pool. Une instance de la classe Worker sera créée sur la pile de chaque thread de travail dans le pool. Chaque instance est active pendant la durée de vie du thread.

Immédiatement après la création d’un thread, Worker`Initialize` :: sera appelé sur l’objet associé à ce thread. Juste avant la destruction d’un thread, Worker`Terminate` :: sera appelé. Les deux méthodes doivent accepter un argument **void** <strong>\*</strong> . La valeur de cet argument est passée au pool de threads par le biais du paramètre *pvWorkerParam* de [CThreadPool:: Initialize](#initialize).

Lorsqu’il existe des éléments de travail dans la file d’attente et les threads de travail disponibles pour le travail, un thread de travail extrait `Execute` un élément de la file d’attente et appelle la méthode de l’objet *Worker* pour ce thread. Trois éléments sont ensuite passés à la méthode: l’élément de la file d’attente, `pvWorkerParam` le même passé à *Worker*:: `Initialize` et `Terminate` *Worker*::, et un pointeur vers la structure [OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-overlapped) utilisée pour la file d’attente du port de terminaison d’e/s .

La classe Worker déclare le type des éléments qui seront mis en file d’attente sur le pool de threads en fournissant un typedef, `RequestType` *Worker*::. Ce type doit pouvoir être casté vers et à partir d’un ULONG_PTR.

La [classe CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)est un exemple de classe Worker.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlutil. h

##  <a name="addref"></a>  CThreadPool::AddRef

Implémentation de `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

### <a name="remarks"></a>Notes

Cette classe n’implémente pas le contrôle de durée de vie à l’aide du décompte de références.

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

Constructeur pour le pool de threads.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Notes

Initialise la valeur de délai d’attente à ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. L’heure par défaut est de 36 secondes. Si nécessaire, vous pouvez définir votre propre valeur entière positive pour ce symbole avant d’inclure atlutil. h.

##  <a name="dtor"></a>  CThreadPool::~CThreadPool

Destructeur du pool de threads.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Notes

Appelle [CThreadPool:: Shutdown](#shutdown).

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

Appelez cette méthode pour connaître le nombre de threads dans le pool.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de threads dans le pool.

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

Appelez cette méthode pour récupérer le handle du port de terminaison d’e/s utilisé pour mettre en file d’attente les éléments de travail.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le handle de file d’attente ou NULL si le pool de threads n’a pas été initialisé.

##  <a name="getsize"></a>  CThreadPool::GetSize

Appelez cette méthode pour connaître le nombre de threads dans le pool.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Paramètres

*pnNumThreads*<br/>
à Adresse de la variable qui, en cas de réussite, reçoit le nombre de threads dans le pool.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

Appelez cette méthode pour obtenir la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Paramètres

*pdwMaxWait*<br/>
à Adresse de la variable qui, en cas de réussite, reçoit la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette valeur de délai d’attente est utilisée par [CThreadPool:: Shutdown](#shutdown) si aucune autre valeur n’est fournie à cette méthode.

##  <a name="initialize"></a>  CThreadPool::Initialize

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
Paramètre Worker à passer aux méthodes, `Initialize` `Execute`et `Terminate` de l’objet thread de travail.

*nNumThreads*<br/>
Nombre demandé de threads dans le pool.

Si *nNumThreads* est négatif, sa valeur absolue est multipliée par le nombre de processeurs de l’ordinateur pour connaître le nombre total de threads.

Si *nNumThreads* est égal à zéro, ATLS_DEFAULT_THREADSPERPROC est multiplié par le nombre de processeurs de l’ordinateur pour connaître le nombre total de threads.  La valeur par défaut est 2 threads par processeur. Si nécessaire, vous pouvez définir votre propre valeur entière positive pour ce symbole avant d’inclure atlutil. h.

*dwStackSize*<br/>
Taille de la pile pour chaque thread dans le pool.

*hCompletion*<br/>
Handle d’un objet à associer au port de terminaison.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

Implémentation de `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Notes

Les objets de cette classe peuvent être interrogés avec succès `IUnknown` pour les interfaces et [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) .

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

Appelez cette méthode pour mettre en file d’attente un élément de travail à gérer par un thread dans le pool.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Paramètres

*request*<br/>
Demande à mettre en file d’attente.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode ajoute un élément de travail à la file d’attente. Les threads du pool sélectionnent les éléments de la file d’attente dans l’ordre dans lequel ils sont reçus.

##  <a name="release"></a>  CThreadPool::Release

Implémentation de `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

### <a name="remarks"></a>Notes

Cette classe n’implémente pas le contrôle de durée de vie à l’aide du décompte de références.

##  <a name="setsize"></a>  CThreadPool::SetSize

Appelez cette méthode pour définir le nombre de threads dans le pool.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Paramètres

*nNumThreads*<br/>
Nombre demandé de threads dans le pool.

Si *nNumThreads* est négatif, sa valeur absolue est multipliée par le nombre de processeurs de l’ordinateur pour connaître le nombre total de threads.

Si *nNumThreads* est égal à zéro, ATLS_DEFAULT_THREADSPERPROC est multiplié par le nombre de processeurs de l’ordinateur pour connaître le nombre total de threads. La valeur par défaut est 2 threads par processeur. Si nécessaire, vous pouvez définir votre propre valeur entière positive pour ce symbole avant d’inclure atlutil. h.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Si le nombre de threads spécifiés est inférieur au nombre de threads actuellement dans le pool, l’objet place un message d’arrêt dans la file d’attente pour être récupéré par un thread en attente. Lorsqu’un thread en attente extrait le message de la file d’attente, il notifie le pool de threads et ferme la procédure de thread. Ce processus est répété jusqu’à ce que le nombre de threads dans le pool atteigne le nombre spécifié ou jusqu’à ce qu’aucun thread ne s’arrête dans la période spécifiée par [GetTimeout](#gettimeout)/ [setTimeout](#settimeout). Dans cette situation, la méthode retourne un HRESULT correspondant à WAIT_TIMEOUT et le message d’arrêt en attente est annulé.

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

Appelez cette méthode pour définir la durée maximale en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Paramètres

*dwMaxWait*<br/>
Durée maximale demandée en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Le délai d’attente est initialisé à ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. L’heure par défaut est de 36 secondes. Si nécessaire, vous pouvez définir votre propre valeur entière positive pour ce symbole avant d’inclure atlutil. h.

Notez que *dwMaxWait* est la durée pendant laquelle le pool attend qu’un seul thread s’arrête. Le temps maximal qui peut être pris pour supprimer plusieurs threads du pool peut être légèrement inférieur à *dwMaxWait* multiplié par le nombre de threads.

##  <a name="shutdown"></a>  CThreadPool::Shutdown

Appelez cette méthode pour arrêter le pool de threads.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Paramètres

*dwMaxWait*<br/>
Durée maximale demandée en millisecondes pendant laquelle le pool de threads attendra qu’un thread s’arrête. Si la valeur est 0 ou si aucune valeur n’est fournie, cette méthode utilise le délai d’attente défini par [CThreadPool:: setTimeout](#settimeout).

### <a name="remarks"></a>Notes

Cette méthode publie une demande d’arrêt pour tous les threads du pool. Si le délai d’attente expire, cette méthode appellera [TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread) sur tout thread qui ne s’est pas arrêté. Cette méthode est appelée automatiquement à partir du destructeur de la classe.

## <a name="see-also"></a>Voir aussi

[IThreadPoolConfig, interface](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Classes](../../atl/reference/atl-classes.md)
