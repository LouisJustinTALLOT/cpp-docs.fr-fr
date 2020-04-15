---
title: Classe CNoWorkerThread
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
ms.openlocfilehash: 90056e648a53218ac06083d43ca34870e1ca72fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326705"
---
# <a name="cnoworkerthread-class"></a>Classe CNoWorkerThread

Utilisez cette classe comme `MonitorClass` argument pour le paramètre de modèle pour les classes de cache si vous voulez désactiver la maintenance dynamique de cache.

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
|[CNoWorkerThread::AddHandle](#addhandle)|Équivalent non fonctionnel de [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Équivalent non fonctionnel de [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Équivalent non fonctionnel de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Équivalent non fonctionnel de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Initialize](#initialize)|Équivalent non fonctionnel de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Équivalent non fonctionnel de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Shutdown](#shutdown)|Équivalent non fonctionnel de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Notes

Cette classe fournit la même interface publique que [CWorkerThread](../../atl/reference/cworkerthread-class.md). Cette interface devrait être fournie `MonitorClass` par le paramètre du modèle pour les classes de cache.

Les méthodes de cette classe sont mises en œuvre pour ne rien faire. Les méthodes qui renvoient un HRESULT retournent toujours S_OK, et les méthodes qui renvoient un HANDLE ou un ID de fil retournent toujours 0.

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CNoWorkerThread::AddHandle

Équivalent non fonctionnel de [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

La mise en œuvre fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread::AddTimer

Équivalent non fonctionnel de [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

La mise en œuvre fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle

Équivalent non fonctionnel de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur Null.

### <a name="remarks"></a>Notes

La mise en œuvre fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CNoWorkerThread::GetThreadId

Équivalent non fonctionnel de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours 0.

### <a name="remarks"></a>Notes

La mise en œuvre fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread::Initialize

Équivalent non fonctionnel de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

La mise en œuvre fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorkerThread::RemoveHandle

Équivalent non fonctionnel de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

La mise en œuvre fournie par cette classe ne fait rien.

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorkerThread::Shutdown

Équivalent non fonctionnel de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours S_OK.

### <a name="remarks"></a>Notes

La mise en œuvre fournie par cette classe ne fait rien.
