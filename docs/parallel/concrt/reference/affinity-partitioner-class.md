---
title: affinity_partitioner, classe
ms.date: 11/04/2016
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
ms.openlocfilehash: dac25755c388e5297ce671da09b7938f09f1ef03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337659"
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

##  <a name="dtor"></a> ~affinity_partitioner

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
