---
title: Classe CNonStatelessWorker
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
ms.openlocfilehash: f3604f95c8217c7407c100671265140bbadbab78
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326734"
---
# <a name="cnonstatelessworker-class"></a>Classe CNonStatelessWorker

Reçoit les demandes d’un pool de threads et les transmet à un objet de travailleur qui est créé et détruit sur chaque demande.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>Paramètres

*Travailleur*<br/>
Une classe de fil de travailleur conforme à [l’archétype du travailleur](../../atl/reference/worker-archetype.md) approprié pour le traitement des demandes en file d’attente sur [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|Mise en œuvre [de WorkerArchetype::RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CNonStatelessWorker::Execute](#execute)|Mise en œuvre [de WorkerArchetype:Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker::Initialize](#initialize)|Mise en œuvre [de WorkerArchetype:Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker::Terminate](#terminate)|Mise en œuvre [de WorkerArchetype::Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Notes

Cette classe est un fil de travail simple pour une utilisation avec [CThreadPool](../../atl/reference/cthreadpool-class.md). Cette classe ne fournit pas de capacités de traitement des demandes de ses propres. Au lieu de cela, il instantanéia un exemple de *travailleur* par demande et délègue la mise en œuvre de ses méthodes à cette instance.

L’avantage de cette classe est qu’elle fournit un moyen pratique de changer le modèle d’état pour les classes existantes de fil de travailleur. `CThreadPool`créera un seul travailleur pour la durée de vie du fil, donc si la classe de travailleurs détient l’état, il tiendra à travers plusieurs demandes. En enveloppant `CNonStatelessWorker` simplement cette classe `CThreadPool`dans le modèle avant de l’utiliser avec , la durée de vie du travailleur et l’état qu’il détient est limitée à une seule demande.

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a>CNonStatelessWorker::Execute

Mise en œuvre [de WorkerArchetype:Execute](worker-archetype.md#execute).

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Notes

Cette méthode crée une instance de la classe *de travailleur* sur la pile et appelle [Initialize](worker-archetype.md#initialize) sur cet objet. Si l’initialisation est réussie, cette méthode appelle également [Exécuter](worker-archetype.md#execute) et [terminer](worker-archetype.md#terminate) sur le même objet.

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a>CNonStatelessWorker::Initialize

Mise en œuvre [de WorkerArchetype:Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours VRAI.

### <a name="remarks"></a>Notes

Cette classe ne fait aucune `Initialize`initialisation dans .

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a>CNonStatelessWorker::RequestType

Mise en œuvre [de WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Notes

Cette classe gère le même type d’élément de travail que la classe utilisée pour le paramètre du modèle *de travailleur.* Voir [CNonStatelessWorker Aperçu](../../atl/reference/cnonstatelessworker-class.md) pour plus de détails.

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a>CNonStatelessWorker::Terminate

Mise en œuvre [de WorkerArchetype::Terminate](worker-archetype.md#terminate).

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Notes

Cette classe ne fait pas `Terminate`de nettoyage en .

## <a name="see-also"></a>Voir aussi

[Classe CThreadPool](../../atl/reference/cthreadpool-class.md)<br/>
[Archetype de travailleur](../../atl/reference/worker-archetype.md)<br/>
[Classes](../../atl/reference/atl-classes.md)
