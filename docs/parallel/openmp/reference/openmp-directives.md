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
ms.openlocfilehash: 4db341cf58884263e414e24aacf888c8c88e57cc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142017"
---
# <a name="openmp-directives"></a>Directives OpenMP

Fournit des liens vers les directives utilisées dans l’API OpenMP.

Visual C++ prend en charge les directives OpenMP suivantes.

Pour le partage de travail parallèle :

|Directive|Description|
|---------|-----------|
|[parallel](#parallel)|Définit une région parallèle, qui est le code qui sera exécuté par plusieurs threads en parallèle.|
|[for](#for-openmp)|Fait en sorte que le travail effectué dans une boucle `for` à l’intérieur d’une région parallèle soit divisé entre les threads.|
|[sections](#sections-openmp)|Identifie les sections de code qui doivent être réparties entre tous les threads.|
|[single](#single)|Vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, pas nécessairement le thread principal.|

Pour le maître et la synchronisation :

|Directive|Description|
|---------|-----------|
|[master](#master)|Spécifie que seul le thread principal doit exécuter une section du programme.|
|[critical](#critical)|Spécifie que le code est exécuté uniquement sur un thread à la fois.|
|[barrier](#barrier)|Synchronise tous les threads d’une équipe ; tous les threads sont suspendus au niveau du cloisonnement, jusqu’à ce que tous les threads exécutent le cloisonnement.|
|[atomic](#atomic)|Spécifie qu’un emplacement de mémoire sera mis à jour de manière atomique.|
|[flush](#flush-openmp)|Spécifie que tous les threads ont la même vue de mémoire pour tous les objets partagés.|
|[substitué](#ordered-openmp-directives)|Spécifie que le code d’une boucle de `for` parallélisée doit être exécuté comme une boucle séquentielle.|

Pour l’environnement de données :

|Directive|Description|
|---------|-----------|
|[threadprivate](#threadprivate)|Spécifie qu’une variable est privée pour un thread.|

## <a name="atomic"></a>atomique

Spécifie qu’un emplacement de mémoire sera mis à jour de manière atomique.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
Instruction qui contient la *lvalue*, dont l’emplacement de la mémoire doit être protégé par rapport à plus d’une écriture.

### <a name="remarks"></a>Notes

La directive `atomic` ne prend pas en charge les clauses.

Pour plus d’informations, consultez [construction atomique 2.6.4](../../../parallel/openmp/2-6-4-atomic-construct.md).

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

## <a name="barrier"></a>bloqué

Synchronise tous les threads d’une équipe ; tous les threads sont suspendus au niveau du cloisonnement, jusqu’à ce que tous les threads exécutent le cloisonnement.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Notes

La directive `barrier` ne prend pas en charge les clauses.

Pour plus d’informations, consultez [directive Barrier 2.6.3](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `barrier`, consultez [maître](#master).

## <a name="critical"></a>critique

Spécifie que le code est exécuté uniquement sur un thread à la fois.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*name*<br/>
Facultatif Nom permettant d’identifier le code critique. Le nom doit être placé entre parenthèses.

### <a name="remarks"></a>Notes

La directive `critical` ne prend pas en charge les clauses.

Pour plus d’informations, consultez [construction critique 2.6.2](../../../parallel/openmp/2-6-2-critical-construct.md).

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

## <a name="flush-openmp"></a>postconsommation

Spécifie que tous les threads ont la même vue de mémoire pour tous les objets partagés.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Facultatif Liste séparée par des virgules des variables qui représentent les objets que vous souhaitez synchroniser. Si *var* n’est pas spécifié, toute la mémoire est vidée.

### <a name="remarks"></a>Notes

La directive `flush` ne prend pas en charge les clauses.

Pour plus d’informations, consultez [la directive 2.6.5 Flush](../../../parallel/openmp/2-6-5-flush-directive.md).

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

## <a name="for-openmp"></a>pour

Fait en sorte que le travail effectué dans une boucle `for` à l’intérieur d’une région parallèle soit divisé entre les threads.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Paramètres

*clauses*<br/>
Facultatif Aucune ou plusieurs clauses, consultez la section **Notes** .

*for_statement*<br/>
Boucle `for`. Un comportement non défini se produit si le code utilisateur de la `for` boucle modifie la variable d’index.

### <a name="remarks"></a>Notes

La directive `for` prend en charge les clauses suivantes :

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [substitué](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Si `parallel` est également spécifié, `clauses` peut être toute clause acceptée par les directives `parallel` ou `for`, à l’exception de `nowait`.

Pour plus d’informations, consultez [2.4.1 for Construct](../../../parallel/openmp/2-4-1-for-construct.md).

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

## <a name="master"></a>Master

Spécifie que seul le thread principal doit exécuter une section du programme.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Notes

La directive `master` ne prend pas en charge les clauses.

La directive [unique](#single) vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, pas nécessairement le thread principal.

Pour plus d’informations, consultez la page [construction principale de 2.6.1](../../../parallel/openmp/2-6-1-master-construct.md).

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

## <a name="ordered-openmp-directives"></a>substitué

Spécifie que le code d’une boucle de `for` parallélisée doit être exécuté comme une boucle séquentielle.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Notes

La directive `ordered` doit se trouver dans l’étendue dynamique d’une construction [for](#for-openmp) ou `parallel for` avec une clause `ordered`.

La directive `ordered` ne prend pas en charge les clauses.

Pour plus d’informations, consultez [construction ordonnée 2.6.6](../../../parallel/openmp/2-6-6-ordered-construct.md).

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

## <a name="parallel"></a>égal

Définit une région parallèle, qui est le code qui sera exécuté par plusieurs threads en parallèle.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*clauses*<br/>
Facultatif Aucune ou plusieurs clauses, consultez la section **Notes** .

### <a name="remarks"></a>Notes

La directive `parallel` prend en charge les clauses suivantes :

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [partagé](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` peut également être utilisé avec [les directives](#sections-openmp) [for](#for-openmp) et.

Pour plus d’informations, consultez [2,3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment définir le nombre de threads et définir une région parallèle. Le nombre de threads est égal par défaut au nombre de processeurs logiques sur l’ordinateur. Par exemple, si vous avez un ordinateur avec un processeur physique pour lequel l’hyperthreading est activé, il aura deux processeurs logiques et deux threads. L’ordre de sortie peut varier sur des ordinateurs différents.

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

Identifie les sections de code qui doivent être réparties entre tous les threads.

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

*clauses*<br/>
Facultatif Aucune ou plusieurs clauses, consultez la section **Notes** .

### <a name="remarks"></a>Notes

La directive `sections` peut contenir zéro ou plusieurs directives `section`.

La directive `sections` prend en charge les clauses suivantes :

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Si `parallel` est également spécifié, `clauses` peut être toute clause acceptée par les directives `parallel` ou `sections`, à l’exception de `nowait`.

Pour plus d’informations, consultez [2.4.2 sections Construct](../../../parallel/openmp/2-4-2-sections-construct.md).

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

## <a name="single"></a>Single

Vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, pas nécessairement le thread principal.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Paramètres

*clauses*<br/>
Facultatif Aucune ou plusieurs clauses, consultez la section **Notes** .

### <a name="remarks"></a>Notes

La directive `single` prend en charge les clauses suivantes :

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

La directive [principale](#master) vous permet de spécifier qu’une section de code ne doit être exécutée que sur le thread principal.

Pour plus d’informations, consultez la section [2.4.3 simple Construct](../../../parallel/openmp/2-4-3-single-construct.md).

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

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Liste de variables séparées par des virgules que vous souhaitez rendre privées pour un thread. *var* doit être une variable de portée d’espace de noms ou globale ou une variable statique locale.

### <a name="remarks"></a>Notes

La directive `threadprivate` ne prend pas en charge les clauses.

La directive `threadprivate` est basée sur l’attribut de [thread](../../../cpp/thread.md) à l’aide du mot clé [__declspec](../../../cpp/declspec.md) ; les limites sur les `__declspec(thread)` s’appliquent à `threadprivate`. Par exemple, une variable `threadprivate` existe dans tout thread démarré dans le processus, pas seulement les threads qui font partie d’une équipe de threads générées par une région parallèle. Tenez compte de ces détails d’implémentation. vous pouvez remarquer que les constructeurs d’un type défini par l’utilisateur `threadprivate` sont plus souvent appelés.

Vous pouvez utiliser `threadprivate` dans une DLL qui est chargée statiquement au démarrage du processus, mais vous ne pouvez pas utiliser `threadprivate` dans une DLL qui sera chargée via [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) , comme les dll qui sont chargées avec [/delayload (différer le chargement de l’importation)](../../../build/reference/delayload-delay-load-import.md), qui utilise également `LoadLibrary`.

Il n’est pas garanti que son destructeur soit appelé pour une `threadprivate` variable d’un type *destructible* . Par exemple :

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

Les utilisateurs n’ont aucun contrôle sur le moment où les threads constituant la région parallèle se terminent. Si ces threads existent lorsque le processus se termine, les threads ne sont pas notifiés de la sortie du processus et le destructeur n’est pas appelé pour `threaded_var` sur un thread, sauf celui qui se termine (ici, le thread principal). Le code ne doit donc pas compter sur la destruction correcte des variables de `threadprivate`.

Pour plus d’informations, consultez [la directive 2.7.1 threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `threadprivate`, consultez [Private](openmp-clauses.md#private-openmp).
