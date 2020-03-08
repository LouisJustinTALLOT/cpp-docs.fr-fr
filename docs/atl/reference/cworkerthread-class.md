---
title: CWorkerThread (classe)
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: f1aa76514b98bbf12f8e516d3d54f68e8ef4dd7d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862916"
---
# <a name="cworkerthread-class"></a>CWorkerThread (classe)

Cette classe crée un thread de travail ou en utilise un, attend un ou plusieurs handles d’objet de noyau et exécute une fonction cliente spécifiée lorsque l’un des descripteurs est signalé.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Paramètres

*ThreadTraits*<br/>
Classe fournissant la fonction de création de thread, telle que [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) ou [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Membres

### <a name="protected-structures"></a>Structures protégées

|Name|Description|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CWorkerThread :: CWorkerThread](#cworkerthread)|Constructeur du thread de travail.|
|[CWorkerThread :: ~ CWorkerThread](#dtor)|Destructeur du thread de travail.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CWorkerThread :: AddHandle](#addhandle)|Appelez cette méthode pour ajouter un handle d’objet pouvant être attendu à la liste gérée par le thread de travail.|
|[CWorkerThread :: AddTimer](#addtimer)|Appelez cette méthode pour ajouter un minuteur périodique attendu à la liste gérée par le thread de travail.|
|[CWorkerThread :: GetThreadHandle](#getthreadhandle)|Appelez cette méthode pour récupérer le handle de thread du thread de travail.|
|[CWorkerThread :: GetThreadId](#getthreadid)|Appelez cette méthode pour récupérer l’ID de thread du thread de travail.|
|[CWorkerThread :: Initialize](#initialize)|Appelez cette méthode pour initialiser le thread de travail.|
|[CWorkerThread :: RemoveHandle](#removehandle)|Appelez cette méthode pour supprimer un handle de la liste d’objets pouvant être attendus.|
|[CWorkerThread :: Shutdown](#shutdown)|Appelez cette méthode pour arrêter le thread de travail.|

## <a name="remarks"></a>Notes

### <a name="to-use-cworkerthread"></a>Pour utiliser CWorkerThread

1. Créez une instance de cette classe.

1. Appelez [CWorkerThread :: Initialize](#initialize).

1. Appelez [CWorkerThread :: AddHandle](#addhandle) avec le handle d’un objet de noyau et un pointeur vers une implémentation de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \- ou -

   Appelez [CWorkerThread :: AddTimer](#addtimer) avec un pointeur vers une implémentation de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Implémentez [IWorkerThreadClient :: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) pour effectuer une action lorsque le handle ou le minuteur est signalé.

1. Pour supprimer un objet de la liste des objets pouvant être attendus, appelez [CWorkerThread :: RemoveHandle](#removehandle).

1. Pour terminer le thread, appelez [CWorkerThread :: Shutdown](#shutdown).

## <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

##  <a name="addhandle"></a>CWorkerThread :: AddHandle

Appelez cette méthode pour ajouter un handle d’objet pouvant être attendu à la liste gérée par le thread de travail.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Handle d’un objet qui est attendu.

*pClient*<br/>
Pointeur vers l’interface [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) sur l’objet à appeler lorsque le handle est signalé.

*dwParam*<br/>
Paramètre à passer à [IWorkerThreadClient :: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) quand le handle est signalé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

[IWorkerThreadClient :: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) est appelé via *pClient* lorsque le handle, *hObject*, est signalé.

##  <a name="addtimer"></a>CWorkerThread :: AddTimer

Appelez cette méthode pour ajouter un minuteur périodique attendu à la liste gérée par le thread de travail.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Paramètres

*dwInterval*<br/>
Spécifie la période, en millisecondes, de la minuterie.

*pClient*<br/>
Pointeur vers l’interface [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) sur l’objet à appeler lorsque le handle est signalé.

*dwParam*<br/>
Paramètre à passer à [IWorkerThreadClient :: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) quand le handle est signalé.

*phTimer*<br/>
à Adresse de la variable de HANDLE qui, en cas de réussite, reçoit le handle de la minuterie nouvellement créée.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

[IWorkerThreadClient :: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) est appelé via *pClient* lorsque la minuterie est signalée.

Transmettez le handle de la minuterie de *phTimer* à [CWorkerThread :: RemoveHandle](#removehandle) pour fermer le minuteur.

##  <a name="cworkerthread"></a>CWorkerThread :: CWorkerThread

Constructeur.

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>CWorkerThread :: ~ CWorkerThread

Destructeur.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Notes

Appelle [CWorkerThread :: Shutdown](#shutdown).

##  <a name="getthreadhandle"></a>CWorkerThread :: GetThreadHandle

Appelez cette méthode pour récupérer le handle de thread du thread de travail.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le handle de thread ou la valeur NULL si le thread de travail n’a pas été initialisé.

##  <a name="getthreadid"></a>CWorkerThread :: GetThreadId

Appelez cette méthode pour récupérer l’ID de thread du thread de travail.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’ID de thread ou NULL si le thread de travail n’a pas été initialisé.

##  <a name="initialize"></a>CWorkerThread :: Initialize

Appelez cette méthode pour initialiser le thread de travail.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Paramètres

*pThread*<br/>
Thread de travail existant.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée pour initialiser l’objet après sa création ou après un appel à [CWorkerThread :: Shutdown](#shutdown).

Pour que deux ou plusieurs objets `CWorkerThread` utilisent le même thread de travail, initialisez l’un d’eux sans passer d’arguments, puis passez un pointeur vers cet objet aux méthodes `Initialize` des autres. Les objets initialisés à l’aide du pointeur doivent être arrêtés avant l’objet utilisé pour les initialiser.

Consultez [CWorkerThread :: Shutdown](#shutdown) pour plus d’informations sur la façon dont le comportement de cette méthode change lorsqu’elle est initialisée à l’aide d’un pointeur vers un objet existant.

##  <a name="removehandle"></a>CWorkerThread :: RemoveHandle

Appelez cette méthode pour supprimer un handle de la liste d’objets pouvant être attendus.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Handle à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Quand le handle est supprimé, [IWorkerThreadClient :: CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) est appelé sur l’objet associé qui a été passé à [AddHandle](#addhandle). Si cet appel échoue, `CWorkerThread` appellera la fonction Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) sur le handle.

##  <a name="shutdown"></a>CWorkerThread :: Shutdown

Appelez cette méthode pour arrêter le thread de travail.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Paramètres

*dwWait*<br/>
Délai d’attente, en millisecondes, avant l’arrêt du thread de travail. ATL_WORKER_THREAD_WAIT la valeur par défaut est 10 secondes. Si nécessaire, vous pouvez définir votre propre valeur pour ce symbole avant d’inclure atlutil. h.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec, par exemple si la valeur du délai d’attente, *dwWait*, est dépassée.

### <a name="remarks"></a>Notes

Pour réutiliser l’objet, appelez [CWorkerThread :: Initialize](#initialize) après avoir appelé cette méthode.

Notez que l’appel de `Shutdown` sur un objet initialisé avec un pointeur vers un autre objet `CWorkerThread` n’a aucun effet et retourne toujours S_OK.

## <a name="see-also"></a>Voir aussi

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Classes](../../atl/reference/atl-classes.md)<br/>
[Multithreading : création de threads de travail](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient, interface](../../atl/reference/iworkerthreadclient-interface.md)
