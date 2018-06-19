---
title: Classe de CNoWorkerThread | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85e1962d10f274f4f8c35ba27cb05c41e8bf19cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363082"
---
# <a name="cnoworkerthread-class"></a>Classe de CNoWorkerThread
Utilisez cette classe comme argument pour le `MonitorClass` paramètre de modèle pour les classes de cache si vous souhaitez désactiver la maintenance du cache dynamique.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](#addhandle)|Non-équivalent du [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|  
|[CNoWorkerThread::AddTimer](#addtimer)|Non-équivalent du [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|  
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Non-équivalent du [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|  
|[CNoWorkerThread::GetThreadId](#getthreadid)|Non-équivalent du [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|  
|[CNoWorkerThread::Initialize](#initialize)|Non-équivalent du [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|  
|[CNoWorkerThread::RemoveHandle](#removehandle)|Non-équivalent du [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|  
|[CNoWorkerThread::Shutdown](#shutdown)|Non-équivalent du [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit la même interface publique en tant que [CWorkerThread](../../atl/reference/cworkerthread-class.md). Cette interface est censée être fournies par le `MonitorClass` paramètre de modèle pour les classes de cache.  
  
 Les méthodes de cette classe sont implémentés pour ne rien faire. Les méthodes qui retournent une valeur HRESULT toujours retournent S_OK et les méthodes qui retournent un ID de HANDLE ou de thread toujours retournent 0.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlutil.h  
  
##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle  
 Non-équivalent du [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
```
HRESULT AddHandle(HANDLE /* hObject
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */) throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours S_OK.  
  
### <a name="remarks"></a>Notes  
 L’implémentation fournie par cette classe ne fait rien.  
  
##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer  
 Non-équivalent du [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).  
  
```
HRESULT AddTimer(DWORD /* dwInterval
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */,
    HANDLE* /* phTimer
 */) throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours S_OK.  
  
### <a name="remarks"></a>Notes  
 L’implémentation fournie par cette classe ne fait rien.  
  
##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle  
 Non-équivalent du [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours NULL.  
  
### <a name="remarks"></a>Notes  
 L’implémentation fournie par cette classe ne fait rien.  
  
##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId  
 Non-équivalent du [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation fournie par cette classe ne fait rien.  
  
##  <a name="initialize"></a>  CNoWorkerThread::Initialize  
 Non-équivalent du [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours S_OK.  
  
### <a name="remarks"></a>Notes  
 L’implémentation fournie par cette classe ne fait rien.  
  
##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle  
 Non-équivalent du [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours S_OK.  
  
### <a name="remarks"></a>Notes  
 L’implémentation fournie par cette classe ne fait rien.  
  
##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown  
 Non-équivalent du [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours S_OK.  
  
### <a name="remarks"></a>Notes  
 L’implémentation fournie par cette classe ne fait rien.
