---
title: Cnonstatelessworker, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
dev_langs:
- C++
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb3b6411e9ce34ba0196d25c8a63f3f066d78549
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765120"
---
# <a name="cnonstatelessworker-class"></a>Cnonstatelessworker, classe

Reçoit des demandes à partir d’un pool de threads et les transmet à un objet de travail qui est créé et détruit dans chaque demande.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class Worker>  
class CNonStatelessWorker
```

#### <a name="parameters"></a>Paramètres

*Travail*  
Une classe de thread de travail correspondant à la [archétype de travail](../../atl/reference/worker-archetype.md) adaptées à la gestion des demandes en file d’attente sur [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|Implémentation de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CNonStatelessWorker::Execute](#execute)|Implémentation de [WorkerArchetype::Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker::Initialize](#initialize)|Implémentation de [WorkerArchetype::Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker::Terminate](#terminate)|Implémentation de [WorkerArchetype::Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Notes

Cette classe est un thread de travail simple pour une utilisation avec [CThreadPool](../../atl/reference/cthreadpool-class.md). Cette classe ne fournit aucune capacité de gestion des demandes de son propre. Au lieu de cela, il instancie une instance de *Worker* par demande et délègue l’implémentation de ses méthodes à cette instance.

L’avantage de cette classe est qu’il fournit un moyen pratique pour modifier le modèle d’état pour les classes de thread de travail existantes. `CThreadPool` Crée un travail unique pour la durée de vie du thread, donc si la classe de travail possède un état, il contiendra il entre plusieurs demandes. En encapsulant simplement cette classe dans le `CNonStatelessWorker` modèle avant de l’utiliser avec `CThreadPool`, la durée de vie du processus de travail et de l’état, sa valeur est est limité à une seule requête.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

##  <a name="execute"></a>  CNonStatelessWorker::Execute

Implémentation de [WorkerArchetype::Execute](worker-archetype.md#execute).  

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Notes

Cette méthode crée une instance de la *Worker* classe sur la pile et les appels [initialiser](worker-archetype.md#initialize) sur cet objet. Si l’initialisation réussite, cette méthode appelle également [Execute](worker-archetype.md#execute) et [Terminate](worker-archetype.md#terminate) sur le même objet.  

##  <a name="initialize"></a>  CNonStatelessWorker::Initialize

Implémentation de [WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie toujours TRUE.

### <a name="remarks"></a>Notes

Cette classe n’effectue pas de toute initialisation `Initialize`.

##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType

Implémentation de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Notes

Cette classe gère le même type d’élément de travail que la classe utilisée pour le *Worker* paramètre de modèle. Consultez [vue d’ensemble de CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md) pour plus d’informations.

##  <a name="terminate"></a>  CNonStatelessWorker::Terminate

Implémentation de [WorkerArchetype::Terminate](worker-archetype.md#terminate).

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Notes

Cette classe n’effectue pas de toute opération de nettoyage `Terminate`.

## <a name="see-also"></a>Voir aussi

[CThreadPool, classe](../../atl/reference/cthreadpool-class.md)   
[Archétype de travail](../../atl/reference/worker-archetype.md)   
[Classes](../../atl/reference/atl-classes.md)
