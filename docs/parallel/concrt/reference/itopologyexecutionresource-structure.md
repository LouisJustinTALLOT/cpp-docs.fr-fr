---
title: ITopologyExecutionResource, structure
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: 82193a9b592cded96f3726cbabd6cf646eaa27c8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140070"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource, structure

Interface avec une ressource d'exécution tel que défini par le Gestionnaire de ressources.

## <a name="syntax"></a>Syntaxe

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[Itopologyexecutionresource, :: GetId](#getid)|Retourne l’identificateur unique de la Gestionnaire des ressources pour cette ressource d’exécution.|
|[Itopologyexecutionresource, :: GetNext](#getnext)|Retourne une interface à la ressource d’exécution suivante dans l’ordre de l’énumération.|

## <a name="remarks"></a>Notes

Cette interface est généralement utilisée pour parcourir la topologie du système telle qu’elle est observée par le Gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ITopologyExecutionResource`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="getid"></a>Itopologyexecutionresource, :: GetId, méthode

Retourne l’identificateur unique de la Gestionnaire des ressources pour cette ressource d’exécution.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur unique de la Gestionnaire des ressources pour cette ressource d’exécution.

## <a name="getnext"></a>Itopologyexecutionresource, :: GetNext, méthode

Retourne une interface à la ressource d’exécution suivante dans l’ordre de l’énumération.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Interface à la ressource d’exécution suivante dans l’ordre d’énumération. S’il n’y a plus de nœuds dans l’ordre d’énumération du nœud auquel cette ressource d’exécution appartient, cette méthode retourne la valeur `NULL`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
