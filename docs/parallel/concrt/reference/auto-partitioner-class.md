---
description: 'En savoir plus sur : classe auto_partitioner'
title: auto_partitioner, classe
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: d8e099c7a3132ce89f81df65d7e18a5c6c673697
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172256"
---
# <a name="auto_partitioner-class"></a>auto_partitioner, classe

La classe `auto_partitioner` représente la méthode par défaut que `parallel_for`, `parallel_for_each` et `parallel_transform` utilisent pour partitionner la plage au sein de laquelle ils itèrent. Cette méthode de partitionnement utilise le vol de plage pour l’équilibrage de charge et l’annulation par itération.

## <a name="syntax"></a>Syntaxe

```cpp
class auto_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[auto_partitioner](#ctor)|Construit un objet `auto_partitioner`.|
|[Destructeur ~ auto_partitioner](#dtor)|Détruit un objet `auto_partitioner` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`auto_partitioner`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrence

## <a name="auto_partitioner"></a><a name="dtor"></a> ~ auto_partitioner

Détruit un objet `auto_partitioner` .

```cpp
~auto_partitioner();
```

## <a name="auto_partitioner"></a><a name="ctor"></a> auto_partitioner

Construit un objet `auto_partitioner`.

```cpp
auto_partitioner();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
