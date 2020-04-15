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
ms.openlocfilehash: 2c9221cab1ac2d48bd099a769188e4bee797823c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368146"
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
|[ITopologyExecutionResource::GetId](#getid)|Retourne l’identifiant unique du gestionnaire de ressources pour cette ressource d’exécution.|
|[ITopologyExecutionResource::GetNext](#getnext)|Retourne une interface à la prochaine ressource d’exécution dans l’ordre de recensement.|

## <a name="remarks"></a>Notes

Cette interface est généralement utilisée pour marcher la topologie du système tel qu’observé par le gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ITopologyExecutionResource`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="itopologyexecutionresourcegetid-method"></a><a name="getid"></a>ITopologyExecutionResource::GetId Méthode

Retourne l’identifiant unique du gestionnaire de ressources pour cette ressource d’exécution.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

L’identifiant unique du gestionnaire des ressources pour cette ressource d’exécution.

## <a name="itopologyexecutionresourcegetnext-method"></a><a name="getnext"></a>ITopologyExecutionResource::GetNext Méthode

Retourne une interface à la prochaine ressource d’exécution dans l’ordre de recensement.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Une interface à la prochaine ressource d’exécution dans l’ordre d’énumération. S’il n’y a plus de nœuds dans l’ordre d’énumération `NULL`du nœud auquel appartient cette ressource d’exécution, cette méthode rendra la valeur .

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
