---
title: Variables d’environnement OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a229aa453b6e40f0da25252f2f8aa1be3d97a729
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074252"
---
# <a name="openmp-environment-variables"></a>Variables d’environnement OpenMP

Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.

L’implémentation Visual C++ de l’OpenMP standard inclut les variables d’environnement suivantes. Ces variables d’environnement sont lues au démarrage du programme et les modifications apportées à leurs valeurs sont ignorées lors de l’exécution (par exemple, à l’aide de [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Variable d’environnement|Description|
|--------------------|-----------|
|[OMP_DYNAMIC](#omp-dynamic)|Spécifie si la durée d’exécution de OpenMP peut ajuster le nombre de threads dans une région parallèle.|
|[OMP_NESTED](#omp-nested)|Spécifie si parallélisme imbriquée est activée, à moins que le parallélisme imbriquée est activée ou désactivée avec `omp_set_nested`.|
|[OMP_NUM_THREADS](#omp-num-threads)|Définit le nombre maximal de threads dans la région parallèle, sauf substitution par [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou [num_threads](openmp-clauses.md#num-threads).|
|[OMP_SCHEDULE](#omp-schedule)|Modifie le comportement de la [planification](openmp-clauses.md#schedule) clause lorsque `schedule(runtime)` est spécifié dans un `for` ou `parallel for` directive.|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Spécifie si la durée d’exécution de OpenMP peut ajuster le nombre de threads dans une région parallèle.

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Notes

Le `OMP_DYNAMIC` variable d’environnement peut être remplacée par la [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) (fonction).

La valeur par défaut dans l’implémentation Visual C++ de la norme OpenMP est `OMP_DYNAMIC=FALSE`.

Pour plus d’informations, consultez [OMP_DYNAMIC 4.3](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Exemple

La commande suivante définit le `OMP_DYNAMIC` variable d’environnement sur TRUE :

```
set OMP_DYNAMIC=TRUE
```

La commande suivante affiche le paramètre actuel de la `OMP_DYNAMIC` variable d’environnement :

```
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Spécifie si parallélisme imbriquée est activée, à moins que le parallélisme imbriquée est activée ou désactivée avec `omp_set_nested`.

```
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Notes

Le `OMP_NESTED` variable d’environnement peut être remplacée par la [omp_set_nested](openmp-functions.md#omp-set-nested) (fonction).

La valeur par défaut dans l’implémentation Visual C++ de la norme OpenMP est `OMP_DYNAMIC=FALSE`.

Pour plus d’informations, consultez [OMP_NESTED 4.4](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Exemple

La commande suivante définit le `OMP_NESTED` variable d’environnement sur TRUE :

```
set OMP_NESTED=TRUE
```

La commande suivante affiche le paramètre actuel de la `OMP_NESTED` variable d’environnement :

```
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Définit le nombre maximal de threads dans la région parallèle, sauf substitution par [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou [num_threads](openmp-clauses.md#num-threads).

```
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Paramètres

*num*<br/>
Le nombre maximal de threads souhaité dans la région parallèle, jusqu'à 64 dans l’implémentation Visual C++.

### <a name="remarks"></a>Notes

Le `OMP_NUM_THREADS` variable d’environnement peut être remplacée par la [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) (fonction) ou par [num_threads](openmp-clauses.md#num-threads).

La valeur par défaut `num` dans Visual C++, mise en œuvre de la norme OpenMP est le nombre de processeurs virtuels, y compris les processeurs avec hyperthreading.

Pour plus d’informations, consultez [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Exemple

La commande suivante définit le `OMP_NUM_THREADS` variable d’environnement à 16 :

```
set OMP_NUM_THREADS=16
```

La commande suivante affiche le paramètre actuel de la `OMP_NUM_THREADS` variable d’environnement :

```
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Modifie le comportement de la [planification](openmp-clauses.md#schedule) clause lorsque `schedule(runtime)` est spécifié dans un `for` ou `parallel for` directive.

```
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Paramètres

*size*<br/>
(Facultatif) Spécifie la taille d’itérations. `size` Doit être un entier positif. La valeur par défaut est 1, sauf quand `type` est statique. Non valide quand `type` est `runtime`.

*type*<br/>
Le type de planification :

- `dynamic`
- `guided`
- `runtime`
- `static`

### <a name="remarks"></a>Notes

La valeur par défaut dans l’implémentation Visual C++ de la norme OpenMP est `OMP_SCHEDULE=static,0`.

Pour plus d’informations, consultez [OMP_SCHEDULE 4.1](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Exemple

La commande suivante définit le `OMP_SCHEDULE` variable d’environnement :

```
set OMP_SCHEDULE="guided,2"
```

La commande suivante affiche le paramètre actuel de la `OMP_SCHEDULE` variable d’environnement :

```
set OMP_SCHEDULE
```
