---
title: static_partitioner, classe
ms.date: 11/04/2016
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
ms.openlocfilehash: a0d06326b2ecbf3c427ae24b45751f7053778a0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500891"
---
# <a name="staticpartitioner-class"></a>static_partitioner, classe

La classe `static_partitioner` représente un partitionnement statique de la plage itérée par `parallel_for`. Le partitionneur divise la plage en autant de segments que de travaux disponibles pour le planificateur sous-jacent.

## <a name="syntax"></a>Syntaxe

```
class static_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[static_partitioner](#ctor)|Construit un objet `static_partitioner`.|
|[~ static_partitioner, destructeur](#dtor)|Détruit un objet `static_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`static_partitioner`

## <a name="requirements"></a>Configuration requise

**En-tête :** ppl.h

**Espace de noms :** concurrency

##  <a name="dtor"></a> ~ static_partitioner

Détruit un objet `static_partitioner`.

```
~static_partitioner();
```

##  <a name="ctor"></a> static_partitioner

Construit un objet `static_partitioner`.

```
static_partitioner();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
