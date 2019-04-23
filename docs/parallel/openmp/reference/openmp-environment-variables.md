---
title: Variables d'environnement OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: 73fb11db14df22e5df95fdec556ccdfc16a935e5
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124965"
---
# <a name="openmp-environment-variables"></a>Variables d'environnement OpenMP

Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.

L’implémentation Visual C++ de l’OpenMP standard inclut les variables d’environnement suivantes. Ces variables d’environnement sont lues au démarrage du programme et les modifications apportées à leurs valeurs sont ignorées lors de l’exécution (par exemple, à l’aide de [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Variable d’environnement|Description|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modifie le comportement de la [planification](openmp-clauses.md#schedule) clause lorsque `schedule(runtime)` est spécifié dans un `for` ou `parallel for` directive.|
|[OMP_NUM_THREADS](#omp-num-threads)|Définit le nombre maximal de threads dans la région parallèle, sauf substitution par [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Spécifie si la durée d’exécution de OpenMP peut ajuster le nombre de threads dans une région parallèle.|
|[OMP_NESTED](#omp-nested)|Spécifie si parallélisme imbriquée est activée, à moins que le parallélisme imbriquée est activée ou désactivée avec `omp_set_nested`.|

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

La commande suivante définit le `OMP_NUM_THREADS` variable d’environnement `16`:

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
(Facultatif) Spécifie la taille d’itérations. *taille* doit être un entier positif. La valeur par défaut est `1`, sauf lorsque *type* est statique. Non valide quand *type* est `runtime`.

*type*<br/>
Le type de la planification, soit `dynamic`, `guided`, `runtime`, ou `static`.

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
