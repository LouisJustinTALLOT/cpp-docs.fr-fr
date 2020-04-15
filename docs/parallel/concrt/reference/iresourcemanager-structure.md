---
title: IResourceManager, structure
ms.date: 03/27/2019
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 15e27a586fc039791255c01a053f6a1109183f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368186"
---
# <a name="iresourcemanager-structure"></a>IResourceManager, structure

Interface avec un gestionnaire des ressources du runtime d'accès concurrentiel. Il s'agit de l'interface par laquelle les planificateurs communiquent avec le gestionnaire des ressources.

## <a name="syntax"></a>Syntaxe

```cpp
struct IResourceManager;
```

## <a name="members"></a>Membres

### <a name="public-enumerations"></a>Énumérations publiques

|Nom|Description|
|----------|-----------------|
|[IResourceManager::OSVersion](#osversion)|Type énuméré qui représente la version du système d'exploitation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IResourceManager::CreateNodeTopologie](#createnodetopology)|Présente uniquement dans les versions de déboçons du temps d’exécution, cette méthode est un crochet de test conçu pour faciliter les tests du gestionnaire de ressources sur différentes topologies matérielles, sans nécessiter de matériel réel correspondant à la configuration. Avec les constructions de détail de l’exécution, cette méthode reviendra sans effectuer aucune action.|
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Retourne le nombre de nœuds à la disposition du gestionnaire des ressources.|
|[IResourceManager::GetFirstNode](#getfirstnode)|Retourne le premier nœud dans l’ordre d’énumération tel que défini par le gestionnaire des ressources.|
|[IResourceManager::Référence](#reference)|Incréments le compte de référence sur l’instance gestionnaire des ressources.|
|[IResourceManager::RegisterScheduler](#registerscheduler)|Enregistre un planificateur auprès du gestionnaire des ressources. Une fois que le planificateur est inscrit, il `ISchedulerProxy` doit communiquer avec le gestionnaire de ressources à l’aide de l’interface qui est retournée.|
|[IResourceManager::Libération](#release)|Écarte le nombre de références sur l’instance du gestionnaire des ressources. Le gestionnaire des ressources est détruit `0`lorsque son nombre de références va à .|

## <a name="remarks"></a>Notes

Utilisez la fonction [CreateResourceManager](concurrency-namespace-functions.md) pour obtenir une interface avec l’instance singleton Resource Manager. La méthode incrémente un compte de référence sur le gestionnaire de ressources, et vous devez invoquer la méthode [IResourceManager::Release](#release) method to release the reference when you are done with Resource Manager. En règle générale, chaque planificateur que vous créez invoque cette méthode pendant la création, et publiera la référence au gestionnaire de ressources après sa fermeture.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IResourceManager`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a>IResourceManager::CreateNodeTopology Méthode

Présente uniquement dans les versions de déboçons du temps d’exécution, cette méthode est un crochet de test conçu pour faciliter les tests du gestionnaire de ressources sur différentes topologies matérielles, sans nécessiter de matériel réel correspondant à la configuration. Avec les constructions de détail de l’exécution, cette méthode reviendra sans effectuer aucune action.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Paramètres

*nodeCompte*<br/>
Le nombre de nœuds de processeur simulés.

*pCoreCompte*<br/>
Un tableau qui spécifie le nombre de cœurs sur chaque nœud.

*pNodeDistance*<br/>
Une matrice spécifiant la distance de nœud entre deux nœuds. Ce paramètre peut `NULL`avoir la valeur .

*pProcessorGroupes*<br/>
Un tableau qui spécifie le groupe de processeur auquel chaque nœud appartient.

### <a name="remarks"></a>Notes

[invalid_argument](../../../standard-library/invalid-argument-class.md) est jeté si `nodeCount` le paramètre a la valeur `0` `pCoreCount` a été `NULL`passé, ou si le paramètre a la valeur .

[invalid_operation](invalid-operation-class.md) est jeté si cette méthode est appelée alors que d’autres planificateurs existent dans le processus.

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a>IResourceManager::GetAvailableNodeCount Méthode

Retourne le nombre de nœuds à la disposition du gestionnaire des ressources.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de nœuds à la disposition du gestionnaire des ressources.

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a>IResourceManager::GetFirstNode Méthode

Retourne le premier nœud dans l’ordre d’énumération tel que défini par le gestionnaire des ressources.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Le premier nœud dans l’ordre d’énumération tel que défini par le gestionnaire des ressources.

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a>IResourceManager::OSVersion Énumération

Type énuméré qui représente la version du système d'exploitation.

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a>IResourceManager::Méthode de référence

Incréments le compte de référence sur l’instance gestionnaire des ressources.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de références qui en résulte.

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a>IResourceManager::RegisterScheduler Méthode

Enregistre un planificateur auprès du gestionnaire des ressources. Une fois que le planificateur est inscrit, il `ISchedulerProxy` doit communiquer avec le gestionnaire de ressources à l’aide de l’interface qui est retournée.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Paramètres

*pScheduler*<br/>
Une `IScheduler` interface à l’horaire à enregistrer.

*version*<br/>
La version de l’interface de communication que le planificateur utilise pour communiquer avec le gestionnaire des ressources. L’utilisation d’une version permet au gestionnaire de ressources de faire évoluer l’interface de communication tout en permettant aux planificateurs d’accéder à des fonctionnalités plus anciennes. Les planificateurs qui souhaitent utiliser les fonctionnalités de Resource Manager `CONCRT_RM_VERSION_1`présentes dans Visual Studio 2010 devraient utiliser la version .

### <a name="return-value"></a>Valeur de retour

L’interface `ISchedulerProxy` que le gestionnaire de ressources a associée à votre planificateur. Votre planificateur devrait utiliser cette interface pour communiquer avec Resource Manager à partir de ce moment.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour initier la communication avec le gestionnaire des ressources. La méthode `IScheduler` associe l’interface de `ISchedulerProxy` votre planificateur à une interface et vous la remet. Vous pouvez utiliser l’interface retournée pour demander des ressources d’exécution pour une utilisation par votre planificateur, ou pour vous abonner à des threads avec le gestionnaire de ressources. Le gestionnaire des ressources utilisera les éléments stratégiques de la politique de planificateur retournée par [l’IScheduler : : «GetPolicy](ischeduler-structure.md#getpolicy) méthode pour déterminer quel type de threads le planificateur devra exécuter le travail. Si `SchedulerKind` votre clé de `UmsThreadDefault` stratégie a la valeur et que `UmsThreadDefault`la `IScheduler` valeur est relue `IUMSScheduler` de la stratégie comme la valeur, l’interface transmise à la méthode doit être une interface.

La méthode prévoit `invalid_argument` une exception `pScheduler` si `NULL` le paramètre `version` a la valeur ou si le paramètre n’est pas une version valide pour l’interface de communication.

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a>IResourceManager::Méthode de libération

Écarte le nombre de références sur l’instance du gestionnaire des ressources. Le gestionnaire des ressources est détruit `0`lorsque son nombre de références va à .

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de références qui en résulte.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[ISchedulerProxy, structure](ischedulerproxy-structure.md)<br/>
[IScheduler, structure](ischeduler-structure.md)
