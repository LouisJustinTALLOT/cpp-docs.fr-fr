---
description: 'En savoir plus sur : IResourceManager, structure'
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
ms.openlocfilehash: 1577d20f7a54bbf2f5613cd47afa22ead36b3630
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334474"
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
|[IResourceManager :: OSVersion](#osversion)|Type énuméré qui représente la version du système d'exploitation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IResourceManager :: CreateNodeTopology](#createnodetopology)|Présent uniquement dans les versions Debug du runtime, cette méthode est un raccordement de test conçu pour faciliter le test de l’Gestionnaire des ressources sur différentes topologies matérielles, sans nécessiter de matériel réel correspondant à la configuration. Avec les versions commerciales du runtime, cette méthode est retournée sans effectuer aucune action.|
|[IResourceManager :: GetAvailableNodeCount](#getavailablenodecount)|Retourne le nombre de nœuds disponibles pour le Gestionnaire des ressources.|
|[IResourceManager :: GetFirstNode](#getfirstnode)|Retourne le premier nœud dans l’ordre d’énumération tel que défini par le Gestionnaire des ressources.|
|[IResourceManager :: Reference](#reference)|Incrémente le décompte de références sur l’instance Gestionnaire des ressources.|
|[IResourceManager :: RegisterScheduler](#registerscheduler)|Inscrit un planificateur avec le Gestionnaire des ressources. Une fois que le planificateur est inscrit, il doit communiquer avec le Gestionnaire des ressources à l’aide de l' `ISchedulerProxy` interface retournée.|
|[IResourceManager :: Release](#release)|Décrémente le décompte de références sur l’instance de Gestionnaire des ressources. Le Gestionnaire des ressources est détruit lorsque son décompte de références atteint `0` .|

## <a name="remarks"></a>Notes

Utilisez la fonction [CreateResourceManager,](concurrency-namespace-functions.md) pour obtenir une interface pour l’instance de gestionnaire des ressources Singleton. La méthode incrémente un décompte de références sur le Gestionnaire des ressources, et vous devez appeler la méthode [IResourceManager :: Release](#release) pour libérer la référence lorsque vous avez terminé avec Gestionnaire des ressources. En règle générale, chaque planificateur que vous créez appellera cette méthode lors de la création et libère la référence au Gestionnaire des ressources une fois qu’il s’est arrêté.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IResourceManager`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrence

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a> IResourceManager :: CreateNodeTopology, méthode

Présent uniquement dans les versions Debug du runtime, cette méthode est un raccordement de test conçu pour faciliter le test de l’Gestionnaire des ressources sur différentes topologies matérielles, sans nécessiter de matériel réel correspondant à la configuration. Avec les versions commerciales du runtime, cette méthode est retournée sans effectuer aucune action.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Paramètres

*nodeCount*<br/>
Nombre de nœuds de processeur qui sont simulés.

*pCoreCount*<br/>
Tableau qui spécifie le nombre de cœurs sur chaque nœud.

*pNodeDistance*<br/>
Matrice spécifiant la distance entre deux nœuds. Ce paramètre peut avoir la valeur `NULL` .

*pProcessorGroups*<br/>
Tableau qui spécifie le groupe de processeurs auquel chaque nœud appartient.

### <a name="remarks"></a>Notes

[invalid_argument](../../../standard-library/invalid-argument-class.md) est levée si la valeur du paramètre a `nodeCount` `0` été passée ou si le paramètre `pCoreCount` a la valeur `NULL` .

[invalid_operation](invalid-operation-class.md) est levée si cette méthode est appelée alors que d’autres planificateurs existent dans le processus.

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a> IResourceManager :: GetAvailableNodeCount, méthode

Retourne le nombre de nœuds disponibles pour le Gestionnaire des ressources.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de nœuds disponibles pour le Gestionnaire des ressources.

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a> IResourceManager :: GetFirstNode, méthode

Retourne le premier nœud dans l’ordre d’énumération tel que défini par le Gestionnaire des ressources.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Premier nœud de l’ordre d’énumération défini par l’Gestionnaire des ressources.

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a> IResourceManager :: OSVersion, énumération

Type énuméré qui représente la version du système d'exploitation.

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a> IResourceManager :: Reference, méthode

Incrémente le décompte de références sur l’instance Gestionnaire des ressources.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Le décompte de références résultant.

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a> IResourceManager :: RegisterScheduler, méthode

Inscrit un planificateur avec le Gestionnaire des ressources. Une fois que le planificateur est inscrit, il doit communiquer avec le Gestionnaire des ressources à l’aide de l' `ISchedulerProxy` interface retournée.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Paramètres

*pScheduler*<br/>
`IScheduler`Interface au planificateur à inscrire.

*version*<br/>
Version de l’interface de communication que le planificateur utilise pour communiquer avec le Gestionnaire des ressources. L’utilisation d’une version permet à l’Gestionnaire des ressources de faire évoluer l’interface de communication tout en autorisant les planificateurs à obtenir l’accès à des fonctionnalités plus anciennes. Les planificateurs qui souhaitent utiliser Gestionnaire des ressources fonctionnalités présentes dans Visual Studio 2010 doivent utiliser la version `CONCRT_RM_VERSION_1` .

### <a name="return-value"></a>Valeur renvoyée

L' `ISchedulerProxy` interface que le gestionnaire des ressources a associé à votre planificateur. Votre planificateur doit utiliser cette interface pour communiquer avec Gestionnaire des ressources à partir de ce point.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour initier la communication avec le Gestionnaire des ressources. La méthode associe l' `IScheduler` interface de votre planificateur à une `ISchedulerProxy` interface et vous le remet. Vous pouvez utiliser l’interface retournée pour demander des ressources d’exécution à votre planificateur, ou pour abonner des threads à l’aide de l’Gestionnaire des ressources. Le Gestionnaire des ressources utilisera les éléments de stratégie de la stratégie du planificateur retournée par la méthode [iScheduler :: GetPolicy](ischeduler-structure.md#getpolicy) pour déterminer le type de threads dont le planificateur aura besoin pour exécuter le travail. Si votre `SchedulerKind` clé de stratégie a la valeur `UmsThreadDefault` et que la valeur est lue en dehors de la stratégie comme valeur `UmsThreadDefault` , l' `IScheduler` interface transmise à la méthode doit être une `IUMSScheduler` interface.

La méthode lève une `invalid_argument` exception si le paramètre `pScheduler` a la valeur `NULL` ou si le paramètre `version` n’est pas une version valide pour l’interface de communication.

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a> IResourceManager :: Release, méthode

Décrémente le décompte de références sur l’instance de Gestionnaire des ressources. Le Gestionnaire des ressources est détruit lorsque son décompte de références atteint `0` .

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Le décompte de références résultant.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[ISchedulerProxy, structure](ischedulerproxy-structure.md)<br/>
[IScheduler, structure](ischeduler-structure.md)
