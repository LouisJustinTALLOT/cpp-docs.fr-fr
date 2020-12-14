---
description: 'En savoir plus sur : classe static_partitioner'
title: static_partitioner, classe
ms.date: 11/04/2016
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
ms.openlocfilehash: f75d2e620a66e0ed347d39d429f59e3e2715369a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188493"
---
# <a name="static_partitioner-class"></a>static_partitioner, classe

La classe `static_partitioner` représente un partitionnement statique de la plage itérée par `parallel_for`. Le partitionneur divise la plage en autant de segments que de threads de travail disponibles pour le planificateur sous-jacent.

## <a name="syntax"></a>Syntaxe

```cpp
class static_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[static_partitioner](#ctor)|Construit un objet `static_partitioner`.|
|[Destructeur ~ static_partitioner](#dtor)|Détruit un objet `static_partitioner` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`static_partitioner`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrence

## <a name="static_partitioner"></a><a name="dtor"></a> ~ static_partitioner

Détruit un objet `static_partitioner` .

```cpp
~static_partitioner();
```

## <a name="static_partitioner"></a><a name="ctor"></a> static_partitioner

Construit un objet `static_partitioner`.

```cpp
static_partitioner();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
