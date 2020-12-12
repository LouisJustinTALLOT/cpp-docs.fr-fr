---
description: 'En savoir plus sur : classe CNonStatelessWorker'
title: CNonStatelessWorker, classe
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: 68457c9594bfaf4d8dd53acd80d7997355c3a3f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141425"
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker, classe

Reçoit des demandes d’un pool de threads et les passe à un objet de travail créé et détruit à chaque requête.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>Paramètres

*Worker*<br/>
Une classe de thread de travail conforme aux [archétype de travail](../../atl/reference/worker-archetype.md) convenant pour gérer les demandes en attente sur [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CNonStatelessWorker :: RequestType](#requesttype)|Implémentation de [WorkerArchetype :: RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CNonStatelessWorker :: Execute](#execute)|Implémentation de [WorkerArchetype :: Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker :: Initialize](#initialize)|Implémentation de [WorkerArchetype :: Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker :: Terminate](#terminate)|Implémentation de [WorkerArchetype :: Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Notes

Cette classe est un thread de travail simple à utiliser avec [CThreadPool](../../atl/reference/cthreadpool-class.md). Cette classe ne fournit pas de fonctionnalités de gestion des requêtes propres. Au lieu de cela, il instancie une instance de *Worker* par demande et délègue l’implémentation de ses méthodes à cette instance.

L’avantage de cette classe est qu’elle offre un moyen pratique de modifier le modèle d’État pour les classes de thread de travail existantes. `CThreadPool` crée un seul thread de travail pour la durée de vie du thread, donc si la classe Worker conserve l’État, elle le contiendra sur plusieurs demandes. En encapsulant simplement cette classe dans le `CNonStatelessWorker` modèle avant de l’utiliser avec `CThreadPool` , la durée de vie du thread de travail et l’État qu’il contient sont limités à une seule requête.

## <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a> CNonStatelessWorker :: Execute

Implémentation de [WorkerArchetype :: Execute](worker-archetype.md#execute).

```cpp
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Notes

Cette méthode crée une instance de la classe *Worker* sur la pile et appelle [Initialize](worker-archetype.md#initialize) sur cet objet. Si l’initialisation réussit, cette méthode appelle également [Execute](worker-archetype.md#execute) et [Terminate](worker-archetype.md#terminate) sur le même objet.

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a> CNonStatelessWorker :: Initialize

Implémentation de [WorkerArchetype :: Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

Cette classe n’effectue aucune initialisation dans `Initialize` .

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a> CNonStatelessWorker :: RequestType

Implémentation de [WorkerArchetype :: RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Notes

Cette classe gère le même type d’élément de travail que la classe utilisée pour le paramètre de modèle de *travail* . Pour plus d’informations, consultez [vue d’ensemble de CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md) .

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a> CNonStatelessWorker :: Terminate

Implémentation de [WorkerArchetype :: Terminate](worker-archetype.md#terminate).

```cpp
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Notes

Cette classe n’effectue aucun nettoyage dans `Terminate` .

## <a name="see-also"></a>Voir aussi

[CThreadPool (classe)](../../atl/reference/cthreadpool-class.md)<br/>
[Archétype Worker](../../atl/reference/worker-archetype.md)<br/>
[Classes](../../atl/reference/atl-classes.md)
