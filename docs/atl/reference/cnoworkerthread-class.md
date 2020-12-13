---
description: 'En savoir plus sur : classe CNoWorkerThread'
title: CNoWorkerThread, classe
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
ms.openlocfilehash: 5159c04a8390f8933291f697faccedb7353fb48e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141412"
---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread, classe

Utilisez cette classe comme argument pour le `MonitorClass` paramètre de modèle pour mettre en cache des classes si vous souhaitez désactiver la maintenance de cache dynamique.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CNoWorkerThread
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|Équivalent non fonctionnel de [CWorkerThread :: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Équivalent non fonctionnel de [CWorkerThread :: AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Équivalent non fonctionnel de [CWorkerThread :: GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Équivalent non fonctionnel de [CWorkerThread :: GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread :: Initialize](#initialize)|Équivalent non fonctionnel de [CWorkerThread :: Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Équivalent non fonctionnel de [CWorkerThread :: RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread :: Shutdown](#shutdown)|Équivalent non fonctionnel de [CWorkerThread :: Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Notes

Cette classe fournit la même interface publique que [CWorkerThread](../../atl/reference/cworkerthread-class.md). Cette interface doit être fournie par le `MonitorClass` paramètre de modèle pour mettre en cache des classes.

Les méthodes de cette classe sont implémentées pour ne rien faire. Les méthodes qui retournent un HRESULT retournent toujours S_OK, et les méthodes qui retournent un HANDLE ou un ID de thread retournent toujours 0.

## <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a> CNoWorkerThread::AddHandle

Équivalent non fonctionnel de [CWorkerThread :: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a> CNoWorkerThread::AddTimer

Équivalent non fonctionnel de [CWorkerThread :: AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a> CNoWorkerThread::GetThreadHandle

Équivalent non fonctionnel de [CWorkerThread :: GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours la valeur Null.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a> CNoWorkerThread::GetThreadId

Équivalent non fonctionnel de [CWorkerThread :: GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours 0.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a> CNoWorkerThread :: Initialize

Équivalent non fonctionnel de [CWorkerThread :: Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a> CNoWorkerThread::RemoveHandle

Équivalent non fonctionnel de [CWorkerThread :: RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a> CNoWorkerThread :: Shutdown

Équivalent non fonctionnel de [CWorkerThread :: Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

L’implémentation fournie par cette classe ne fait rien.
