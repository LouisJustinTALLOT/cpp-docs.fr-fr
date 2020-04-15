---
title: Directives OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: 569419b3422b155afc6e9692efaecd4e5a06f188
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366444"
---
# <a name="openmp-directives"></a>Directives OpenMP

Fournit des liens vers des directives utilisées dans l’API OpenMP.

Visual CMD prend en charge les directives OpenMP suivantes.

Pour le partage parallèle du travail :

|Directive|Description|
|---------|-----------|
|[parallel](#parallel)|Définit une région parallèle, qui est un code qui sera exécuté par plusieurs threads en parallèle.|
|[for](#for-openmp)|Provoque le travail `for` effectué dans une boucle à l’intérieur d’une région parallèle à diviser entre les fils.|
|[sections](#sections-openmp)|Identifie les sections de code à répartir entre tous les threads.|
|[single](#single)|Vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, pas nécessairement le fil maître.|

Pour le master et la synchronisation :

|Directive|Description|
|---------|-----------|
|[master](#master)|Spécifie que seul le fil principal doit exécuter une section du programme.|
|[Critique](#critical)|Spécifie que le code n’est exécuté que sur un seul thread à la fois.|
|[barrier](#barrier)|Synchronise tous les fils d’une équipe; tous les fils s’arrêtent à la barrière, jusqu’à ce que tous les fils exécutent la barrière.|
|[atomique](#atomic)|Précise qu’un emplacement de mémoire qui sera mis à jour atomiquement.|
|[Rincer](#flush-openmp)|Spécifie que tous les threads ont la même vue de mémoire pour tous les objets partagés.|
|[Commandé](#ordered-openmp-directives)|Précise que le code sous `for` une boucle parallèle doit être exécuté comme une boucle séquentielle.|

Pour l’environnement de données :

|Directive|Description|
|---------|-----------|
|[threadprivate](#threadprivate)|Spécifie qu’une variable est privée à un thread.|

## <a name="atomic"></a><a name="atomic"></a>Atomique

Précise qu’un emplacement de mémoire qui sera mis à jour atomiquement.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
La déclaration qui a la *lvalue*, dont l’emplacement de mémoire que vous voulez protéger contre plus d’une écriture.

### <a name="remarks"></a>Notes

La `atomic` directive ne prévoit aucune clause.

Pour plus d’informations, voir [2.6.4 construction atomique](../../../parallel/openmp/2-6-4-atomic-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a><a name="barrier"></a>Barrière

Synchronise tous les fils d’une équipe; tous les fils s’arrêtent à la barrière, jusqu’à ce que tous les fils exécutent la barrière.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Notes

La `barrier` directive ne prévoit aucune clause.

Pour plus d’informations, voir [2.6.3 directive barrière](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Exemple

Pour un échantillon de `barrier`la façon d’utiliser , voir [maître](#master).

## <a name="critical"></a><a name="critical"></a>Critique

Spécifie que le code n’est exécuté que sur un thread à la fois.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*name*<br/>
(Facultatif) Un nom pour identifier le code critique. Le nom doit être inclus entre parenthèses.

### <a name="remarks"></a>Notes

La `critical` directive ne prévoit aucune clause.

Pour plus d’informations, voir [2.6.2 construction critique](../../../parallel/openmp/2-6-2-critical-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush"></a><a name="flush-openmp"></a>Rincer

Spécifie que tous les threads ont la même vue de mémoire pour tous les objets partagés.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Paramètres

*Var*<br/>
(Facultatif) Une liste de variables séparées par virgule qui représentent les objets que vous souhaitez synchroniser. Si *var* n’est pas spécifié, toute mémoire est rincée.

### <a name="remarks"></a>Notes

La `flush` directive ne prévoit aucune clause.

Pour plus d’informations, voir [2.6.5 directive flush](../../../parallel/openmp/2-6-5-flush-directive.md).

### <a name="example"></a>Exemple

```cpp
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for"></a><a name="for-openmp"></a> pour

Provoque le travail `for` effectué dans une boucle à l’intérieur d’une région parallèle à diviser entre les fils.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Paramètres

*Clauses*<br/>
(Facultatif) Zéro ou plus de clauses, voir la section **Remarques.**

*for_statement*<br/>
Une `for` boucle. Un comportement indéfini se traduira `for` si le code utilisateur dans la boucle modifie la variable de l’index.

### <a name="remarks"></a>Notes

La `for` directive soutient les clauses suivantes :

- [Privé](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [Commandé](openmp-clauses.md#ordered-openmp-clauses)
- [Horaire](openmp-clauses.md#schedule)
- [Nowait](openmp-clauses.md#nowait)

Si `parallel` elle est `clauses` également spécifiée, `parallel` peut `for` être `nowait`n’importe quelle clause acceptée par les directives ou les directives, sauf .

Pour plus d’informations, voir [2.4.1 pour la construction](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a><a name="master"></a>Maître

Spécifie que seul le fil principal doit exécuter une section du programme.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Notes

La `master` directive ne prévoit aucune clause.

La directive [unique](#single) vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, pas nécessairement le fil principal.

Pour plus d’informations, voir [2.6.1 master build](../../../parallel/openmp/2-6-1-master-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered"></a><a name="ordered-openmp-directives"></a>Commandé

Précise que le code sous `for` une boucle parallèle doit être exécuté comme une boucle séquentielle.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Notes

La `ordered` directive doit être dans l’étendue dynamique `ordered` d’un [pour](#for-openmp) ou `parallel for` d’une construction avec une clause.

La `ordered` directive ne prévoit aucune clause.

Pour plus d’informations, voir [2.6.6 construction commandée](../../../parallel/openmp/2-6-6-ordered-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a><a name="parallel"></a>Parallèle

Définit une région parallèle, qui est un code qui sera exécuté par plusieurs threads en parallèle.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*Clauses*<br/>
(Facultatif) Zéro ou plus de clauses, voir la section **Remarques.**

### <a name="remarks"></a>Notes

La `parallel` directive soutient les clauses suivantes :

- [if](openmp-clauses.md#if-openmp)
- [Privé](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [Partagé](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel`peut également être utilisé avec les directives [de for](#for-openmp) et [de sections.](#sections-openmp)

Pour plus d’informations, voir [2.3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Exemple

L’échantillon suivant montre comment définir le nombre de threads et définir une région parallèle. Le nombre de threads est égal par défaut au nombre de processeurs logiques sur la machine. Par exemple, si vous avez une machine avec un processeur physique qui a hyperthreading activé, il aura deux processeurs logiques et deux threads. L’ordre de sortie peut varier sur différentes machines.

```cpp
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

## <a name="sections"></a><a name="sections-openmp"></a>Sections

Identifie les sections de code à répartir entre tous les threads.

```cpp
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>Paramètres

*Clauses*<br/>
(Facultatif) Zéro ou plus de clauses, voir la section **Remarques.**

### <a name="remarks"></a>Notes

La `sections` directive peut contenir `section` zéro ou plus de directives.

La `sections` directive soutient les clauses suivantes :

- [Privé](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [Nowait](openmp-clauses.md#nowait)

Si `parallel` elle est `clauses` également spécifiée, `parallel` peut `sections` être `nowait`n’importe quelle clause acceptée par les directives ou les directives, sauf .

Pour plus d’informations, voir [2.4.2 sections construire](../../../parallel/openmp/2-4-2-sections-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a><a name="single"></a>Seul

Vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, pas nécessairement le fil maître.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*Clauses*<br/>
(Facultatif) Zéro ou plus de clauses, voir la section **Remarques.**

### <a name="remarks"></a>Notes

La `single` directive soutient les clauses suivantes :

- [Privé](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [Nowait](openmp-clauses.md#nowait)

La directive [principale](#master) vous permet de spécifier qu’une section de code ne doit être exécutée que sur le fil principal.

Pour plus d’informations, voir [2.4.3 construction unique](../../../parallel/openmp/2-4-3-single-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a><a name="threadprivate"></a>threadprivate

Spécifie qu’une variable est privée à un thread.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Paramètres

*Var*<br/>
Une liste de variables séparées par virgule que vous souhaitez faire du privé à un thread. *var* doit être soit une variable globale ou namespace-portée ou une variable statique locale.

### <a name="remarks"></a>Notes

La `threadprivate` directive ne prévoit aucune clause.

La `threadprivate` directive est basée sur l’attribut de [thread](../../../cpp/thread.md) à l’aide du mot clé [__declspec;](../../../cpp/declspec.md) limites `__declspec(thread)` sur `threadprivate`s’appliquer à . Par exemple, `threadprivate` une variable existera dans n’importe quel thread commencé dans le processus, pas seulement les fils qui font partie d’une équipe de thread engendrée par une région parallèle. Soyez conscient de ce détail de mise en œuvre; vous remarquerez peut-être `threadprivate` que les constructeurs d’un type défini par l’utilisateur sont appelés plus souvent que prévu.

Vous pouvez `threadprivate` utiliser dans un DLL qui est chargé statiquement `threadprivate` au démarrage de processus, mais vous ne pouvez pas utiliser dans n’importe quel DLL qui `LoadLibrary`sera chargé via [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) tels que DLLs qui sont chargés avec [/DELAYLOAD (importation de charge de retard)](../../../build/reference/delayload-delay-load-import.md), qui utilise également .

Une `threadprivate` variable d’un type *destructible* n’est pas garantie d’avoir son destructeur appelé. Par exemple :

```cpp
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

Les utilisateurs n’ont aucun contrôle quant au moment où les fils constituant la région parallèle se termineront. Si ces fils existent lorsque le processus sort, les fils ne seront pas informés de la sortie `threaded_var` du processus, et le destructeur ne sera pas appelé sur n’importe quel thread, sauf celui qui sort (ici, le fil principal). Donc, le code ne devrait `threadprivate` pas compter sur la destruction appropriée des variables.

Pour plus d’informations, voir [2.7.1 directive threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Exemple

Pour un échantillon `threadprivate`d’utilisation , voir [privé](openmp-clauses.md#private-openmp).
