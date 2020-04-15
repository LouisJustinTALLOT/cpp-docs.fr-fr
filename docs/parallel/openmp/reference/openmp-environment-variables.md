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
ms.openlocfilehash: bee9b0fbdf147ee962ff92d0b3b9ff57d4209f84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363886"
---
# <a name="openmp-environment-variables"></a>Variables d'environnement OpenMP

Fournit des liens vers des variables environment utilisées dans l’API OpenMP.

La mise en œuvre visuelle de la norme OpenMP comprend les variables de l’environnement suivantes. Ces variables de l’environnement sont lues au démarrage du programme et les modifications apportées à leurs valeurs sont ignorées au moment de l’exécution (par exemple, à [l’aide de _putenv, _wputenv).](../../../c-runtime-library/reference/putenv-wputenv.md)

|Variable d’environnement|Description|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modifie le comportement de la `schedule(runtime)` clause de `for` `parallel for` [calendrier](openmp-clauses.md#schedule) lorsqu’il est spécifié dans une directive ou une directive.|
|[OMP_NUM_THREADS](#omp-num-threads)|Définit le nombre maximum de threads dans la région parallèle, à moins d’être remplacé par [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Précise si le temps d’exécution OpenMP peut ajuster le nombre de threads dans une région parallèle.|
|[OMP_NESTED](#omp-nested)|Précise si le parallélisme imbriqué est activé, à `omp_set_nested`moins que le parallélisme imbriqué ne soit activé ou désactivé avec .|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a>OMP_DYNAMIC

Précise si le temps d’exécution OpenMP peut ajuster le nombre de threads dans une région parallèle.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Notes

La `OMP_DYNAMIC` variable de l’environnement peut être remplacée par la fonction [omp_set_dynamic.](openmp-functions.md#omp-set-dynamic)

La valeur par défaut dans la mise en `OMP_DYNAMIC=FALSE`œuvre Visual C DE la norme OpenMP est .

Pour plus d’informations, voir [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Exemple

La commande suivante `OMP_DYNAMIC` définit la variable de l’environnement à TRUE :

```cmd
set OMP_DYNAMIC=TRUE
```

La commande suivante affiche le `OMP_DYNAMIC` réglage actuel de la variable de l’environnement :

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a>OMP_NESTED

Précise si le parallélisme imbriqué est activé, à `omp_set_nested`moins que le parallélisme imbriqué ne soit activé ou désactivé avec .

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Notes

La `OMP_NESTED` variable de l’environnement peut être remplacée par la fonction [omp_set_nested.](openmp-functions.md#omp-set-nested)

La valeur par défaut dans la mise en `OMP_DYNAMIC=FALSE`œuvre Visual C DE la norme OpenMP est .

Pour plus d’informations, voir [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Exemple

La commande suivante `OMP_NESTED` définit la variable de l’environnement à TRUE :

```cmd
set OMP_NESTED=TRUE
```

La commande suivante affiche le `OMP_NESTED` réglage actuel de la variable de l’environnement :

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a>OMP_NUM_THREADS

Définit le nombre maximum de threads dans la région parallèle, à moins d’être remplacé par [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Paramètres

*num*<br/>
Le nombre maximum de threads que vous souhaitez dans la région parallèle, jusqu’à 64 dans la mise en œuvre Visual C.

### <a name="remarks"></a>Notes

La `OMP_NUM_THREADS` variable d’environnement peut être remplacée par la fonction [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) ou par [num_threads](openmp-clauses.md#num-threads).

La valeur `num` par défaut de la mise en œuvre visualC DE la norme OpenMP est le nombre de processeurs virtuels, y compris l’hyperthreading CPUs.

Pour plus d’informations, voir [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Exemple

La commande suivante `OMP_NUM_THREADS` définit `16`la variable de l’environnement à :

```cmd
set OMP_NUM_THREADS=16
```

La commande suivante affiche le `OMP_NUM_THREADS` réglage actuel de la variable de l’environnement :

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a>OMP_SCHEDULE

Modifie le comportement de la `schedule(runtime)` clause de `for` `parallel for` [calendrier](openmp-clauses.md#schedule) lorsqu’il est spécifié dans une directive ou une directive.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
(Facultatif) Spécifie la taille des itérations. *la taille* doit être un intégré positif. La valeur `1`par défaut est, sauf lorsque *le type* est statique. Non valide lorsque `runtime`le *type* est .

*type*<br/>
Le genre d’horaire, `runtime`soit `static` `dynamic`, `guided`, , ou .

### <a name="remarks"></a>Notes

La valeur par défaut dans la mise en `OMP_SCHEDULE=static,0`œuvre Visual C DE la norme OpenMP est .

Pour plus d’informations, voir [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Exemple

La commande suivante `OMP_SCHEDULE` définit la variable de l’environnement :

```cmd
set OMP_SCHEDULE="guided,2"
```

La commande suivante affiche le `OMP_SCHEDULE` réglage actuel de la variable de l’environnement :

```cmd
set OMP_SCHEDULE
```
