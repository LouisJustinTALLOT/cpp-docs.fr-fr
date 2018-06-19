---
title: Classe de CThreadPool | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64a165bdffa9f37241991af919d60de2e0dc7a96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365687"
---
# <a name="cthreadpool-class"></a>CThreadPool (classe)
Cette classe fournit un pool de threads de travail qui traitent d’une file d’attente d’éléments de travail.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```  
  
#### <a name="parameters"></a>Paramètres  
 *Processus de travail*  
 La classe conforme à la [archétype de travail](../../atl/reference/worker-archetype.md) en fournissant le code utilisé pour traiter les éléments en file d’attente du pool de threads de travail.  
  
 `ThreadTraits`  
 La classe qui fournit la fonction utilisée pour créer les threads dans le pool.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](#cthreadpool)|Le constructeur pour le pool de threads.|  
|[CThreadPool :: ~ CThreadPool](#dtor)|Le destructeur pour le pool de threads.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CThreadPool::AddRef](#addref)|Implémentation de `IUnknown::AddRef`.|  
|[CThreadPool::GetNumThreads](#getnumthreads)|Appelez cette méthode pour obtenir le nombre de threads dans le pool.|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Appelez cette méthode pour obtenir le descripteur du port de terminaison d’e/s utilisé pour la file d’attente des éléments de travail.|  
|[À CThreadPool::GetSize](#getsize)|Appelez cette méthode pour obtenir le nombre de threads dans le pool.|  
|[CThreadPool::GetTimeout](#gettimeout)|Appelez cette méthode pour obtenir le temps maximal en millisecondes d’attente du pool de threads d’un thread pour l’arrêter.|  
|[CThreadPool::Initialize](#initialize)|Appelez cette méthode pour initialiser le pool de threads.|  
|[CThreadPool::QueryInterface](#queryinterface)|Implémentation de **IUnknown::QueryInterface**.|  
|[CThreadPool::QueueRequest](#queuerequest)|Appelez cette méthode pour la file d’attente d’un élément de travail devant être traitée par un thread dans le pool.|  
|[CThreadPool::Release](#release)|Implémentation de `IUnknown::Release`.|  
|[CThreadPool::SetSize](#setsize)|Appelez cette méthode pour définir le nombre de threads dans le pool.|  
|[CThreadPool::SetTimeout](#settimeout)|Appelez cette méthode pour définir le délai maximal en millisecondes d’attente du pool de threads d’un thread pour l’arrêter.|  
|[CThreadPool::Shutdown](#shutdown)|Appelez cette méthode pour arrêter le pool de threads.|  
  
## <a name="remarks"></a>Notes  
 Threads dans le pool sont créés et détruits lorsque le pool est initialisé, redimensionné ou arrêté. Une instance de classe *travail* sera créé sur la pile de chaque thread de travail dans le pool. Chaque instance se trouvera pour la durée de vie du thread.  
  
 Immédiatement après la création d’un thread, *travail*:: `Initialize` sera appelée sur l’objet associé à ce thread. Juste avant la destruction d’un thread, *travail*:: `Terminate` sera appelée. Les deux méthodes doivent accepter un **void\***  argument. La valeur de cet argument est passée au pool de threads par le biais du `pvWorkerParam` paramètre de [CThreadPool::Initialize](#initialize).  
  
 Lorsqu’il existe des éléments de travail dans les threads de travail et de file d’attente de travail, un thread de travail doivent extraire un objet en dehors de la file d’attente et l’appel de la **Execute** méthode de la *travail* objet pour ce thread. Trois éléments sont ensuite passées à la méthode : l’élément à partir de la file d’attente, le même `pvWorkerParam` passé à *travail*:: `Initialize` et *travail*:: `Terminate`et un pointeur vers le [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) structure utilisée pour la file d’attente du port de fin e/s.  
  
 Le *travail* classe déclare le type des éléments qui seront mises en attente sur le pool de threads en fournissant un typedef, *travail*:: `RequestType`. Ce type doit être capable d’en cours de conversion vers et depuis un **ULONG_PTR entière**.  
  
 Un exemple d’un *travail* classe est [CNonStatelessWorker classe](../../atl/reference/cnonstatelessworker-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IUnknown`  
  
 [Interface IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlutil.h  
  
##  <a name="addref"></a>  CThreadPool::AddRef  
 Implémentation de `IUnknown::AddRef`.  
  
```
ULONG STDMETHODCALLTYPE AddRef() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours 1.  
  
### <a name="remarks"></a>Notes  
 Cette classe n’implémente pas de contrôle de durée de vie à l’aide de comptage de références.  
  
##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool  
 Le constructeur pour le pool de threads.  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>Notes  
 Initialise la valeur de délai d’attente à `ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`. La durée par défaut est 36 secondes. Si nécessaire, vous pouvez définir votre propre valeur entière positive pour ce symbole avant d’inclure atlutil.h.  
  
##  <a name="dtor"></a>  CThreadPool :: ~ CThreadPool  
 Le destructeur pour le pool de threads.  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>Notes  
 Appels [CThreadPool::Shutdown](#shutdown).  
  
##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads  
 Appelez cette méthode pour obtenir le nombre de threads dans le pool.  
  
```
int GetNumThreads() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de threads dans le pool.  
  
##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle  
 Appelez cette méthode pour obtenir le descripteur du port de terminaison d’e/s utilisé pour la file d’attente des éléments de travail.  
  
```
HANDLE GetQueueHandle() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le handle de la file d’attente ou NULL si le pool de threads n’a pas été initialisé.  
  
##  <a name="getsize"></a>  À CThreadPool::GetSize  
 Appelez cette méthode pour obtenir le nombre de threads dans le pool.  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pnNumThreads`  
 [out] Adresse de la variable qui, en cas de réussite, reçoit le nombre de threads dans le pool.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="gettimeout"></a>  CThreadPool::GetTimeout  
 Appelez cette méthode pour obtenir le temps maximal en millisecondes d’attente du pool de threads d’un thread pour l’arrêter.  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pdwMaxWait`  
 [out] Adresse de la variable qui, en cas de réussite, reçoit la durée maximale en millisecondes d’attente du pool de threads d’un thread pour l’arrêter.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette valeur de délai d’attente est utilisée par [CThreadPool::Shutdown](#shutdown) si aucune autre valeur n’est fourni à cette méthode.  
  
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
 `pvWorkerParam`  
 Le paramètre de travail à passer à l’objet de thread de travail `Initialize`, **Execute**, et `Terminate` méthodes.  
  
 `nNumThreads`  
 Le nombre demandé de threads dans le pool.  
  
 Si `nNumThreads` est négatif, sa valeur absolue sera multiplié par le nombre de processeurs sur l’ordinateur pour obtenir le nombre total de threads.  
  
 Si `nNumThreads` est égal à zéro, `ATLS_DEFAULT_THREADSPERPROC` sera multiplié par le nombre de processeurs sur l’ordinateur pour obtenir le nombre total de threads.  La valeur par défaut est 2 threads par processeur. Si nécessaire, vous pouvez définir votre propre valeur entière positive pour ce symbole avant d’inclure atlutil.h.
  
 `dwStackSize`  
 La taille de pile pour chaque thread dans le pool.  
  
 *hCompletion*  
 Le handle d’un objet à associer avec le port de terminaison.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="queryinterface"></a>  CThreadPool::QueryInterface  
 Implémentation de **IUnknown::QueryInterface**.  
  
```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```  
  
### <a name="remarks"></a>Notes  
 Objets de cette classe peuvent être interrogés avec succès pour le **IUnknown** et [interface IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) interfaces.  
  
##  <a name="queuerequest"></a>  CThreadPool::QueueRequest  
 Appelez cette méthode pour la file d’attente d’un élément de travail devant être traitée par un thread dans le pool.  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `request`  
 La demande en file d’attente.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette méthode ajoute un élément de travail à la file d’attente. Les threads dans le pool de choisir des éléments de la file d’attente dans l’ordre dans lequel ils sont reçus.  
  
##  <a name="release"></a>  CThreadPool::Release  
 Implémentation de `IUnknown::Release`.  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours 1.  
  
### <a name="remarks"></a>Notes  
 Cette classe n’implémente pas de contrôle de durée de vie à l’aide de comptage de références.  
  
##  <a name="setsize"></a>  CThreadPool::SetSize  
 Appelez cette méthode pour définir le nombre de threads dans le pool.  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nNumThreads`  
 Le nombre demandé de threads dans le pool.  
  
 Si `nNumThreads` est négatif, sa valeur absolue sera multiplié par le nombre de processeurs sur l’ordinateur pour obtenir le nombre total de threads.  
  
 Si `nNumThreads` est égal à zéro, `ATLS_DEFAULT_THREADSPERPROC` sera multiplié par le nombre de processeurs sur l’ordinateur pour obtenir le nombre total de threads. La valeur par défaut est 2 threads par processeur. Si nécessaire, vous pouvez définir votre propre valeur entière positive pour ce symbole avant d’inclure atlutil.h.
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Si le nombre de threads spécifié est inférieur au nombre de threads actuellement dans le pool, l’objet place un message d’arrêt sur la file d’attente pour être récupéré par un thread en attente. Lorsqu’un thread en attente extrait le message de la file d’attente, il avertit le pool de threads et termine la procédure de thread. Ce processus est répété jusqu'à ce que le nombre de threads dans le pool atteint le nombre spécifié ou jusqu'à ce qu’aucun thread ne s’est arrêté pendant la période spécifiée par [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). Dans ce cas la méthode retourne un HRESULT correspondant à **WAIT_TIMEOUT** et que le message d’arrêt en attente est annulé.  
  
##  <a name="settimeout"></a>  CThreadPool::SetTimeout  
 Appelez cette méthode pour définir le délai maximal en millisecondes d’attente du pool de threads d’un thread pour l’arrêter.  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `dwMaxWait`  
 L’heure demandée maximal en millisecondes d’attente du pool de threads d’un thread pour l’arrêter.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Le délai d’attente est initialisée à `ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`. La durée par défaut est 36 secondes. Si nécessaire, vous pouvez définir votre propre valeur entière positive pour ce symbole avant d’inclure atlutil.h. 
  
 Notez que `dwMaxWait` est le délai d’attente pour un seul thread arrêter le pool. La durée maximale qui pourrait être prise pour supprimer plusieurs threads du pool peut être légèrement inférieure à `dwMaxWait` multipliée par le nombre de threads.  
  
##  <a name="shutdown"></a>  CThreadPool::Shutdown  
 Appelez cette méthode pour arrêter le pool de threads.  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `dwMaxWait`  
 L’heure demandée maximal en millisecondes d’attente du pool de threads d’un thread pour l’arrêter. Si 0 ou aucune valeur n’est fournie, cette méthode utilise le délai défini par [CThreadPool::SetTimeout](#settimeout).  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie une demande d’arrêt à tous les threads dans le pool. Si le délai expire, cette méthode appelle [TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717) sur n’importe quel thread qui n’a pas été arrêté. Cette méthode est appelée automatiquement à partir du destructeur de la classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface de l’interface IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Classes](../../atl/reference/atl-classes.md)
