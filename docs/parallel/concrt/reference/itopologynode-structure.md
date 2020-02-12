---
title: ITopologyNode, structure
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 1b4cb6a856d6da7b8eee7f9cba1ad51e375c024d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140061"
---
# <a name="itopologynode-structure"></a>ITopologyNode, structure

Interface avec un nœud de topologie, comme défini par le gestionnaire des ressources. Un nœud contient une ou plusieurs ressources d'exécution.

## <a name="syntax"></a>Syntaxe

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[ITopologyNode :: GetExecutionResourceCount](#getexecutionresourcecount)|Retourne le nombre de ressources d’exécution regroupées sous ce nœud.|
|[ITopologyNode :: GetFirstExecutionResource](#getfirstexecutionresource)|Retourne la première ressource d’exécution regroupée sous ce nœud dans l’ordre d’énumération.|
|[ITopologyNode :: GetId](#getid)|Retourne l’identificateur unique de l’Gestionnaire des ressources pour ce nœud.|
|[ITopologyNode :: GetNext](#getnext)|Retourne une interface au nœud de topologie suivant dans l’ordre de l’énumération.|
|[ITopologyNode :: GetNumaNode](#getnumanode)|Retourne le numéro de nœud NUMA affecté par Windows auquel appartient ce nœud maanger de ressource.|

## <a name="remarks"></a>Notes

Cette interface est généralement utilisée pour parcourir la topologie du système telle qu’elle est observée par le Gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ITopologyNode`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="getexecutionresourcecount"></a>ITopologyNode :: GetExecutionResourceCount, méthode

Retourne le nombre de ressources d’exécution regroupées sous ce nœud.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Nombre de ressources d’exécution regroupées sous ce nœud.

## <a name="getfirstexecutionresource"></a>ITopologyNode :: GetFirstExecutionResource, méthode

Retourne la première ressource d’exécution regroupée sous ce nœud dans l’ordre d’énumération.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Première ressource d’exécution regroupée sous ce nœud dans l’ordre d’énumération.

## <a name="getid"></a>ITopologyNode :: GetId, méthode

Retourne l’identificateur unique de l’Gestionnaire des ressources pour ce nœud.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur unique du Gestionnaire des ressources pour ce nœud.

### <a name="remarks"></a>Notes

Le runtime d’accès concurrentiel représente les threads matériels sur le système dans des groupes de nœuds de processeur. Les nœuds sont généralement dérivés de la topologie matérielle du système. Par exemple, tous les processeurs sur un socket spécifique ou un nœud NUMA spécifique peuvent appartenir au même nœud de processeur. Le Gestionnaire des ressources assigne des identificateurs uniques à ces nœuds en commençant par `0` jusqu’à `nodeCount - 1`, où `nodeCount` représente le nombre total de nœuds de processeur sur le système.

Le nombre de nœuds peut être obtenu à partir de la fonction [GetProcessorNodeCount,](concurrency-namespace-functions.md).

## <a name="getnext"></a>ITopologyNode :: GetNext, méthode

Retourne une interface au nœud de topologie suivant dans l’ordre de l’énumération.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Interface vers le nœud suivant dans l’ordre d’énumération. S’il n’y a plus de nœuds dans l’ordre d’énumération de la topologie du système, cette méthode retourne la valeur `NULL`.

## <a name="getnumanode"></a>ITopologyNode :: GetNumaNode, méthode

Retourne le numéro de nœud NUMA affecté par Windows auquel appartient ce nœud maanger de ressource.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Numéro de nœud NUMA affecté à Windows auquel appartient ce nœud de Gestionnaire des ressources.

### <a name="remarks"></a>Notes

Un proxy de thread s’exécutant sur une racine de processeur virtuel appartenant à ce nœud aura une affinité avec au moins le niveau de nœud NUMA pour le nœud NUMA retourné par cette méthode.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
