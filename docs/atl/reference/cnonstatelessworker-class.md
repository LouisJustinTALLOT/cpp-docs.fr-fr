---
title: Classe de CNonStatelessWorker | Documents Microsoft
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
ms.openlocfilehash: de03ded4bc0021a8884f608d10368e3d09c11cf8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359605"
---
# <a name="cnonstatelessworker-class"></a>Classe de CNonStatelessWorker
Reçoit des demandes à partir d’un pool de threads et les transmet à un objet de travail qui est créé et détruit à chaque demande.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Worker>  
class CNonStatelessWorker
```  
  
#### <a name="parameters"></a>Paramètres  
 *Processus de travail*  
 Une classe de thread de travail conformes à la [archétype de travail](../../atl/reference/worker-archetype.md) approprié pour la gestion des demandes en attente sur [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
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
 Cette classe est un thread de travail simple pour une utilisation avec [CThreadPool](../../atl/reference/cthreadpool-class.md). Cette classe ne fournit pas toutes les capacités de gestion des demandes qui lui sont propres. Au lieu de cela, il instancie une instance de *travail* par demande et délègue l’implémentation de ses méthodes à cette instance.  
  
 L’avantage de cette classe est qu’il fournit un moyen pratique de modifier le modèle d’état pour les classes de thread de travail existant. `CThreadPool` Crée un seul processus de travail pour la durée de vie du thread, donc si la classe de travail possède un état, il contiendra il entre plusieurs demandes. En encapsulant simplement cette classe dans le `CNonStatelessWorker` modèle avant de l’utiliser avec `CThreadPool`, la durée de vie du processus de travail et de l’état, sa valeur est est limité à une demande unique.  
  
## <a name="requirements"></a>Spécifications  
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
 Cette méthode crée une instance de la *travail* classe sur la pile et les appels [initialiser](worker-archetype.md#initialize) sur cet objet. Si l’initialisation réussit, cette méthode appelle également [Execute](worker-archetype.md#execute) et [Terminate](worker-archetype.md#terminate) sur le même objet.  

  
##  <a name="initialize"></a>  CNonStatelessWorker::Initialize  
 Implémentation de [WorkerArchetype::Initialize](worker-archetype.md#initialize).  
  
```
BOOL Initialize(void* /* pvParam */) throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours la valeur TRUE.  
  
### <a name="remarks"></a>Notes  
 Cette classe ne toute initialisation `Initialize`.  
  
##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType  
 Implémentation de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).  
  
```
typedef Worker::RequestType RequestType;
```  
  
### <a name="remarks"></a>Notes  
 Cette classe gère le même type d’élément de travail que la classe utilisée pour le *travail* paramètre de modèle. Consultez [vue d’ensemble de CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md) pour plus d’informations.  
  
##  <a name="terminate"></a>  CNonStatelessWorker::Terminate  
 Implémentation de [WorkerArchetype::Terminate](worker-archetype.md#terminate).  
  
```
void Terminate(void* /* pvParam */) throw();
```  
  
### <a name="remarks"></a>Notes  
 Cette classe n’effectue un nettoyage `Terminate`.  
  
## <a name="see-also"></a>Voir aussi  
 [CThreadPool (classe)](../../atl/reference/cthreadpool-class.md)   
 [Archétype de travail](../../atl/reference/worker-archetype.md)   
 [Classes](../../atl/reference/atl-classes.md)
