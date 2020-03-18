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
ms.openlocfilehash: 838427320fcb68cedb97b36156fc18002ed962d8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417004"
---
# <a name="openmp-environment-variables"></a>Variables d'environnement OpenMP

Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.

L’implémentation C++ visuelle de la norme OpenMP comprend les variables d’environnement suivantes. Ces variables d’environnement sont lues au démarrage du programme et les modifications apportées à leurs valeurs sont ignorées au moment de l’exécution (par exemple, à l’aide de [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Variable d’environnement|Description|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modifie le comportement de la clause [Schedule](openmp-clauses.md#schedule) lorsque `schedule(runtime)` est spécifié dans une directive `for` ou `parallel for`.|
|[OMP_NUM_THREADS](#omp-num-threads)|Définit le nombre maximal de threads dans la région parallèle, sauf si elle est substituée par [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Spécifie si le temps d’exécution OpenMP peut ajuster le nombre de threads dans une région parallèle.|
|[OMP_NESTED](#omp-nested)|Spécifie si le parallélisme imbriqué est activé, à moins que le parallélisme imbriqué soit activé ou désactivé avec `omp_set_nested`.|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Spécifie si le temps d’exécution OpenMP peut ajuster le nombre de threads dans une région parallèle.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Notes

La variable d’environnement `OMP_DYNAMIC` peut être remplacée par la fonction [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) .

La valeur par défaut de l' C++ implémentation visuelle de la norme OpenMP est `OMP_DYNAMIC=FALSE`.

Pour plus d’informations, consultez [4,3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Exemple

La commande suivante définit la variable d’environnement `OMP_DYNAMIC` sur TRUE :

```cmd
set OMP_DYNAMIC=TRUE
```

La commande suivante affiche le paramètre actuel de la variable d’environnement `OMP_DYNAMIC` :

```cmd
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Spécifie si le parallélisme imbriqué est activé, à moins que le parallélisme imbriqué soit activé ou désactivé avec `omp_set_nested`.

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Notes

La variable d’environnement `OMP_NESTED` peut être remplacée par la fonction [omp_set_nested](openmp-functions.md#omp-set-nested) .

La valeur par défaut de l' C++ implémentation visuelle de la norme OpenMP est `OMP_DYNAMIC=FALSE`.

Pour plus d’informations, consultez [4,4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Exemple

La commande suivante définit la variable d’environnement `OMP_NESTED` sur TRUE :

```cmd
set OMP_NESTED=TRUE
```

La commande suivante affiche le paramètre actuel de la variable d’environnement `OMP_NESTED` :

```cmd
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Définit le nombre maximal de threads dans la région parallèle, sauf si elle est substituée par [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Paramètres

*num*<br/>
Nombre maximal de threads que vous souhaitez dans la région parallèle, jusqu’à 64 dans l' C++ implémentation visuelle.

### <a name="remarks"></a>Notes

La variable d’environnement `OMP_NUM_THREADS` peut être remplacée par la fonction [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou par [num_threads](openmp-clauses.md#num-threads).

La valeur par défaut de `num` dans l' C++ implémentation visuelle de la norme OpenMP est le nombre de processeurs virtuels, y compris les processeurs hyperthreading.

Pour plus d’informations, consultez [4,2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Exemple

La commande suivante définit la variable d’environnement `OMP_NUM_THREADS` sur `16`:

```cmd
set OMP_NUM_THREADS=16
```

La commande suivante affiche le paramètre actuel de la variable d’environnement `OMP_NUM_THREADS` :

```cmd
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Modifie le comportement de la clause [Schedule](openmp-clauses.md#schedule) lorsque `schedule(runtime)` est spécifié dans une directive `for` ou `parallel for`.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Facultatif Spécifie la taille des itérations. la *taille* doit être un entier positif. La valeur par défaut est `1`, sauf lorsque le *type* est static. Non valide lorsque le *type* est `runtime`.

*type*<br/>
Type de planification, `dynamic`, `guided`, `runtime`ou `static`.

### <a name="remarks"></a>Notes

La valeur par défaut de l' C++ implémentation visuelle de la norme OpenMP est `OMP_SCHEDULE=static,0`.

Pour plus d’informations, consultez [4,1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Exemple

La commande suivante définit la variable d’environnement `OMP_SCHEDULE` :

```cmd
set OMP_SCHEDULE="guided,2"
```

La commande suivante affiche le paramètre actuel de la variable d’environnement `OMP_SCHEDULE` :

```cmd
set OMP_SCHEDULE
```
