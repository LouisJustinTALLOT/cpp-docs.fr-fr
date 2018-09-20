---
title: static_partitioner, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
dev_langs:
- C++
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de1b63cf24fbc84130302fcbae2cb965e8d00597
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376018"
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
