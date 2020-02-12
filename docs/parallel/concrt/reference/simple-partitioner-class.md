---
title: simple_partitioner, classe
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: 503f36b90c5eb3319f9aa2d56528172ffa95bb11
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142495"
---
# <a name="simple_partitioner-class"></a>simple_partitioner, classe

La classe `simple_partitioner` représente un partitionnement statique de la plage itérée par `parallel_for`. Le partitionneur divise la plage en segments de sorte que chaque segment comporte au moins le nombre d'itérations spécifié par la taille du segment.

## <a name="syntax"></a>Syntaxe

```cpp
class simple_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[simple_partitioner](#ctor)|Construit un objet `simple_partitioner`.|
|[Destructeur ~ simple_partitioner](#dtor)|Détruit un objet `simple_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`simple_partitioner`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrency

## <a name="dtor"></a>~ simple_partitioner

Détruit un objet `simple_partitioner`.

```cpp
~simple_partitioner();
```

## <a name="ctor"></a>simple_partitioner

Construit un objet `simple_partitioner`.

```cpp
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>Paramètres

*_Chunk_size*<br/>
Taille de partition minimale.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
