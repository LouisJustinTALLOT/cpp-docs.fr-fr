---
title: CWorkerThread, classe | Microsoft Docs
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
ms.openlocfilehash: 79855860b4d2d6bfee328f8fa07f2a3ba6cfd69c
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861458"
---
# <a name="cworkerthread-class"></a>CWorkerThread, classe

Cette classe crée un thread de travail ou utilise un, attend sur un ou plusieurs handles d’objet de noyau et exécute une fonction cliente spécifiée lorsqu’une des poignées est signalée.

> [!IMPORTANT]
> Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Paramètres

*ThreadTraits*<br/>
La classe de fournir la fonction de création de thread, tel que [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) ou [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Membres

### <a name="protected-structures"></a>Structures protégées

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
|[CWorkerThread::AddHandle](#addhandle)|Appelez cette méthode pour ajouter le handle d’un objet pouvant être attendu à la liste gérée par le thread de travail.|
|[CWorkerThread::AddTimer](#addtimer)|Appelez cette méthode pour ajouter une minuterie périodique pouvant être attendue à la liste gérée par le thread de travail.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Appelez cette méthode pour obtenir le handle du thread du thread actif.|
|[CWorkerThread::GetThreadId](#getthreadid)|Appelez cette méthode pour obtenir l’ID de thread du thread actif.|
|[CWorkerThread::Initialize](#initialize)|Appelez cette méthode pour initialiser le thread de travail.|
|[CWorkerThread::RemoveHandle](#removehandle)|Appelez cette méthode pour supprimer un handle de la liste d’objets pouvant être attendus.|
|[CWorkerThread::Shutdown](#shutdown)|Appelez cette méthode pour arrêter le thread de travail.|

## <a name="remarks"></a>Notes

### <a name="to-use-cworkerthread"></a>Pour utiliser CWorkerThread

1. Créez une instance de cette classe.

1. Appelez [CWorkerThread::Initialize](#initialize).

1. Appelez [CWorkerThread::AddHandle](#addhandle) avec le handle d’un objet de noyau et un pointeur vers une implémentation de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \- ou -

   Appelez [CWorkerThread::AddTimer](#addtimer) avec un pointeur vers une implémentation de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Implémentez [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) à prendre des mesures quand la poignée ou la minuterie est signalée.

1. Pour supprimer un objet dans la liste des objets pouvant être attendus, appelez [CWorkerThread::RemoveHandle](#removehandle).

1. Pour mettre fin au thread, appelez [CWorkerThread::Shutdown](#shutdown).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

##  <a name="addhandle"></a>  CWorkerThread::AddHandle

Appelez cette méthode pour ajouter le handle d’un objet pouvant être attendu à la liste gérée par le thread de travail.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Handle d’un objet pouvant être attendu.

*pClient*<br/>
Le pointeur vers le [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interface sur l’objet à appeler lorsque le handle est signalé.

*dwParam*<br/>
Le paramètre à passer à [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) lorsque le handle est signalé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) sera appelée par le biais *pClient* lorsque le handle, *hObject*, est signalé.

##  <a name="addtimer"></a>  CWorkerThread::AddTimer

Appelez cette méthode pour ajouter une minuterie périodique pouvant être attendue à la liste gérée par le thread de travail.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Paramètres

*dwInterval*<br/>
Spécifie la période de l’horloge en millisecondes.

*pClient*<br/>
Le pointeur vers le [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interface sur l’objet à appeler lorsque le handle est signalé.

*dwParam*<br/>
Le paramètre à passer à [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) lorsque le handle est signalé.

*phTimer*<br/>
[out] Adresse de la variable HANDLE qui, en cas de réussite, reçoit le handle à la minuterie nouvellement créé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) sera appelée par le biais *pClient* lorsque le minuteur est signalé.

Passez le handle du minuteur de *phTimer* à [CWorkerThread::RemoveHandle](#removehandle) pour fermer la minuterie.

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

Appelez cette méthode pour obtenir le handle du thread du thread actif.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le handle du thread ou NULL si le thread de travail n’a pas été initialisé.

##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId

Appelez cette méthode pour obtenir l’ID de thread du thread actif.

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

*pThread*<br/>
Un thread de travail existant.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée pour initialiser l’objet après la création ou après un appel à [CWorkerThread::Shutdown](#shutdown).

Deux ou plusieurs `CWorkerThread` objets utilisent le même thread de travail, un d’eux sans passer d’arguments puis passez un pointeur vers cet objet pour initialiser le `Initialize` méthodes de toutes les autres. Les objets sont initialisés à l’aide du pointeur doivent être arrêtés avant de l’objet utilisé pour les initialiser.

Consultez [CWorkerThread::Shutdown](#shutdown) pour plus d’informations sur les modifications de comportement de cette méthode lorsque initialisée à l’aide d’un pointeur vers un objet existant.

##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle

Appelez cette méthode pour supprimer un handle de la liste d’objets pouvant être attendus.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Handle à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Lorsque le handle est supprimé [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) est appelée sur l’objet associé a été passé à [AddHandle](#addhandle). Si cet appel échoue, `CWorkerThread` appellera le Windows [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211) fonction sur le handle.

##  <a name="shutdown"></a>  CWorkerThread::Shutdown

Appelez cette méthode pour arrêter le thread de travail.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Paramètres

*dwWait*<br/>
Durée en millisecondes à attendre pour le thread de travail à arrêter. ATL_WORKER_THREAD_WAIT par défaut est 10 secondes. Si nécessaire, vous pouvez définir votre propre valeur pour ce symbole avant d’inclure atlutil.h.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec, par exemple si la valeur de délai d’attente, *dwWait*, est dépassée.

### <a name="remarks"></a>Notes

Pour réutiliser l’objet, appelez [CWorkerThread::Initialize](#initialize) après l’appel de cette méthode.

Notez que l’appel `Shutdown` sur un objet initialisé avec un pointeur vers une autre `CWorkerThread` objet n’a aucun effet et renvoie toujours S_OK.

## <a name="see-also"></a>Voir aussi

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Classes](../../atl/reference/atl-classes.md)<br/>
[Multithreading : création de threads de travail](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient, interface](../../atl/reference/iworkerthreadclient-interface.md)
