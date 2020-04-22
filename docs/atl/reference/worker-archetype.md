---
title: Archetype de travailleur
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: c9ed9b30b94a8debe133bc213c12063750bfb15a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747344"
---
# <a name="worker-archetype"></a>Archetype de travailleur

Les classes conformes à l’archétype *du travailleur* fournissent le code pour traiter les éléments de travail en file d’attente sur un pool de threads.

**Implémentation**

Pour mettre en œuvre une classe conforme à cet archétype, la classe doit fournir les caractéristiques suivantes :

|Méthode|Description|
|------------|-----------------|
|[Initialiser](#initialize)|Appelé à initialiser l’objet du travailleur avant que toute demande ne soit transmise à [Exécuter](#execute).|
|[Exécuter](#execute)|Appelé à traiter un élément de travail.|
|[Terminate](#terminate)|Appelé à uninitialiser l’objet du travailleur après que toutes les demandes ont été transmises à [Exécuter](#execute).|

|Typedef|Description|
|-------------|-----------------|
|[DemandeType](#requesttype)|Un typedef pour le type d’élément de travail qui peut être traité par la classe des travailleurs.|

Une classe de *travailleurs* typique ressemble à ceci :

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Mises en œuvre existantes**

Ces classes sont conformes à cet archétype :

|Classe|Description|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Reçoit les demandes du pool de threads et les transmet à un objet de travailleur qui est créé et détruit pour chaque demande.|

**Utilisation**

Ces paramètres de modèle s’attendent à ce que la classe se conforme à cet archétype :

|Nom du paramètre|Utilisée par|
|--------------------|-------------|
|*Travailleur*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Travailleur*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="workerarchetypeexecute"></a><a name="execute"></a>WorkerArchetype::Exécuter

Appelé à traiter un élément de travail.

```cpp
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Paramètres

*requête*<br/>
L’élément de travail à traiter. L’élément de travail est `RequestType`du même type que .

*pvWorkerParam*<br/>
Un paramètre personnalisé compris par la classe des travailleurs. Également passé `WorkerArchetype::Initialize` `Terminate`à et .

*pOverlapped*<br/>
Un pointeur de la structure [OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) utilisé pour créer la file d’attente sur laquelle les éléments de travail ont été mis en file d’attente.

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a>WorkerArchetype::Initialize

Appelé à initialiser l’objet du `WorkerArchetype::Execute`travailleur avant que toute demande ne soit transmise à .

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Paramètres

*pvParam pvParam*<br/>
Un paramètre personnalisé compris par la classe des travailleurs. Également passé `WorkerArchetype::Terminate` `WorkerArchetype::Execute`à et .

### <a name="return-value"></a>Valeur de retour

Retour VRAI sur le succès, FALSE sur l’échec.

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a>WorkerArchetype::RequestType

Un typedef pour le type d’élément de travail qui peut être traité par la classe des travailleurs.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Notes

Ce type doit être utilisé `WorkerArchetype::Execute` comme premier paramètre et doit être capable d’être jeté vers et à partir d’une ULONG_PTR.

## <a name="workerarchetypeterminate"></a><a name="terminate"></a>WorkerArchetype::Terminate

Appelé à uninitialiser l’objet du travailleur `WorkerArchetype::Execute`après que toutes les demandes ont été transmises à ).

```cpp
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Paramètres

*pvParam pvParam*<br/>
Un paramètre personnalisé compris par la classe des travailleurs. Également passé `WorkerArchetype::Initialize` `WorkerArchetype::Execute`à et .

## <a name="see-also"></a>Voir aussi

[Concepts](../../atl/active-template-library-atl-concepts.md)<br/>
[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
