---
description: 'En savoir plus sur : structure Itopologyexecutionresource,'
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
ms.openlocfilehash: c2567cf9e34e0b27308e331056d5e0dbc99b2779
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334378"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource, structure

Interface avec une ressource d'exécution tel que défini par le Gestionnaire de ressources.

## <a name="syntax"></a>Syntaxe

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Itopologyexecutionresource, :: GetId](#getid)|Retourne l’identificateur unique de la Gestionnaire des ressources pour cette ressource d’exécution.|
|[Itopologyexecutionresource, :: GetNext](#getnext)|Retourne une interface à la ressource d’exécution suivante dans l’ordre de l’énumération.|

## <a name="remarks"></a>Notes

Cette interface est généralement utilisée pour parcourir la topologie du système telle qu’elle est observée par le Gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ITopologyExecutionResource`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrence

## <a name="itopologyexecutionresourcegetid-method"></a><a name="getid"></a> Itopologyexecutionresource, :: GetId, méthode

Retourne l’identificateur unique de la Gestionnaire des ressources pour cette ressource d’exécution.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur unique de la Gestionnaire des ressources pour cette ressource d’exécution.

## <a name="itopologyexecutionresourcegetnext-method"></a><a name="getnext"></a> Itopologyexecutionresource, :: GetNext, méthode

Retourne une interface à la ressource d’exécution suivante dans l’ordre de l’énumération.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Interface à la ressource d’exécution suivante dans l’ordre d’énumération. S’il n’y a plus de nœuds dans l’ordre d’énumération du nœud auquel cette ressource d’exécution appartient, cette méthode retourne la valeur `NULL` .

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
