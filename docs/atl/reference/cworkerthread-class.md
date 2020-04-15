---
title: Classe CWorkerThread
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
ms.openlocfilehash: 05e6b432d44927fa7e276792643e29c80c42d822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330222"
---
# <a name="cworkerthread-class"></a>Classe CWorkerThread

Cette classe crée un thread de travailleur ou utilise un fil existant, attend sur une ou plusieurs poignées d’objets de noyau, et exécute une fonction client spécifiée lorsque l’une des poignées est signalée.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Paramètres

*ThreadTraits*<br/>
La classe fournissant la fonction de création de thread, tels que [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) ou [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Membres

### <a name="protected-structures"></a>Structures protégées

|Nom|Description|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|Le constructeur pour le fil de travail.|
|[CWorkerThread::CWorkerThread](#dtor)|Le destructeur pour le fil de travailleur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|Appelez cette méthode pour ajouter la poignée d’un objet attentable à la liste maintenue par le thread du travailleur.|
|[CWorkerThread::AddTimer](#addtimer)|Appelez cette méthode pour ajouter une minuterie périodique à la liste maintenue par le fil de travailleur.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Appelez cette méthode pour obtenir la poignée de fil du fil de travail.|
|[CWorkerThread::GetThreadId](#getthreadid)|Appelez cette méthode pour obtenir l’ID de fil du fil de travail.|
|[CWorkerThread::Initialize](#initialize)|Appelez cette méthode pour initialiser le fil de travail.|
|[CWorkerThread::RemoveHandle](#removehandle)|Appelez cette méthode pour supprimer une poignée de la liste des objets serveurs.|
|[CWorkerThread::Shutdown](#shutdown)|Appelez cette méthode pour arrêter le fil de travail.|

## <a name="remarks"></a>Notes

### <a name="to-use-cworkerthread"></a>Pour utiliser CWorkerThread

1. Créez un exemple de cette classe.

1. Appelez [CWorkerThread:Initialize](#initialize).

1. Appelez [CWorkerThread::AddHandle](#addhandle) avec la poignée d’un objet de noyau et un pointeur à une mise en œuvre de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \- ou -

   Appelez [CWorkerThread:AddTimer](#addtimer) avec un pointeur à une mise en œuvre de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Implémentez [IWorkerThreadClient::Exécutez](../../atl/reference/iworkerthreadclient-interface.md#execute) pour prendre des mesures lorsque le manche ou la minuterie est signalé.

1. Pour supprimer un objet de la liste des objets serveurs, appelez [CWorkerThread::RemoveHandle](#removehandle).

1. Pour mettre fin au fil, appelez [CWorkerThread::Shutdown](#shutdown).

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="cworkerthreadaddhandle"></a><a name="addhandle"></a>CWorkerThread::AddHandle

Appelez cette méthode pour ajouter la poignée d’un objet attentable à la liste maintenue par le thread du travailleur.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Le manche à un objet attentable.

*pClient (en)*<br/>
Le pointeur de l’interface [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) sur l’objet à appeler lorsque la poignée est signalée.

*dwParam dwParam*<br/>
Le paramètre à passer à [IWorkerThreadClient::Exécutez](../../atl/reference/iworkerthreadclient-interface.md#execute) quand la poignée est signalée.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) sera appelé par *pClient* lorsque la poignée, *hObject*, est signalé.

## <a name="cworkerthreadaddtimer"></a><a name="addtimer"></a>CWorkerThread::AddTimer

Appelez cette méthode pour ajouter une minuterie périodique à la liste maintenue par le fil de travailleur.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Paramètres

*dwInterval*<br/>
Spécifie la période de la minuterie en millisecondes.

*pClient (en)*<br/>
Le pointeur de l’interface [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) sur l’objet à appeler lorsque la poignée est signalée.

*dwParam dwParam*<br/>
Le paramètre à passer à [IWorkerThreadClient::Exécutez](../../atl/reference/iworkerthreadclient-interface.md#execute) quand la poignée est signalée.

*phTimer phTimer*<br/>
[out] Adresse de la variable HANDLE qui, sur le succès, reçoit la poignée à la minuterie nouvellement créée.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) sera appelé par *pClient* lorsque la minuterie est signalée.

Passez la poignée de minuterie de *phTimer* à [CWorkerThread::RemoveHandle](#removehandle) pour fermer la minuterie.

## <a name="cworkerthreadcworkerthread"></a><a name="cworkerthread"></a>CWorkerThread::CWorkerThread

Constructeur.

```
CWorkerThread() throw();
```

## <a name="cworkerthreadcworkerthread"></a><a name="dtor"></a>CWorkerThread::CWorkerThread

Destructeur.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Notes

Appels [CWorkerThread:Shutdown](#shutdown).

## <a name="cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

Appelez cette méthode pour obtenir la poignée de fil du fil de travail.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la poignée de thread ou NULL si le thread du travailleur n’a pas été para initialisé.

## <a name="cworkerthreadgetthreadid"></a><a name="getthreadid"></a>CWorkerThread::GetThreadId

Appelez cette méthode pour obtenir l’ID de fil du fil de travail.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie l’ID de fil ou NULL si le thread du travailleur n’a pas été para initialisé.

## <a name="cworkerthreadinitialize"></a><a name="initialize"></a>CWorkerThread::Initialize

Appelez cette méthode pour initialiser le fil de travail.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Paramètres

*Pthread*<br/>
Un fil de travail existant.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée à initialiser l’objet après la création ou après un appel à [CWorkerThread::Shutdown](#shutdown).

Pour avoir deux `CWorkerThread` objets ou plus utiliser le même fil de travailleur, initialiser l’un `Initialize` d’eux sans passer aucun argument, puis passer un pointeur à cet objet aux méthodes des autres. Les objets paralysés à l’aide du pointeur doivent être arrêtés avant que l’objet utilisé pour les initialiser.

Voir [CWorkerThread:Shutdown](#shutdown) pour obtenir des informations sur la façon dont le comportement de cette méthode change lorsqu’il est paralysé à l’aide d’un pointeur à un objet existant.

## <a name="cworkerthreadremovehandle"></a><a name="removehandle"></a>CWorkerThread::RemoveHandle

Appelez cette méthode pour supprimer une poignée de la liste des objets serveurs.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
La poignée à enlever.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Lorsque le manche est enlevé [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) sera appelé sur l’objet associé qui a été passé à [AddHandle](#addhandle). Si cet appel `CWorkerThread` échoue, appellera la fonction [Windows CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) sur la poignée.

## <a name="cworkerthreadshutdown"></a><a name="shutdown"></a>CWorkerThread::Shutdown

Appelez cette méthode pour arrêter le fil de travail.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Paramètres

*dwWait*<br/>
Le temps en millisecondes d’attendre que le fil du travailleur s’arrête. ATL_WORKER_THREAD_WAIT par défaut à 10 secondes. Si nécessaire, vous pouvez définir votre propre valeur pour ce symbole avant d’inclure atlutil.h.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec, comme si la valeur de délai *d’attente, dwWait*, est dépassée.

### <a name="remarks"></a>Notes

Pour réutiliser l’objet, appelez [CWorkerThread::Initialize](#initialize) après avoir appelé cette méthode.

Notez `Shutdown` que l’appel d’un `CWorkerThread` objet paralysé avec un pointeur d’un autre objet n’a aucun effet et retourne toujours S_OK.

## <a name="see-also"></a>Voir aussi

[DéfautThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Classes](../../atl/reference/atl-classes.md)<br/>
[Multithreading : création de threads de travail](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient Interface](../../atl/reference/iworkerthreadclient-interface.md)
