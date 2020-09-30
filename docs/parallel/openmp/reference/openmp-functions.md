---
title: Fonctions OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 660d786148738c8ce998ad5d78645efdb444ea47
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503704"
---
# <a name="openmp-functions"></a>Fonctions OpenMP

Fournit des liens vers les fonctions utilisées dans l’API OpenMP.

L’implémentation Visual C++ de la norme OpenMP comprend les fonctions et types de données suivants.

Pour l’exécution de l’environnement :

|Fonction|Description|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Définit le nombre de threads dans les régions parallèles à venir, sauf si elles sont remplacées par une clause [num_threads](openmp-clauses.md#num-threads) .|
|[omp_get_num_threads](#omp-get-num-threads)|Retourne le nombre de threads dans la région parallèle.|
|[omp_get_max_threads](#omp-get-max-threads)|Retourne un entier qui est supérieur ou égal au nombre de threads qui seraient disponibles si une région parallèle sans [num_threads](openmp-clauses.md#num-threads) n’a pas été définie à ce stade dans le code.|
|[omp_get_thread_num](#omp-get-thread-num)|Retourne le numéro de thread du thread qui s’exécute dans son équipe de threads.|
|[omp_get_num_procs](#omp-get-num-procs)|Retourne le nombre de processeurs disponibles lorsque la fonction est appelée.|
|[omp_in_parallel](#omp-in-parallel)|Retourne une valeur différente de zéro si elle est appelée à partir d’une région parallèle.|
|[omp_set_dynamic](#omp-set-dynamic)|Indique que le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le temps d’exécution.|
|[omp_get_dynamic](#omp-get-dynamic)|Retourne une valeur qui indique si le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le moment de l’exécution.|
|[omp_set_nested](#omp-set-nested)|Active le parallélisme imbriqué.|
|[omp_get_nested](#omp-get-nested)|Retourne une valeur qui indique si le parallélisme imbriqué est activé.|

Pour le verrou :

|Fonction|Description|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Initialise un verrou simple.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Initialise un verrou.|
|[omp_destroy_lock](#omp-destroy-lock)|Réinitialise un verrou.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Réinitialise un verrou imbriqué.|
|[omp_set_lock](#omp-set-lock)|Bloque l’exécution du thread jusqu’à ce qu’un verrou soit disponible.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Bloque l’exécution du thread jusqu’à ce qu’un verrou soit disponible.|
|[omp_unset_lock](#omp-unset-lock)|Libère un verrou.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Libère un verrou imbriqué.|
|[omp_test_lock](#omp-test-lock)|Tente de définir un verrou, mais ne bloque pas l’exécution du thread.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Tente de définir un verrou imbriqué, mais ne bloque pas l’exécution du thread.|

|Type de données|Description|
|---------|-----------|
|`omp_lock_t`|Type qui contient l’état d’un verrou, si le verrou est disponible ou si un thread possède un verrou.|
|`omp_nest_lock_t`|Type qui contient l’une des informations suivantes sur un verrou : indique si le verrou est disponible et l’identité du thread qui détient le verrou et un nombre d’imbrications.|

Pour les routines de minutage :

|Fonction|Description|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Retourne une valeur en secondes du temps écoulé à partir d’un certain point.|
|[omp_get_wtick](#omp-get-wtick)|Retourne le nombre de secondes entre les battements d’horloge du processeur.|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a> omp_destroy_lock

Réinitialise un verrou.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_lock_t` qui a été initialisée avec [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.2.2 omp_destroy_lock et omp_destroy_nest_lock Functions](../3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [omp_init_lock](#omp-init-lock) `omp_destroy_lock` .

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a> omp_destroy_nest_lock

Réinitialise un verrou imbriqué.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_nest_lock_t` qui a été initialisée avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.2.2 omp_destroy_lock et omp_destroy_nest_lock Functions](../3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [omp_init_nest_lock](#omp-init-nest-lock) `omp_destroy_nest_lock` .

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a> omp_get_dynamic

Retourne une valeur qui indique si le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le moment de l’exécution.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Valeur renvoyée

Une valeur différente de zéro signifie que les threads seront ajustés dynamiquement.

### <a name="remarks"></a>Remarques

L’ajustement dynamique des threads est spécifié avec [omp_set_dynamic](#omp-set-dynamic) et [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Pour plus d’informations, consultez [3.1.7 omp_set_dynamic Function](../3-run-time-library-functions.md#317-omp_set_dynamic-function).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [omp_set_dynamic](#omp-set-dynamic) `omp_get_dynamic` .

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a> omp_get_max_threads

Retourne un entier qui est supérieur ou égal au nombre de threads qui seraient disponibles si une région parallèle sans [num_threads](openmp-clauses.md#num-threads) n’a pas été définie à ce stade dans le code.

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.1.3 omp_get_max_threads Function](../3-run-time-library-functions.md#313-omp_get_max_threads-function).

### <a name="example"></a>Exemple

```cpp
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a> omp_get_nested

Retourne une valeur qui indique si le parallélisme imbriqué est activé.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Valeur renvoyée

Une valeur différente de zéro signifie que le parallélisme imbriqué est activé.

### <a name="remarks"></a>Remarques

Le parallélisme imbriqué est spécifié avec [omp_set_nested](#omp-set-nested) et [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Pour plus d’informations, consultez [3.1.10 omp_get_nested Function](../3-run-time-library-functions.md#3110-omp_get_nested-function).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [omp_set_nested](#omp-set-nested) `omp_get_nested` .

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a> omp_get_num_procs

Retourne le nombre de processeurs disponibles lorsque la fonction est appelée.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez la [fonction 3.1.5 omp_get_num_procs](../3-run-time-library-functions.md#315-omp_get_num_procs-function).

### <a name="example"></a>Exemple

```cpp
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a> omp_get_num_threads

Retourne le nombre de threads dans la région parallèle.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.1.2 omp_get_num_threads Function](../3-run-time-library-functions.md#312-omp_get_num_threads-function).

### <a name="example"></a>Exemple

```cpp
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a> omp_get_thread_num

Retourne le numéro de thread du thread qui s’exécute dans son équipe de threads.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez la [fonction 3.1.4 omp_get_thread_num](../3-run-time-library-functions.md#314-omp_get_thread_num-function).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [Parallel](openmp-directives.md#parallel) `omp_get_thread_num` .

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a> omp_get_wtick

Retourne le nombre de secondes entre les battements d’horloge du processeur.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.3.2 omp_get_wtick Function](../3-run-time-library-functions.md#332-omp_get_wtick-function).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [omp_get_wtime](#omp-get-wtime) `omp_get_wtick` .

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a> omp_get_wtime

Retourne une valeur en secondes du temps écoulé à partir d’un certain point.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Valeur renvoyée

Retourne une valeur en secondes du temps écoulé à partir d’un point arbitraire, mais cohérent.

### <a name="remarks"></a>Remarques

Ce point restera cohérent pendant l’exécution du programme, ce qui rendra possible les futures comparaisons.

Pour plus d’informations, consultez [3.3.1 omp_get_wtime Function](../3-run-time-library-functions.md#331-omp_get_wtime-function).

### <a name="example"></a>Exemple

```cpp
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a> omp_in_parallel

Retourne une valeur différente de zéro si elle est appelée à partir d’une région parallèle.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.1.6 omp_in_parallel Function](../3-run-time-library-functions.md#316-omp_in_parallel-function).

### <a name="example"></a>Exemple

```cpp
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a> omp_init_lock

Initialise un verrou simple.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_lock_t`.

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez la section [3.2.1 omp_init_lock et omp_init_nest_lock Functions](../3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

### <a name="example"></a>Exemple

```cpp
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a> omp_init_nest_lock

Initialise un verrou.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_nest_lock_t`.

### <a name="remarks"></a>Remarques

Le nombre initial d’imbrications est égal à zéro.

Pour plus d’informations, consultez la section [3.2.1 omp_init_lock et omp_init_nest_lock Functions](../3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

### <a name="example"></a>Exemple

```cpp
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a> omp_set_dynamic

Indique que le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le temps d’exécution.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Paramètres

*multiples*<br/>
Valeur qui indique si le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le Runtime. Si la valeur est différente de zéro, le runtime peut ajuster le nombre de threads, si zéro, le runtime n’ajuste pas dynamiquement le nombre de threads.

### <a name="remarks"></a>Remarques

Le nombre de threads ne dépassera jamais la valeur définie par [omp_set_num_threads](#omp-set-num-threads) ou par [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Utilisez [omp_get_dynamic](#omp-get-dynamic) pour afficher la valeur actuelle de `omp_set_dynamic` .

Le paramètre de `omp_set_dynamic` remplace le paramètre de la variable d’environnement [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) .

Pour plus d’informations, consultez [3.1.7 omp_set_dynamic Function](../3-run-time-library-functions.md#317-omp_set_dynamic-function).

### <a name="example"></a>Exemple

```cpp
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a> omp_set_lock

Bloque l’exécution du thread jusqu’à ce qu’un verrou soit disponible.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_lock_t` qui a été initialisée avec [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez la section [3.2.3 omp_set_lock et omp_set_nest_lock Functions](../3-run-time-library-functions.md#323-omp_set_lock-and-omp_set_nest_lock-functions).

### <a name="examples"></a>Exemples

Pour obtenir un exemple d’utilisation de, consultez [omp_init_lock](#omp-init-lock) `omp_set_lock` .

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a> omp_set_nest_lock

Bloque l’exécution du thread jusqu’à ce qu’un verrou soit disponible.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_nest_lock_t` qui a été initialisée avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez la section [3.2.3 omp_set_lock et omp_set_nest_lock Functions](../3-run-time-library-functions.md#323-omp_set_lock-and-omp_set_nest_lock-functions).

### <a name="examples"></a>Exemples

Pour obtenir un exemple d’utilisation de, consultez [omp_init_nest_lock](#omp-init-nest-lock) `omp_set_nest_lock` .

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a> omp_set_nested

Active le parallélisme imbriqué.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Paramètres

*multiples*<br/>
Une valeur différente de zéro active le parallélisme imbriqué, tandis que zéro désactive le parallélisme imbriqué.

### <a name="remarks"></a>Remarques

OMP le parallélisme imbriqué peut être activé `omp_set_nested` ou en définissant la variable d’environnement [OMP_NESTED](openmp-environment-variables.md#omp-nested) .

Le paramètre de `omp_set_nested` remplacera le paramètre de la `OMP_NESTED` variable d’environnement.

L’activation de la variable d’environnement peut interrompre un programme opérationnel autrement, car le nombre de threads augmente de façon exponentielle lors de l’imbrication de régions parallèles. Par exemple, une fonction qui est recurse six fois avec le nombre de threads OMP défini sur 4 requiert 4 096 (4 à la puissance de 6) threads. Sauf avec les applications liées aux e/s, les performances d’une application se dégradent généralement si le nombre de threads est supérieur à celui des processeurs.

Utilisez [omp_get_nested](#omp-get-nested) pour afficher la valeur actuelle de `omp_set_nested` .

Pour plus d’informations, consultez [3.1.9 omp_set_nested Function](../3-run-time-library-functions.md#319-omp_set_nested-function).

### <a name="example"></a>Exemple

```cpp
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a> omp_set_num_threads

Définit le nombre de threads dans les régions parallèles à venir, sauf si elles sont remplacées par une clause [num_threads](openmp-clauses.md#num-threads) .

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Paramètres

*num_threads*<br/>
Nombre de threads dans la région parallèle.

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez la section [3.1.1 omp_set_num_threads Function](../3-run-time-library-functions.md#311-omp_set_num_threads-function).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [omp_get_num_threads](#omp-get-num-threads) `omp_set_num_threads` .

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a> omp_test_lock

Tente de définir un verrou, mais ne bloque pas l’exécution du thread.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_lock_t` qui a été initialisée avec [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.2.5 omp_test_lock et omp_test_nest_lock Functions](../3-run-time-library-functions.md#325-omp_test_lock-and-omp_test_nest_lock-functions).

### <a name="example"></a>Exemple

```cpp
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a> omp_test_nest_lock

Tente de définir un verrou imbriqué, mais ne bloque pas l’exécution du thread.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_nest_lock_t` qui a été initialisée avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.2.5 omp_test_lock et omp_test_nest_lock Functions](../3-run-time-library-functions.md#325-omp_test_lock-and-omp_test_nest_lock-functions).

### <a name="example"></a>Exemple

```cpp
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a> omp_unset_lock

Libère un verrou.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_lock_t` qui a été initialisée avec [omp_init_lock](#omp-init-lock), détenue par le thread et s’exécutant dans la fonction.

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.2.4 omp_unset_lock et omp_unset_nest_lock fonctions](../3-run-time-library-functions.md#324-omp_unset_lock-and-omp_unset_nest_lock-functions).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [omp_init_lock](#omp-init-lock) `omp_unset_lock` .

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a> omp_unset_nest_lock

Libère un verrou imbriqué.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Lock*<br/>
Variable de type `omp_nest_lock_t` qui a été initialisée avec [omp_init_nest_lock](#omp-init-nest-lock), détenue par le thread et s’exécutant dans la fonction.

### <a name="remarks"></a>Remarques

Pour plus d’informations, consultez [3.2.4 omp_unset_lock et omp_unset_nest_lock fonctions](../3-run-time-library-functions.md#324-omp_unset_lock-and-omp_unset_nest_lock-functions).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [omp_init_nest_lock](#omp-init-nest-lock) `omp_unset_nest_lock` .
