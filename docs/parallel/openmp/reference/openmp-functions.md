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
ms.openlocfilehash: 0475a83ba259ed00bbcb9ddaba99a1556b35f613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317140"
---
# <a name="openmp-functions"></a>Fonctions OpenMP

Fournit des liens vers des fonctions utilisées dans l’API OpenMP.

La mise en œuvre visualise de la norme OpenMP comprend les fonctions et les types de données suivants.

Pour l’exécution de l’environnement :

|Fonction|Description|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Définit le nombre de threads dans les régions parallèles à venir, à moins d’être remplacé par une clause [num_threads.](openmp-clauses.md#num-threads)|
|[omp_get_num_threads](#omp-get-num-threads)|Retourne le nombre de threads dans la région parallèle.|
|[omp_get_max_threads](#omp-get-max-threads)|Renvoie un intégrateur égal ou supérieur au nombre de threads qui seraient disponibles si une région parallèle sans [num_threads](openmp-clauses.md#num-threads) était définie à ce moment-là dans le code.|
|[omp_get_thread_num](#omp-get-thread-num)|Retourne le numéro de thread du thread exécutant au sein de son équipe de thread.|
|[omp_get_num_procs](#omp-get-num-procs)|Retourne le nombre de processeurs disponibles lorsque la fonction est appelée.|
|[omp_in_parallel](#omp-in-parallel)|Retourne nonzero s’il est appelé de l’intérieur d’une région parallèle.|
|[omp_set_dynamic](#omp-set-dynamic)|Indique que le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le temps d’exécution.|
|[omp_get_dynamic](#omp-get-dynamic)|Retourne une valeur qui indique si le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le temps d’exécution.|
|[omp_set_nested](#omp-set-nested)|Permet le parallélisme imbriqué.|
|[omp_get_nested](#omp-get-nested)|Retourne une valeur qui indique si le parallélisme imbriqué est activé.|

Pour verrouiller :

|Fonction|Description|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Initialise une serrure simple.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Initialise une serrure.|
|[omp_destroy_lock](#omp-destroy-lock)|Uninitialise une serrure.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Uninitialise une écluse imbriquée.|
|[omp_set_lock](#omp-set-lock)|Bloque l’exécution du fil jusqu’à ce qu’un verrou soit disponible.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Bloque l’exécution du fil jusqu’à ce qu’un verrou soit disponible.|
|[omp_unset_lock](#omp-unset-lock)|Libère une serrure.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Libère une écluse imbriquée.|
|[omp_test_lock](#omp-test-lock)|Tentatives de régler un verrou, mais ne bloque pas l’exécution du fil.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Tentatives de définir une serrure nestable, mais ne bloque pas l’exécution du fil.|

|Type de données|Description|
|---------|-----------|
|`omp_lock_t`|Un type qui détient l’état d’un verrou, si le verrou est disponible ou si un thread possède un verrou.|
|`omp_nest_lock_t`|Un type qui contient l’une des informations suivantes sur une serrure: si la serrure est disponible, et l’identité du fil qui possède l’écluse et un nombre de nidification.|

Pour les routines de chronométrage :

|Fonction|Description|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Retourne une valeur en secondes du temps écoulée à partir d’un certain point.|
|[omp_get_wtick](#omp-get-wtick)|Retourne le nombre de secondes entre les tiques d’horloge du processeur.|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a>omp_destroy_lock

Uninitialise une serrure.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Une variable `omp_lock_t` de type qui a été parasécé avec [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.2 omp_destroy_lock et omp_destroy_nest_lock fonctions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Exemple

Voir [omp_init_lock](#omp-init-lock) par exemple d’utilisation `omp_destroy_lock`.

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Uninitialise une écluse imbriquée.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Une variable `omp_nest_lock_t` de type qui a été parasécé avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.2 omp_destroy_lock et omp_destroy_nest_lock fonctions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Exemple

Voir [omp_init_nest_lock](#omp-init-nest-lock) par exemple d’utilisation `omp_destroy_nest_lock`.

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a>omp_get_dynamic

Retourne une valeur qui indique si le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le temps d’exécution.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Valeur retournée

Une valeur non zéro signifie que les threads seront ajustés dynamiquement.

### <a name="remarks"></a>Notes

L’ajustement dynamique des threads est spécifié avec [omp_set_dynamic](#omp-set-dynamic) et [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Pour plus d’informations, voir [3.1.7 omp_set_dynamic fonction](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Exemple

Voir [omp_set_dynamic](#omp-set-dynamic) par exemple d’utilisation `omp_get_dynamic`.

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a>omp_get_max_threads

Renvoie un intégrateur égal ou supérieur au nombre de threads qui seraient disponibles si une région parallèle sans [num_threads](openmp-clauses.md#num-threads) était définie à ce moment-là dans le code.

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.1.3 omp_get_max_threads fonction](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

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

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a>omp_get_nested

Retourne une valeur qui indique si le parallélisme imbriqué est activé.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Valeur retournée

Une valeur non zéro signifie que le parallélisme imbriqué est activé.

### <a name="remarks"></a>Notes

Le parallélisme imbriqué est spécifié avec [omp_set_nested](#omp-set-nested) et [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Pour plus d’informations, voir [3.1.10 omp_get_nested fonction](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Exemple

Voir [omp_set_nested](#omp-set-nested) par exemple d’utilisation `omp_get_nested`.

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a>omp_get_num_procs

Retourne le nombre de processeurs disponibles lorsque la fonction est appelée.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.1.5 omp_get_num_procs fonction](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

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

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a>omp_get_num_threads

Retourne le nombre de threads dans la région parallèle.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.1.2 omp_get_num_threads fonction](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

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

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a>omp_get_thread_num

Retourne le numéro de thread du thread exécutant au sein de son équipe de thread.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.1.4 omp_get_thread_num fonction](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Exemple

Voir [parallèle](openmp-directives.md#parallel) pour un `omp_get_thread_num`exemple d’utilisation .

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a>omp_get_wtick

Retourne le nombre de secondes entre les tiques d’horloge du processeur.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.3.2 omp_get_wtick fonction](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Exemple

Voir [omp_get_wtime](#omp-get-wtime) par exemple d’utilisation `omp_get_wtick`.

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a>omp_get_wtime

Retourne une valeur en secondes du temps écoulée à partir d’un certain point.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Valeur retournée

Retourne une valeur en secondes du temps écoulée à partir d’un point arbitraire, mais cohérent.

### <a name="remarks"></a>Notes

Ce point restera cohérent pendant l’exécution du programme, ce qui permettra de faire des comparaisons à venir.

Pour plus d’informations, voir [3.3.1 omp_get_wtime fonction](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

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

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a>omp_in_parallel

Retourne nonzero s’il est appelé de l’intérieur d’une région parallèle.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.1.6 omp_in_parallel fonction](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

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

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a>omp_init_lock

Initialise une serrure simple.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Variable de type `omp_lock_t`.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.1 omp_init_lock et omp_init_nest_lock fonctions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a>omp_init_nest_lock

Initialise une serrure.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Variable de type `omp_nest_lock_t`.

### <a name="remarks"></a>Notes

Le nombre initial de nidification est nul.

Pour plus d’informations, voir [3.2.1 omp_init_lock et omp_init_nest_lock fonctions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a>omp_set_dynamic

Indique que le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le temps d’exécution.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Paramètres

*Val*<br/>
Une valeur qui indique si le nombre de threads disponibles dans les régions parallèles à venir peut être ajusté par le temps d’exécution. Si non zéro, le temps d’exécution peut ajuster le nombre de threads, si zéro, le temps d’exécution ne sera pas ajuster dynamiquement le nombre de threads.

### <a name="remarks"></a>Notes

Le nombre de threads ne dépassera jamais la valeur fixée par [omp_set_num_threads](#omp-set-num-threads) ou par [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Utilisez [omp_get_dynamic](#omp-get-dynamic) pour afficher le `omp_set_dynamic`réglage actuel de .

Le réglage `omp_set_dynamic` pour remplacer le réglage de la variable [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) environnement.

Pour plus d’informations, voir [3.1.7 omp_set_dynamic fonction](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

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

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a>omp_set_lock

Bloque l’exécution du fil jusqu’à ce qu’un verrou soit disponible.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Une variable `omp_lock_t` de type qui a été parasécé avec [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.3 omp_set_lock et omp_set_nest_lock fonctions](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Exemples

Voir [omp_init_lock](#omp-init-lock) par exemple d’utilisation `omp_set_lock`.

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a>omp_set_nest_lock

Bloque l’exécution du fil jusqu’à ce qu’un verrou soit disponible.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Une variable `omp_nest_lock_t` de type qui a été parasécé avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.3 omp_set_lock et omp_set_nest_lock fonctions](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Exemples

Voir [omp_init_nest_lock](#omp-init-nest-lock) par exemple d’utilisation `omp_set_nest_lock`.

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a>omp_set_nested

Permet le parallélisme imbriqué.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Paramètres

*Val*<br/>
Une valeur non zéro permet le parallélisme imbriqué, tandis que zéro désactive le parallélisme imbriqué.

### <a name="remarks"></a>Notes

Le parallélisme imbriqué `omp_set_nested`de l’OMP peut être activé avec, ou en fixant la variable [OMP_NESTED](openmp-environment-variables.md#omp-nested) environnement.

Le réglage `omp_set_nested` pour remplacer le `OMP_NESTED` réglage de la variable de l’environnement.

L’activation de la variable de l’environnement peut briser un programme autrement opérationnel, car le nombre de fils augmente de façon exponentielle lors de la nidification des régions parallèles. Par exemple, une fonction qui revient six fois avec le nombre de threads OMP réglés à 4 nécessite 4 096 (4 à la puissance de 6) threads. Sauf pour les applications I/O-bound, les performances d’une application se dégradent généralement s’il y a plus de threads que de processeurs.

Utilisez [omp_get_nested](#omp-get-nested) pour afficher le réglage `omp_set_nested`actuel de .

Pour plus d’informations, voir [3.1.9 omp_set_nested fonction](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

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

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a>omp_set_num_threads

Définit le nombre de threads dans les régions parallèles à venir, à moins d’être remplacé par une clause [num_threads.](openmp-clauses.md#num-threads)

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Paramètres

*num_threads*<br/>
Le nombre de fils dans la région parallèle.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.1.1 omp_set_num_threads fonction](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Exemple

Voir [omp_get_num_threads](#omp-get-num-threads) par exemple d’utilisation `omp_set_num_threads`.

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a>omp_test_lock

Tentatives de régler un verrou, mais ne bloque pas l’exécution du fil.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Une variable `omp_lock_t` de type qui a été parasécé avec [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.5 omp_test_lock et omp_test_nest_lock fonctions](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a>omp_test_nest_lock

Tentatives de définir une serrure nestable, mais ne bloque pas l’exécution du fil.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Une variable `omp_nest_lock_t` de type qui a été parasécé avec [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.5 omp_test_lock et omp_test_nest_lock fonctions](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a>omp_unset_lock

Libère une serrure.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Une variable `omp_lock_t` de type qui a été parasminée avec [omp_init_lock](#omp-init-lock), détenue par le fil et l’exécution dans la fonction.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.4 omp_unset_lock et omp_unset_nest_lock fonctions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Exemple

Voir [omp_init_lock](#omp-init-lock) par exemple d’utilisation `omp_unset_lock`.

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Libère une écluse imbriquée.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Une variable `omp_nest_lock_t` de type qui a été parasminée avec [omp_init_nest_lock](#omp-init-nest-lock), détenue par le fil et l’exécution dans la fonction.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [3.2.4 omp_unset_lock et omp_unset_nest_lock fonctions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Exemple

Voir [omp_init_nest_lock](#omp-init-nest-lock) par exemple d’utilisation `omp_unset_nest_lock`.
