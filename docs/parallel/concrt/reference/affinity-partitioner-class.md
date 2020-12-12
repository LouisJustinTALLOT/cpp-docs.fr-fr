---
description: 'En savoir plus sur : classe affinity_partitioner'
title: affinity_partitioner, classe
ms.date: 11/04/2016
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
ms.openlocfilehash: 44aa693d5007507e33f062a673713d1ddbda3172
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172321"
---
# <a name="affinity_partitioner-class"></a>affinity_partitioner, classe

La classe `affinity_partitioner` est similaire à la classe `static_partitioner`, mais elle améliore l'affinité du cache par son choix de mapper les sous-plages aux threads de travail. Elle peut améliorer considérablement les performances quand une boucle est réexécutée sur le même jeu de données et que les données tiennent dans le cache. Notez que le même objet `affinity_partitioner` doit être utilisé avec les itérations suivantes d'une boucle parallèle exécutée sur un jeu de données particulier, pour bénéficier de la localité des données.

## <a name="syntax"></a>Syntaxe

```cpp
class affinity_partitioner;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Construit un objet `affinity_partitioner`.|
|[Destructeur ~ affinity_partitioner](#dtor)|Détruit un `affinity_partitioner` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`affinity_partitioner`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrence

## <a name="affinity_partitioner"></a><a name="dtor"></a> ~ affinity_partitioner

Détruit un `affinity_partitioner` objet.

```cpp
~affinity_partitioner();
```

## <a name="affinity_partitioner"></a><a name="ctor"></a> affinity_partitioner

Construit un objet `affinity_partitioner`.

```cpp
affinity_partitioner();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
