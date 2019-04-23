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
- ordered
- parallel
- section
- SECTIONS
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
ms.openlocfilehash: d644b612c0c326692786c94046d799163dfbce8d
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124952"
---
# <a name="openmp-directives"></a>Directives OpenMP

Fournit des liens vers les directives utilisées dans l’API OpenMP.

Visual C++ prend en charge les directives OpenMP.

Pour la partage de travail parallèle :

|Directive|Description|
|---------|-----------|
|[parallel](#parallel)|Définit une région parallèle, ce qui est le code qui sera exécuté par plusieurs threads en parallèle.|
|[for](#for-openmp)|Provoque le travail effectué dans un `for` boucle à l’intérieur d’une région parallèle doit être divisé entre threads.|
|[sections](#sections-openmp)|Identifie les sections de code pour être réparti entre tous les threads.|
|[single](#single)|Vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, mais pas nécessairement le thread principal.|

Pour master et la synchronisation :

|Directive|Description|
|---------|-----------|
|[master](#master)|Spécifie que seul le thread principal doit exécuter une section du programme.|
|[critical](#critical)|Spécifie que code est exécuté uniquement sur un seul thread à la fois.|
|[barrier](#barrier)|Synchronise tous les threads dans une équipe. tous les threads suspendre à la barrière, jusqu'à ce que tous les threads exécuteront le cloisonnement.|
|[atomic](#atomic)|Spécifie qu’un emplacement de mémoire qui sera mis à jour atomiquement.|
|[flush](#flush-openmp)|Spécifie que tous les threads ont la même vue de mémoire pour tous les objets partagés.|
|[ordered](#ordered-openmp-directives)|Spécifie que le code sous une parallélisée `for` boucle doit être exécutée comme une boucle séquentielle.|

Pour l’environnement de données :

|Directive|Description|
|---------|-----------|
|[threadprivate](#threadprivate)|Spécifie qu’une variable est privée pour un thread.|

## <a name="atomic"></a>atomic

Spécifie qu’un emplacement de mémoire qui sera mis à jour atomiquement.

```
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
L’instruction qui a le *lvalue*, dont l’emplacement de mémoire que vous souhaitez protéger contre plusieurs écritures.

### <a name="remarks"></a>Notes

Le `atomic` directive prend en charge aucune clause.

Pour plus d’informations, consultez [2.6.4 atomique construire](../../../parallel/openmp/2-6-4-atomic-construct.md).

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

## <a name="barrier"></a>barrier

Synchronise tous les threads dans une équipe. tous les threads suspendre à la barrière, jusqu'à ce que tous les threads exécuteront le cloisonnement.

```
#pragma omp barrier
```

### <a name="remarks"></a>Notes

Le `barrier` directive prend en charge aucune clause.

Pour plus d’informations, consultez [2.6.3 directive de barrière](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser `barrier`, consultez [master](#master).

## <a name="critical"></a>critical

Spécifie que code est uniquement être exécuté sur un seul thread à la fois.

```
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*name*<br/>
(Facultatif) Un nom pour identifier le code critique. Le nom doit être placé entre parenthèses.

### <a name="remarks"></a>Notes

Le `critical` directive prend en charge aucune clause.

Pour plus d’informations, consultez [2.6.2 critiques construire](../../../parallel/openmp/2-6-2-critical-construct.md).

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

## <a name="flush-openmp"></a>flush

Spécifie que tous les threads ont la même vue de mémoire pour tous les objets partagés.

```
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Paramètres

*var*<br/>
(Facultatif) Une liste séparée par des virgules de variables qui représentent des objets que vous souhaitez synchroniser. Si *var* n’est pas spécifié, toute la mémoire est vidée.

### <a name="remarks"></a>Notes

Le `flush` directive prend en charge aucune clause.

Pour plus d’informations, consultez [2.6.5 directive flush](../../../parallel/openmp/2-6-5-flush-directive.md).

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

## <a name="for-openmp"></a>Pour

Provoque le travail effectué dans un `for` boucle à l’intérieur d’une région parallèle doit être divisé entre threads.

```
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Paramètres

*clauses*<br/>
(Facultatif) Zéro ou plusieurs clauses, consultez le **notes** section.

*for_statement*<br/>
Un `for` boucle. Un comportement non défini se produira si le code utilisateur dans le `for` boucle modifie la variable d’index.

### <a name="remarks"></a>Notes

Le `for` directive prend en charge les clauses suivantes :

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [ordered](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Si `parallel` est également spécifié, `clauses` peut être toute clause acceptée par le `parallel` ou `for` directives, à l’exception `nowait`.

Pour plus d’informations, consultez [2.4.1 construction for](../../../parallel/openmp/2-4-1-for-construct.md).

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

## <a name="master"></a>master

Spécifie que seul le thread principal doit exécuter une section du programme.

```
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Notes

Le `master` directive prend en charge aucune clause.

Le [unique](#single) directive vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, mais pas nécessairement le thread principal.

Pour plus d’informations, consultez [2.6.1 maître construction](../../../parallel/openmp/2-6-1-master-construct.md).

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

## <a name="ordered-openmp-directives"></a>ordered

Spécifie que le code sous une parallélisée `for` boucle doit être exécutée comme une boucle séquentielle.

```
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Notes

Le `ordered` directive doit se trouver dans l’étendue dynamique d’un [pour](#for-openmp) ou `parallel for` construire avec un `ordered` clause.

Le `ordered` directive prend en charge aucune clause.

Pour plus d’informations, consultez [2.6.6 construction ordered](../../../parallel/openmp/2-6-6-ordered-construct.md).

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

## <a name="parallel"></a>parallel

Définit une région parallèle, ce qui est le code qui sera exécuté par plusieurs threads en parallèle.

```
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*clauses*<br/>
(Facultatif) Zéro ou plusieurs clauses, consultez le **notes** section.

### <a name="remarks"></a>Notes

Le `parallel` directive prend en charge les clauses suivantes :

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [shared](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` peut également être utilisé avec le [pour](#for-openmp) et [sections](#sections-openmp) directives.

Pour plus d’informations, consultez [2.3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment définir le nombre de threads et de définir une région parallèle. Le nombre de threads équivaut au nombre de processeurs logiques sur l’ordinateur par défaut. Par exemple, si vous avez un ordinateur avec un processeur physique qui a l’hyperthreading est activé, il aura deux processeurs logiques et deux threads. L’ordre de sortie peut varier sur des ordinateurs différents.

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

## <a name="sections-openmp"></a>sections

Identifie les sections de code pour être réparti entre tous les threads.

```
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>Paramètres

*clauses*<br/>
(Facultatif) Zéro ou plusieurs clauses, consultez le **notes** section.

### <a name="remarks"></a>Notes

Le `sections` directive peut contenir zéro ou plusieurs `section` directives.

Le `sections` directive prend en charge les clauses suivantes :

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Si `parallel` est également spécifié, `clauses` peut être toute clause acceptée par le `parallel` ou `sections` directives, à l’exception `nowait`.

Pour plus d’informations, consultez [2.4.2 construction sections](../../../parallel/openmp/2-4-2-sections-construct.md).

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

## <a name="single"></a>single

Vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, mais pas nécessairement le thread principal.

```
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*clauses*<br/>
(Facultatif) Zéro ou plusieurs clauses, consultez le **notes** section.

### <a name="remarks"></a>Notes

Le `single` directive prend en charge les clauses suivantes :

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

Le [master](#master) directive vous permet de spécifier qu’une section de code doit être exécutée uniquement sur le thread principal.

Pour plus d’informations, consultez [2.4.3 unique construire](../../../parallel/openmp/2-4-3-single-construct.md).

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

## <a name="threadprivate"></a>threadprivate

Spécifie qu’une variable est privée pour un thread.

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Une liste séparée par des virgules des variables que vous souhaitez rendre privé à un thread. *var* doit être une variable globale ou espace de noms-portée ou une variable locale statique.

### <a name="remarks"></a>Notes

Le `threadprivate` directive prend en charge aucune clause.

Le `threadprivate` directive est basée sur le [thread](../../../cpp/thread.md) attribut à l’aide de la [__declspec](../../../cpp/declspec.md) mot clé ; limites sur `__declspec(thread)` s’appliquent à `threadprivate`. Par exemple, un `threadprivate` variable existera dans n’importe quel thread a démarré le processus, pas seulement les threads qui font partie d’une équipe de thread générée par une région parallèle. N’oubliez pas de ce détail d’implémentation ; Vous pouvez remarquer que les constructeurs pour un `threadprivate` type défini par l’utilisateur sont appelées plus souvent puis attendu.

Vous pouvez utiliser `threadprivate` cependant dans une DLL est chargée statiquement au démarrage du processus, vous ne pouvez pas utiliser `threadprivate` dans n’importe quelle DLL qui est chargée par le biais de [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya) tels que les DLL qui sont chargés avec [/DELAYLOAD (délai importation à chargement)](../../../build/reference/delayload-delay-load-import.md), qui utilise également `LoadLibrary`.

Un `threadprivate` variable d’un *destructible* ce type n’est pas garanti d’avoir son destructeur appelé. Exemple :

```
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

Les utilisateurs n’ont aucun contrôle quant à lorsque les threads qui constituent la région parallèle seront termine. Si ces threads existent lorsque le processus s’arrête, les threads ne sont pas notifier à propos de la sortie du processus, le destructeur ne sera pas appelé pour `threaded_var` sur n’importe quel thread à l’exception de celui qui se termine (ici, le thread principal). Afin de code ne doit pas compter sur la destruction correcte de `threadprivate` variables.

Pour plus d’informations, consultez [2.7.1 directive threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `threadprivate`, consultez [privé](openmp-clauses.md#private-openmp).
