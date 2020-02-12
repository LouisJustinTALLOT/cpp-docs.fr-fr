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
ms.openlocfilehash: 0ae6bbee49d1b8873190a7054e55f65b40b31b13
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142875"
---
# <a name="affinity_partitioner-class"></a>affinity_partitioner, classe

La classe `affinity_partitioner` est similaire à la classe `static_partitioner`, mais elle améliore l'affinité du cache par son choix de mapper les sous-plages aux threads de travail. Elle peut améliorer considérablement les performances quand une boucle est réexécutée sur le même jeu de données et que les données tiennent dans le cache. Notez que le même objet `affinity_partitioner` doit être utilisé avec les itérations suivantes d'une boucle parallèle exécutée sur un jeu de données particulier, pour bénéficier de la localité des données.

## <a name="syntax"></a>Syntaxe

```cpp
class affinity_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Construit un objet `affinity_partitioner`.|
|[Destructeur ~ affinity_partitioner](#dtor)|Détruit un objet `affinity_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`affinity_partitioner`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrency

## <a name="dtor"></a>~ affinity_partitioner

Détruit un objet `affinity_partitioner`.

```cpp
~affinity_partitioner();
```

## <a name="ctor"></a>affinity_partitioner

Construit un objet `affinity_partitioner`.

```cpp
affinity_partitioner();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
