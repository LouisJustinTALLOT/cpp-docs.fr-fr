---
title: simple_partitioner, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
dev_langs:
- C++
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89114c96beb49c8f843ec8a04b08802632c61ca1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401509"
---
# <a name="simplepartitioner-class"></a>simple_partitioner, classe

La classe `simple_partitioner` représente un partitionnement statique de la plage itérée par `parallel_for`. Le partitionneur divise la plage en segments de sorte que chaque segment comporte au moins le nombre d'itérations spécifié par la taille du segment.

## <a name="syntax"></a>Syntaxe

```
class simple_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[simple_partitioner](#ctor)|Construit un objet `simple_partitioner`.|
|[~ simple_partitioner, destructeur](#dtor)|Détruit un objet `simple_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`simple_partitioner`

## <a name="requirements"></a>Configuration requise

**En-tête :** ppl.h

**Espace de noms :** concurrency

##  <a name="dtor"></a> ~ simple_partitioner

Détruit un objet `simple_partitioner`.

```
~simple_partitioner();
```

##  <a name="ctor"></a> simple_partitioner

Construit un objet `simple_partitioner`.

```
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>Paramètres

*_Chunk_size*<br/>
La taille de partition minimale.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
