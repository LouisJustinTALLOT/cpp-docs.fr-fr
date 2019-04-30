---
title: auto_partitioner, classe
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: 2d8bbb8e8af17dd19953487c47e5fd40343fe349
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391086"
---
# <a name="autopartitioner-class"></a>auto_partitioner, classe

La classe `auto_partitioner` représente la méthode par défaut que `parallel_for`, `parallel_for_each` et `parallel_transform` utilisent pour partitionner la plage au sein de laquelle ils itèrent. Cette méthode de partitionnement utilise un vol de plage pour équilibrer la charge et annuler par itération.

## <a name="syntax"></a>Syntaxe

```
class auto_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[auto_partitioner](#ctor)|Construit un objet `auto_partitioner`.|
|[~auto_partitioner Destructor](#dtor)|Détruit un objet `auto_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`auto_partitioner`

## <a name="requirements"></a>Configuration requise

**En-tête :** ppl.h

**Espace de noms :** concurrency

##  <a name="dtor"></a> ~auto_partitioner

Détruit un objet `auto_partitioner`.

```
~auto_partitioner();
```

##  <a name="ctor"></a> auto_partitioner

Construit un objet `auto_partitioner`.

```
auto_partitioner();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
