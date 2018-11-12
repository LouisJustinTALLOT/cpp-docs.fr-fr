---
title: Cnoworkerthread, classe
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: fcd103283738ce7d573faa2fb1025ee2af642021
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520209"
---
# <a name="cnoworkerthread-class"></a>Cnoworkerthread, classe

Utilisez cette classe comme argument pour le `MonitorClass` paramètre de modèle pour les classes de cache si vous souhaitez désactiver la maintenance du cache dynamique.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CNoWorkerThread
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|Équivalent non fonctionnelles de [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Équivalent non fonctionnelles de [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Équivalent non fonctionnelles de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Équivalent non fonctionnelles de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Initialize](#initialize)|Équivalent non fonctionnelles de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Équivalent non fonctionnelles de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Shutdown](#shutdown)|Équivalent non fonctionnelles de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Notes

Cette classe fournit la même interface publique en tant que [CWorkerThread](../../atl/reference/cworkerthread-class.md). Cette interface est censée être fournies par le `MonitorClass` paramètre de modèle pour les classes de cache.

Les méthodes de cette classe sont implémentées pour ne rien faire. Les méthodes qui retournent une valeur HRESULT toujours retournent S_OK et les méthodes qui retournent un ID de HANDLE ou de thread toujours retournent 0.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle

Équivalent non fonctionnelles de [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer

Équivalent non fonctionnelles de [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle

Équivalent non fonctionnelles de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours NULL.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId

Équivalent non fonctionnelles de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours 0.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

##  <a name="initialize"></a>  CNoWorkerThread::Initialize

Équivalent non fonctionnelles de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle

Équivalent non fonctionnelles de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown

Équivalent non fonctionnelles de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.
