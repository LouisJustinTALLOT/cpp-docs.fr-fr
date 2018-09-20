---
title: affinity_partitioner, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1254b316a52bd3e61b3cafd81ba2e89ee88b62
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444643"
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner, classe

La classe `affinity_partitioner` est similaire à la classe `static_partitioner`, mais elle améliore l'affinité du cache par son choix de mapper les sous-plages aux threads de travail. Elle peut améliorer considérablement les performances quand une boucle est réexécutée sur le même jeu de données et que les données tiennent dans le cache. Notez que le même objet `affinity_partitioner` doit être utilisé avec les itérations suivantes d'une boucle parallèle exécutée sur un jeu de données particulier, pour bénéficier de la localité des données.

## <a name="syntax"></a>Syntaxe

```
class affinity_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Construit un objet `affinity_partitioner`.|
|[~ affinity_partitioner, destructeur](#dtor)|Détruit un `affinity_partitioner` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`affinity_partitioner`

## <a name="requirements"></a>Configuration requise

**En-tête :** ppl.h

**Espace de noms :** concurrency

##  <a name="dtor"></a> ~ affinity_partitioner

Détruit un `affinity_partitioner` objet.

```
~affinity_partitioner();
```

##  <a name="ctor"></a> affinity_partitioner

Construit un objet `affinity_partitioner`.

```
affinity_partitioner();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
