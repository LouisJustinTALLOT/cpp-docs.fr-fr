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
ms.openlocfilehash: 7cb815c4f7dc5ad09e8d352abc3f3375b8d9e205
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368105"
---
# <a name="itopologynode-structure"></a>ITopologyNode, structure

Interface avec un nœud de topologie, comme défini par le gestionnaire des ressources. Un nœud contient une ou plusieurs ressources d'exécution.

## <a name="syntax"></a>Syntaxe

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Retourne le nombre de ressources d’exécution regroupées sous ce nœud.|
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Retourne la première ressource d’exécution regroupée sous ce nœud dans l’ordre de recensement.|
|[ITopologyNode::GetId](#getid)|Retourne l’identifiant unique du gestionnaire de ressources pour ce nœud.|
|[ITopologyNode::GetNext](#getnext)|Retourne une interface au prochain nœud topologique dans l’ordre d’énumération.|
|[ITopologyNode::GetNumaNode](#getnumanode)|Retourne le numéro de nœud NUMA attribué par Windows auquel appartient ce nœud Resource Maanger.|

## <a name="remarks"></a>Notes

Cette interface est généralement utilisée pour marcher la topologie du système tel qu’observé par le gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ITopologyNode`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>ITopologyNode::GetExecutionResourceCount Méthode

Retourne le nombre de ressources d’exécution regroupées sous ce nœud.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de ressources d’exécution regroupées sous ce nœud.

## <a name="itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>ITopologyNode::GetFirstExecutionResource Méthode

Retourne la première ressource d’exécution regroupée sous ce nœud dans l’ordre de recensement.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Valeur de retour

La première ressource d’exécution regroupée sous ce nœud dans l’ordre d’énumération.

## <a name="itopologynodegetid-method"></a><a name="getid"></a>ITopologyNode::GetId Méthode

Retourne l’identifiant unique du gestionnaire de ressources pour ce nœud.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

L’identifiant unique du gestionnaire des ressources pour ce nœud.

### <a name="remarks"></a>Notes

Le Concurrency Runtime représente des fils matériels sur le système en groupes de nœuds de processeur. Les nœuds sont généralement dérivés de la topologie matérielle du système. Par exemple, tous les processeurs sur une prise spécifique ou un nœud NUMA spécifique peuvent appartenir au même nœud de processeur. Le gestionnaire de ressources attribue des identifiants `0` uniques à `nodeCount - 1`ces `nodeCount` nœuds en commençant par jusqu’à et y compris, où représente le nombre total de nœuds processeur sur le système.

Le nombre de nœuds peut être obtenu à partir de la fonction [GetProcessorNodeCount](concurrency-namespace-functions.md).

## <a name="itopologynodegetnext-method"></a><a name="getnext"></a>ITopologyNode::GetNext Méthode

Retourne une interface au prochain nœud topologique dans l’ordre d’énumération.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Une interface au nœud suivant dans l’ordre d’énumération. S’il n’y a plus de nœuds dans l’ordre `NULL`d’énumération de la topologie du système, cette méthode retournera la valeur.

## <a name="itopologynodegetnumanode-method"></a><a name="getnumanode"></a>ITopologyNode::GetNumaNode Méthode

Retourne le numéro de nœud NUMA attribué par Windows auquel appartient ce nœud Resource Maanger.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Le numéro de nœud NUMA attribué par Windows à laquelle appartient ce nœud Resource Manager.

### <a name="remarks"></a>Notes

Un proxy de fil fonctionnant sur une racine de processeur virtuel appartenant à ce nœud aura affinité au moins le niveau de nœud NUMA pour le nœud NUMA retourné par cette méthode.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
