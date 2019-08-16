---
title: Archétype Worker
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 7f28b9e64c88a5be440417dd9d22f129ee7d6edf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495265"
---
# <a name="worker-archetype"></a>Archétype Worker

Les classes qui se conforment aux archétype de *travail* fournissent le code pour traiter les éléments de travail mis en file d’attente sur un pool de threads.

**Implémentation**

Pour implémenter une classe conforme à ce archétype, la classe doit fournir les fonctionnalités suivantes:

|Méthode|Description|
|------------|-----------------|
|[Initialize](#initialize)|Appelé pour initialiser l’objet Worker avant que toutes les demandes soient passées à [Execute](#execute).|
|[Execute](#execute)|Appelé pour traiter un élément de travail.|
|[Terminate](#terminate)|Appelé pour désinitialiser l’objet Worker une fois que toutes les demandes ont été passées à [Execute](#execute).|

|TypeDef|Description|
|-------------|-----------------|
|[RequestType](#requesttype)|Typedef pour le type d’élément de travail qui peut être traité par la classe Worker.|

Une classe *Worker* classique ressemble à ceci:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Implémentations existantes**

Ces classes sont conformes à ce archétype:

|Classe|Description|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Reçoit des demandes du pool de threads et les transmet à un objet de travail créé et détruit pour chaque requête.|

**Utilisation**

Ces paramètres de modèle s’attendent à ce que la classe soit conforme à ce archétype:

|Nom du paramètre|Utilisé par|
|--------------------|-------------|
|*Collabor*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Collabor*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Configuration requise

**En-tête:** atlutil. h

## <a name="execute"></a>WorkerArchetype::Execute

Appelé pour traiter un élément de travail.

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Paramètres

*request*<br/>
Élément de travail à traiter. L’élément de travail est du même type que `RequestType`.

*pvWorkerParam*<br/>
Paramètre personnalisé compréhensible par la classe Worker. Également passé à `WorkerArchetype::Initialize` et `Terminate`.

*pOverlapped*<br/>
Pointeur vers la structure [OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) utilisée pour créer la file d’attente sur laquelle les éléments de travail ont été mis en file d’attente.

## <a name="initialize"></a> WorkerArchetype::Initialize

Appelé pour initialiser l’objet Worker avant que toutes les demandes `WorkerArchetype::Execute`soient passées à.
```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Paramètres

*pvParam*<br/>
Paramètre personnalisé compréhensible par la classe Worker. Également passé à `WorkerArchetype::Terminate` et `WorkerArchetype::Execute`.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="requesttype"></a> WorkerArchetype::RequestType

Typedef pour le type d’élément de travail qui peut être traité par la classe Worker.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Notes

Ce type doit être utilisé comme premier paramètre de `WorkerArchetype::Execute` et doit pouvoir être casté vers et à partir d’un ULONG_PTR.

## <a name="terminate"></a> WorkerArchetype::Terminate

Appelé pour désinitialiser l’objet Worker une fois que toutes les demandes `WorkerArchetype::Execute`ont été passées à).

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Paramètres

*pvParam*<br/>
Paramètre personnalisé compréhensible par la classe Worker. Également passé à `WorkerArchetype::Initialize` et `WorkerArchetype::Execute`.

## <a name="see-also"></a>Voir aussi

[Concepts](../../atl/active-template-library-atl-concepts.md)<br/>
[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
