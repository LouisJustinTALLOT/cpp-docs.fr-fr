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
ms.openlocfilehash: 1bf0e08f3b28368d9aea5438b3036ac8a0283735
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363087"
---
# <a name="openmp-functions"></a>Fonctions OpenMP

Fournit des liens vers les fonctions utilisées dans l’API OpenMP.

L’élément visuel C++ implémentation de la norme OpenMP inclut les types suivants de fonctions et données.

L’exécution d’environnement :

|Fonction|Description|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Définit le nombre de threads dans des régions parallèles à venir, sauf substitution par une [num_threads](openmp-clauses.md#num-threads) clause.|
|[omp_get_num_threads](#omp-get-num-threads)|Retourne le nombre de threads dans la région parallèle.|
|[omp_get_max_threads](#omp-get-max-threads)|Retourne un entier qui est égal à ou supérieur au nombre de threads qui serait disponible si une région parallèle sans [num_threads](openmp-clauses.md#num-threads) ont été définies à ce stade dans le code.|
|[omp_get_thread_num](#omp-get-thread-num)|Retourne le nombre de threads d’exécution du thread au sein de son équipe de thread.|
|[omp_get_num_procs](#omp-get-num-procs)|Retourne le nombre de processeurs qui sont disponibles lorsque la fonction est appelée.|
|[omp_in_parallel](#omp-in-parallel)|Retourne une valeur différente de zéro si elle est appelée à partir de dans une région parallèle.|
|[omp_set_dynamic](#omp-set-dynamic)|Indique que le nombre de threads disponibles dans des régions parallèles à venir peut être ajusté par la durée d’exécution.|
|[omp_get_dynamic](#omp-get-dynamic)|Retourne une valeur qui indique si le nombre de threads disponibles dans des régions parallèles à venir peut être ajusté par la durée d’exécution.|
|[omp_set_nested](#omp-set-nested)|Active le parallélisme imbriqué.|
|[omp_get_nested](#omp-get-nested)|Retourne une valeur qui indique si le parallélisme imbriquée est activée.|

Verrou :

|Fonction|Description|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Initialise un verrou simple.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Initialise un verrou.|
|[omp_destroy_lock](#omp-destroy-lock)|Désinitialise un verrou.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Désinitialise un verrou pouvant être imbriqué.|
|[omp_set_lock](#omp-set-lock)|Blocs d’exécution de thread jusqu'à ce qu’un verrou est disponible.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Blocs d’exécution de thread jusqu'à ce qu’un verrou est disponible.|
|[omp_unset_lock](#omp-unset-lock)|Libère un verrou.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Libère un verrou pouvant être imbriqué.|
|[omp_test_lock](#omp-test-lock)|Tente de définir un verrou, mais ne bloque pas l’exécution du thread.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Tente de définir un verrou pouvant être imbriqué, mais ne bloque pas l’exécution du thread.|

|Type de données|Description|
|---------|-----------|
|`omp_lock_t`|Un type qui contient l’état d’un verrou, si le verrou est disponible ou si un thread détient un verrou.|
|`omp_nest_lock_t`|Un type qui conserve l’un des éléments suivants d’informations sur un verrou : si le verrou est disponible et que l’identité du thread qui détient le verrou et un nombre d’imbrication.|

Pour les routines de minutage :

|Fonction|Description|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Retourne qu'une valeur en secondes du temps écoulé à partir d’un moment donné.|
|[omp_get_wtick](#omp-get-wtick)|Retourne le nombre de secondes entre les battements d’horloge de processeur.|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

Désinitialise un verrou.

```
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type `omp_lock_t` qui a été initialisée avec [fonctions omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.2 fonctions omp_destroy_lock et omp_destroy_nest_lock fonctions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Exemple

Consultez [fonctions omp_init_lock](#omp-init-lock) pour obtenir un exemple d’utilisation de `omp_destroy_lock`.

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Désinitialise un verrou pouvant être imbriqué.

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type `omp_nest_lock_t` qui a été initialisée avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.2 fonctions omp_destroy_lock et omp_destroy_nest_lock fonctions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Exemple

Consultez [omp_init_nest_lock](#omp-init-nest-lock) pour obtenir un exemple d’utilisation de `omp_destroy_nest_lock`.

## <a name="omp-get-dynamic"></a>omp_get_dynamic

Retourne une valeur qui indique si le nombre de threads disponibles dans des régions parallèles à venir peut être ajusté par la durée d’exécution.

```
int omp_get_dynamic();
```

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro signifie threads soient ajustées dynamiquement.

### <a name="remarks"></a>Notes

L’ajustement dynamique de threads est spécifié avec [omp_set_dynamic](#omp-set-dynamic) et [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Pour plus d’informations, consultez [3.1.7 omp_set_dynamic fonction](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Exemple

Consultez [omp_set_dynamic](#omp-set-dynamic) pour obtenir un exemple d’utilisation de `omp_get_dynamic`.

## <a name="omp-get-max-threads"></a>omp_get_max_threads

Retourne un entier qui est égal à ou supérieur au nombre de threads qui serait disponible si une région parallèle sans [num_threads](openmp-clauses.md#num-threads) ont été définies à ce stade dans le code.

```
int omp_get_max_threads( )
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.1.3 omp_get_max_threads fonction](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

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

## <a name="omp-get-nested"></a>omp_get_nested

Retourne une valeur qui indique si le parallélisme imbriquée est activée.

```
int omp_get_nested( );
```

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro signifie parallélisme imbriquée est activée.

### <a name="remarks"></a>Notes

Parallélisme imbriquée est spécifié avec [omp_set_nested](#omp-set-nested) et [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Pour plus d’informations, consultez [3.1.10 omp_get_nested fonction](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Exemple

Consultez [omp_set_nested](#omp-set-nested) pour obtenir un exemple d’utilisation de `omp_get_nested`.

## <a name="omp-get-num-procs"></a>omp_get_num_procs

Retourne le nombre de processeurs qui sont disponibles lorsque la fonction est appelée.

```
int omp_get_num_procs();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.1.5 omp_get_num_procs fonction](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

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

## <a name="omp-get-num-threads"></a>omp_get_num_threads

Retourne le nombre de threads dans la région parallèle.

```
int omp_get_num_threads( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.1.2 omp_get_num_threads fonction](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

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

## <a name="omp-get-thread-num"></a>omp_get_thread_num

Retourne le nombre de threads d’exécution du thread au sein de son équipe de thread.

```
int omp_get_thread_num( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.1.4 omp_get_thread_num fonction](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Exemple

Consultez [parallèles](openmp-directives.md#parallel) pour obtenir un exemple d’utilisation de `omp_get_thread_num`.

## <a name="omp-get-wtick"></a>omp_get_wtick

Retourne le nombre de secondes entre les battements d’horloge de processeur.

```
double omp_get_wtick( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.3.2 omp_get_wtick fonction](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Exemple

Consultez [omp_get_wtime](#omp-get-wtime) pour obtenir un exemple d’utilisation de `omp_get_wtick`.

## <a name="omp-get-wtime"></a>omp_get_wtime

Retourne qu'une valeur en secondes du temps écoulé à partir d’un moment donné.

```
double omp_get_wtime( );
```

### <a name="return-value"></a>Valeur de retour

Retourne qu'une valeur en secondes du temps écoulé à partir du point certaines arbitraire, mais il est cohérent.

### <a name="remarks"></a>Notes

Ce point reste cohérent lors de l’exécution du programme, comparaisons à venir possible.

Pour plus d’informations, consultez [3.3.1 omp_get_wtime fonction](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

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

## <a name="omp-in-parallel"></a>omp_in_parallel

Retourne une valeur différente de zéro si elle est appelée à partir de dans une région parallèle.

```
int omp_in_parallel( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.1.6 omp_in_parallel fonction](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

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

## <a name="omp-init-lock"></a>omp_init_lock

Initialise un verrou simple.

```
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Variable de type `omp_lock_t`.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.1 fonctions omp_init_lock et omp_init_nest_lock fonctions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp-init-nest-lock"></a>omp_init_nest_lock

Initialise un verrou.

```
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Variable de type `omp_nest_lock_t`.

### <a name="remarks"></a>Notes

Le nombre initial d’imbrication est égal à zéro.

Pour plus d’informations, consultez [3.2.1 fonctions omp_init_lock et omp_init_nest_lock fonctions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp-set-dynamic"></a>omp_set_dynamic

Indique que le nombre de threads disponibles dans des régions parallèles à venir peut être ajusté par la durée d’exécution.

```
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Paramètres

*val*<br/>
Une valeur qui indique si le nombre de threads disponibles dans des régions parallèles à venir peut être ajusté par le runtime. Si elle est différente de zéro, que le runtime peut ajuster le nombre de threads, si zéro, le runtime ne sont pas ajuster dynamiquement le nombre de threads.

### <a name="remarks"></a>Notes

Le nombre de threads ne dépassera jamais la valeur définie par [omp_set_num_threads](#omp-set-num-threads) ou par [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Utilisez [omp_get_dynamic](#omp-get-dynamic) pour afficher le paramètre actuel de `omp_set_dynamic`.

Le paramètre pour `omp_set_dynamic` remplace le paramètre de la [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) variable d’environnement.

Pour plus d’informations, consultez [3.1.7 omp_set_dynamic fonction](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

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

## <a name="omp-set-lock"></a>omp_set_lock

Blocs d’exécution de thread jusqu'à ce qu’un verrou est disponible.

```
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type `omp_lock_t` qui a été initialisée avec [fonctions omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.3 fonctions omp_set_lock et omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Exemples

Consultez [fonctions omp_init_lock](#omp-init-lock) pour obtenir un exemple d’utilisation de `omp_set_lock`.

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

Blocs d’exécution de thread jusqu'à ce qu’un verrou est disponible.

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type `omp_nest_lock_t` qui a été initialisée avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.3 fonctions omp_set_lock et omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Exemples

Consultez [omp_init_nest_lock](#omp-init-nest-lock) pour obtenir un exemple d’utilisation de `omp_set_nest_lock`.

## <a name="omp-set-nested"></a>omp_set_nested

Active le parallélisme imbriqué.

```
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Paramètres

*val*<br/>
Une valeur différente de zéro permet de parallélisme imbriqué, alors que zéro désactive le parallélisme imbriqué.

### <a name="remarks"></a>Notes

OMP imbriqué parallélisme peut être activé avec `omp_set_nested`, ou en définissant le [OMP_NESTED](openmp-environment-variables.md#omp-nested) variable d’environnement.

Le paramètre pour `omp_set_nested` remplace le paramètre de la `OMP_NESTED` variable d’environnement.

L’activation de la variable d’environnement peut interrompre un programme opérationnel dans le cas contraire, étant donné que le nombre de threads augmente de façon exponentielle lors de l’imbrication de régions parallèles. Par exemple, une fonction qui lit de façon récursive six fois avec le nombre de threads OMP défini sur 4 nécessite 4 096 (4 à la puissance de 6) threads. À l’exception avec les applications utilisant des e/S, les performances d’une application généralement se dégradent s’il existe plus de threads que de processeurs.

Utilisez [omp_get_nested](#omp-get-nested) pour afficher le paramètre actuel de `omp_set_nested`.

Pour plus d’informations, consultez [3.1.9 omp_set_nested fonction](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

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

## <a name="omp-set-num-threads"></a>omp_set_num_threads

Définit le nombre de threads dans des régions parallèles à venir, sauf substitution par une [num_threads](openmp-clauses.md#num-threads) clause.

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Paramètres

*num_threads*<br/>
Le nombre de threads dans la région parallèle.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.1.1 omp_set_num_threads fonction](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Exemple

Consultez [omp_get_num_threads](#omp-get-num-threads) pour obtenir un exemple d’utilisation de `omp_set_num_threads`.

## <a name="omp-test-lock"></a>omp_test_lock

Tente de définir un verrou, mais ne bloque pas l’exécution du thread.

```
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type `omp_lock_t` qui a été initialisée avec [fonctions omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.5 fonctions omp_test_lock et omp_test_nest_lock fonctions](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp-test-nest-lock"></a>omp_test_nest_lock

Tente de définir un verrou pouvant être imbriqué, mais ne bloque pas l’exécution du thread.

```
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type `omp_nest_lock_t` qui a été initialisée avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.5 fonctions omp_test_lock et omp_test_nest_lock fonctions](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp-unset-lock"></a>omp_unset_lock

Libère un verrou.

```
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type `omp_lock_t` qui a été initialisée avec [fonctions omp_init_lock](#omp-init-lock), détenu par le thread et en cours d’exécution dans la fonction.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.4 fonctions omp_unset_lock et omp_unset_nest_lock fonctions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Exemple

Consultez [fonctions omp_init_lock](#omp-init-lock) pour obtenir un exemple d’utilisation de `omp_unset_lock`.

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Libère un verrou pouvant être imbriqué.

```
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type `omp_nest_lock_t` qui a été initialisée avec [omp_init_nest_lock](#omp-init-nest-lock), détenu par le thread et en cours d’exécution dans la fonction.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.4 fonctions omp_unset_lock et omp_unset_nest_lock fonctions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Exemple

Consultez [omp_init_nest_lock](#omp-init-nest-lock) pour obtenir un exemple d’utilisation de `omp_unset_nest_lock`.
