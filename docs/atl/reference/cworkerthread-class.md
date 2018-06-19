---
title: Classe CWorkerThread | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e87001ca341ae27cb173357f74e06e543f5eb262
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365518"
---
# <a name="cworkerthread-class"></a>Classe CWorkerThread
Cette classe crée un thread de travail ou utilise un existant, attend sur un ou plusieurs handles d’objet noyau et exécute une fonction de client spécifié lors d’une des poignées est signalée.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>Paramètres  
 `ThreadTraits`  
 La classe de fournir la fonction de création de thread, tel que [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) ou [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).  
  
## <a name="members"></a>Membres  
  
### <a name="protected-structures"></a>Structures protégés  
  
|Name|Description|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|Le constructeur pour le thread de travail.|  
|[CWorkerThread :: ~ CWorkerThread](#dtor)|Le destructeur pour le thread de travail.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|Appelez cette méthode pour ajouter le handle d’un objet qui peuvent être attendus à la liste gérée par le thread de travail.|  
|[CWorkerThread::AddTimer](#addtimer)|Appelez cette méthode pour ajouter une minuterie qui peuvent être attendue périodique à la liste gérée par le thread de travail.|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Appelez cette méthode pour obtenir le handle du thread du thread de travail.|  
|[CWorkerThread::GetThreadId](#getthreadid)|Appelez cette méthode pour obtenir l’ID de thread du thread de travail.|  
|[CWorkerThread::Initialize](#initialize)|Appelez cette méthode pour initialiser le thread de travail.|  
|[CWorkerThread::RemoveHandle](#removehandle)|Appelez cette méthode pour supprimer un handle de la liste des objets.|  
|[CWorkerThread::Shutdown](#shutdown)|Appelez cette méthode pour arrêter le thread de travail.|  
  
## <a name="remarks"></a>Notes  
  
### <a name="to-use-cworkerthread"></a>Pour utiliser CWorkerThread  
  
1.  Créer une instance de cette classe.  
  
2.  Appelez [CWorkerThread::Initialize](#initialize).  
  
3.  Appelez [CWorkerThread::AddHandle](#addhandle) avec le handle d’un objet de noyau et un pointeur vers une implémentation de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
     - ou  
  
     Appelez [CWorkerThread::AddTimer](#addtimer) avec un pointeur vers une implémentation de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
4.  Implémentez [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) pour intervenir lors de la poignée ou la minuterie est signalé.  
  
5.  Pour supprimer un objet dans la liste des objets, appelez [CWorkerThread::RemoveHandle](#removehandle).  
  
6.  Pour mettre fin au thread, appelez [CWorkerThread::Shutdown](#shutdown).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlutil.h  
  
##  <a name="addhandle"></a>  CWorkerThread::AddHandle  
 Appelez cette méthode pour ajouter le handle d’un objet qui peuvent être attendus à la liste gérée par le thread de travail.  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Le handle d’un objet qui peuvent être attendu.  
  
 `pClient`  
 Le pointeur vers le [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interface sur l’objet à appeler lorsque le handle est signalé.  
  
 `dwParam`  
 Le paramètre doit être passé à [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) lorsque le handle est signalé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) sera appelé par le biais `pClient` lorsque le handle, `hObject`, est signalé.  
  
##  <a name="addtimer"></a>  CWorkerThread::AddTimer  
 Appelez cette méthode pour ajouter une minuterie qui peuvent être attendue périodique à la liste gérée par le thread de travail.  
  
```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *dwInterval*  
 Spécifie le délai du minuteur en millisecondes.  
  
 `pClient`  
 Le pointeur vers le [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interface sur l’objet à appeler lorsque le handle est signalé.  
  
 `dwParam`  
 Le paramètre doit être passé à [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) lorsque le handle est signalé.  
  
 `phTimer`  
 [out] Adresse de la variable HANDLE qui, en cas de réussite, reçoit le handle à la minuterie nouvellement créé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) sera appelé par le biais `pClient` lorsque la minuterie est signalée.  
  
 Passez le handle du minuteur de `phTimer` à [CWorkerThread::RemoveHandle](#removehandle) pour fermer le minuteur.  
  
##  <a name="cworkerthread"></a>  CWorkerThread::CWorkerThread  
 Constructeur.  
  
```
CWorkerThread() throw();
```  
  
##  <a name="dtor"></a>  CWorkerThread :: ~ CWorkerThread  
 Destructeur.  
  
```
~CWorkerThread() throw();
```  
  
### <a name="remarks"></a>Notes  
 Appels [CWorkerThread::Shutdown](#shutdown).  
  
##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle  
 Appelez cette méthode pour obtenir le handle du thread du thread de travail.  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le handle du thread ou NULL si le thread de travail n’a pas été initialisé.  
  
##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId  
 Appelez cette méthode pour obtenir l’ID de thread du thread de travail.  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’ID de thread ou NULL si le thread de travail n’a pas été initialisé.  
  
##  <a name="initialize"></a>  CWorkerThread::Initialize  
 Appelez cette méthode pour initialiser le thread de travail.  
  
```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pThread`  
 Un thread de travail existant.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette méthode doit être appelée pour initialiser l’objet après la création ou après un appel à [CWorkerThread::Shutdown](#shutdown).  
  
 Deux ou plusieurs `CWorkerThread` objets utilisent le même thread de travail, un d’eux sans passer d’arguments puis passez un pointeur vers cet objet pour initialiser le `Initialize` méthodes de toutes les autres. Les objets sont initialisés à l’aide du pointeur doivent être arrêtés avant de l’objet utilisé pour les initialiser.  
  
 Consultez [CWorkerThread::Shutdown](#shutdown) pour plus d’informations sur les modifications de comportement de cette méthode lors de l’initialisation à l’aide d’un pointeur vers un objet existant.  
  
##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle  
 Appelez cette méthode pour supprimer un handle de la liste des objets.  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Le handle à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Lorsque le handle est supprimé [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) sera appelée sur l’objet associé a été passé à [AddHandle](#addhandle). Si cet appel échoue, `CWorkerThread` appellera Windows [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) fonction sur le handle.  
  
##  <a name="shutdown"></a>  CWorkerThread::Shutdown  
 Appelez cette méthode pour arrêter le thread de travail.  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `dwWait`  
 La durée en millisecondes d’attente pour le thread de travail pour l’arrêter. ATL_WORKER_THREAD_WAIT par défaut est 10 secondes. Si nécessaire, vous pouvez définir votre propre valeur pour ce symbole avant d’inclure atlutil.h. 
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite ou une erreur HRESULT d’échec, par exemple si la valeur de délai d’attente, `dwWait`, est dépassée.  
  
### <a name="remarks"></a>Notes  
 Pour réutiliser l’objet, appelez [CWorkerThread::Initialize](#initialize) après avoir appelé cette méthode.  
  
 Notez que l’appel **arrêt** sur un objet initialisé avec un pointeur vers un autre `CWorkerThread` objet n’a aucun effet et renvoie toujours S_OK.  
  
## <a name="see-also"></a>Voir aussi  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Classes](../../atl/reference/atl-classes.md)   
 [Multithreading : Création de Threads de travail](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient, interface](../../atl/reference/iworkerthreadclient-interface.md)
