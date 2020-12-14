---
description: 'En savoir plus sur : classe simple_partitioner'
title: simple_partitioner, classe
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: 76dcac6d7fc2dce5b69d0a9dbefaf01420f8bcde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188688"
---
# <a name="simple_partitioner-class"></a>simple_partitioner, classe

La classe `simple_partitioner` représente un partitionnement statique de la plage itérée par `parallel_for`. Le partitionneur divise la plage en segments de sorte que chaque segment comporte au moins le nombre d'itérations spécifié par la taille du segment.

## <a name="syntax"></a>Syntaxe

```cpp
class simple_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[simple_partitioner](#ctor)|Construit un objet `simple_partitioner`.|
|[Destructeur ~ simple_partitioner](#dtor)|Détruit un objet `simple_partitioner` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`simple_partitioner`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrence

## <a name="simple_partitioner"></a><a name="dtor"></a> ~ simple_partitioner

Détruit un objet `simple_partitioner` .

```cpp
~simple_partitioner();
```

## <a name="simple_partitioner"></a><a name="ctor"></a> simple_partitioner

Construit un objet `simple_partitioner`.

```cpp
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>Paramètres

*_Chunk_size*<br/>
Taille de partition minimale.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
