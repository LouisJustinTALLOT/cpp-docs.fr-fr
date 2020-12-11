---
description: 'En savoir plus sur : Worker archétype'
title: Archétype Worker
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 8cb8c2b281bbdc074bb700b77a856f4d26c26cf6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157566"
---
# <a name="worker-archetype"></a>Archétype Worker

Les classes qui se conforment aux archétype de *travail* fournissent le code pour traiter les éléments de travail mis en file d’attente sur un pool de threads.

**Implémentation**

Pour implémenter une classe conforme à ce archétype, la classe doit fournir les fonctionnalités suivantes :

|Méthode|Description|
|------------|-----------------|
|[Initialiser](#initialize)|Appelé pour initialiser l’objet Worker avant que toutes les demandes soient passées à [Execute](#execute).|
|[Execute](#execute)|Appelé pour traiter un élément de travail.|
|[Terminer](#terminate).|Appelé pour désinitialiser l’objet Worker une fois que toutes les demandes ont été passées à [Execute](#execute).|

|Typedef|Description|
|-------------|-----------------|
|[RequestType](#requesttype)|Typedef pour le type d’élément de travail qui peut être traité par la classe Worker.|

Une classe *Worker* classique ressemble à ceci :

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Implémentations existantes**

Ces classes sont conformes à ce archétype :

|Classe|Description|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Reçoit des demandes du pool de threads et les transmet à un objet de travail créé et détruit pour chaque requête.|

**Utilisation**

Ces paramètres de modèle s’attendent à ce que la classe soit conforme à ce archétype :

|Nom du paramètre|Utilisée par|
|--------------------|-------------|
|*Worker*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Worker*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="workerarchetypeexecute"></a><a name="execute"></a> WorkerArchetype :: Execute

Appelé pour traiter un élément de travail.

```cpp
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Paramètres

*requête*<br/>
Élément de travail à traiter. L’élément de travail est du même type que `RequestType` .

*pvWorkerParam*<br/>
Paramètre personnalisé compréhensible par la classe Worker. Également passé à `WorkerArchetype::Initialize` et `Terminate` .

*pOverlapped*<br/>
Pointeur vers la structure [OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) utilisée pour créer la file d’attente sur laquelle les éléments de travail ont été mis en file d’attente.

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a> WorkerArchetype :: Initialize

Appelé pour initialiser l’objet Worker avant que toutes les demandes soient passées à `WorkerArchetype::Execute` .

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Paramètres

*pvParam*<br/>
Paramètre personnalisé compréhensible par la classe Worker. Également passé à `WorkerArchetype::Terminate` et `WorkerArchetype::Execute` .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a> WorkerArchetype :: RequestType

Typedef pour le type d’élément de travail qui peut être traité par la classe Worker.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Notes

Ce type doit être utilisé comme premier paramètre de `WorkerArchetype::Execute` et doit pouvoir être casté vers et à partir d’un ULONG_PTR.

## <a name="workerarchetypeterminate"></a><a name="terminate"></a> WorkerArchetype :: Terminate

Appelé pour désinitialiser l’objet Worker une fois que toutes les demandes ont été passées à `WorkerArchetype::Execute` ).

```cpp
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Paramètres

*pvParam*<br/>
Paramètre personnalisé compréhensible par la classe Worker. Également passé à `WorkerArchetype::Initialize` et `WorkerArchetype::Execute` .

## <a name="see-also"></a>Voir aussi

[Concepts](../../atl/active-template-library-atl-concepts.md)<br/>
[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
