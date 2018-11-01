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
ms.openlocfilehash: fa4d8978cbdb5cab36367138ffb607a722b6b91a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631073"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource, structure

Interface avec une ressource d'exécution tel que défini par le Gestionnaire de ressources.

## <a name="syntax"></a>Syntaxe

```
struct ITopologyExecutionResource;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ITopologyExecutionResource::GetId](#getid)|Retourne l’identificateur unique du Gestionnaire de ressources pour cette ressource d’exécution.|
|[ITopologyExecutionResource::GetNext](#getnext)|Retourne une interface pour la ressource de l’exécution suivante dans l’ordre d’énumération.|

## <a name="remarks"></a>Notes

Cette interface est généralement utilisée pour parcourir la topologie du système comme observée par le Gestionnaire de ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ITopologyExecutionResource`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrtrm.h

**Espace de noms :** concurrency

##  <a name="getid"></a>  Itopologyexecutionresource::GetId, méthode

Retourne l’identificateur unique du Gestionnaire de ressources pour cette ressource d’exécution.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur unique du Gestionnaire de ressources pour cette ressource d’exécution.

##  <a name="getnext"></a>  Itopologyexecutionresource::GetNext, méthode

Retourne une interface pour la ressource de l’exécution suivante dans l’ordre d’énumération.

```
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Une interface pour la ressource de l’exécution suivante dans l’ordre d’énumération. S’il n’y a pas d’autres nœuds dans l’ordre d’énumération du nœud auquel appartient cette ressource d’exécution, cette méthode retournera la valeur `NULL`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
