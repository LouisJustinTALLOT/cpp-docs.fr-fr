---
title: Clauses OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP clauses
- copyin
- copyprivate
- default
- firstprivate
- if
- lastprivate
- nowait
- num_threads
- ordered
- private
- reduction
- schedule
- shared
helpviewer_keywords:
- OpenMP clauses
- copyin OpenMP clause
- copyprivate OpenMP clause
- default OpenMP clause
- defaults, OpenMP clause
- firstprivate OpenMP clause
- if OpenMP clause
- lastprivate OpenMP clause
- nowait OpenMP clause
- num_threads OpenMP clause
- ordered OpenMP clause
- private OpenMP clause
- reduction OpenMP clause
- schedule OpenMP clause
- shared OpenMP clause
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
ms.openlocfilehash: 92bd73fda5891b0bbf7393d1a7fda573d0f00263
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882898"
---
# <a name="openmp-clauses"></a>Clauses OpenMP

Fournit des liens vers des clauses utilisées dans l’API OpenMP.

Visual C++ prend en charge les clauses OpenMP suivantes.

Pour les attributs généraux :

|Clause|Description|
|------|-----------|
|[if](#if-openmp)|Spécifie si une boucle doit être exécutée en parallèle ou en série.|
|[num_threads](#num-threads)|Définit le nombre de threads dans une équipe de threads.|
|[substitué](#ordered-openmp-clauses)|Obligatoire sur une instruction Parallel [for](openmp-directives.md#for-openmp) si une directive [ordered](openmp-directives.md#ordered-openmp-directives) doit être utilisée dans la boucle.|
|[schedule](#schedule)|S’applique à la directive [for](openmp-directives.md#for-openmp) .|
|[nowait](#nowait)|Remplace la barrière implicite dans une directive.|

Pour les attributs de partage de données :

|Clause|Description|
|------|-----------|
|[private](#private-openmp)|Spécifie que chaque thread doit avoir sa propre instance d’une variable.|
|[firstprivate](#firstprivate)|Spécifie que chaque thread doit avoir sa propre instance d’une variable, et que la variable doit être initialisée avec la valeur de la variable, car elle existe avant la construction parallèle.|
|[lastprivate](#lastprivate)|Spécifie que la version du contexte englobant de la variable est égale à la version privée de quel thread exécute la dernière itération (construction de boucle) ou dernière section (#pragma sections).|
|[partagé](#shared-openmp)|Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.|
|[default](#default-openmp)|Spécifie le comportement des variables non délimitées dans une région parallèle.|
|[reduction](#reduction)|Spécifie qu’une ou plusieurs variables qui sont privées pour chaque thread font l’objet d’une opération de réduction à la fin de la région parallèle.|
|[copyin](#copyin)|Permet aux threads d’accéder à la valeur du thread principal, pour une variable [threadprivate](openmp-directives.md#threadprivate) .|
|[copyprivate](#copyprivate)|Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.|

## <a name="copyin"></a>copyin

Permet aux threads d’accéder à la valeur du thread principal, pour une variable [threadprivate](openmp-directives.md#threadprivate) .

```cpp
copyin(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
`threadprivate` variable qui sera initialisée avec la valeur de la variable dans le thread principal, telle qu’elle existe avant la construction parallèle.

### <a name="remarks"></a>Notes

`copyin` s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, consultez [copie 2.7.2.7](../../../parallel/openmp/2-7-2-7-copyin.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `copyin`, consultez [threadprivate](openmp-directives.md#threadprivate) .

## <a name="copyprivate"></a>copyprivate

Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.

```cpp
copyprivate(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Une ou plusieurs variables à partager. Si plusieurs variables sont spécifiées, séparez les noms des variables par une virgule.

### <a name="remarks"></a>Notes

`copyprivate` s’applique à la directive [unique](openmp-directives.md#single) .

Pour plus d’informations, consultez [2.7.2.8 copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md).

### <a name="example"></a>Exemple

```cpp
// omp_copyprivate.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

float x, y, fGlobal = 1.0;
#pragma omp threadprivate(x, y)

float get_float() {
   fGlobal += 0.001;
   return fGlobal;
}

void use_float(float f, int t) {
   printf_s("Value = %f, thread = %d\n", f, t);
}

void CopyPrivate(float a, float b) {
   #pragma omp single copyprivate(a, b, x, y)
   {
      a = get_float();
      b = get_float();
      x = get_float();
      y = get_float();
    }

   use_float(a, omp_get_thread_num());
   use_float(b, omp_get_thread_num());
   use_float(x, omp_get_thread_num());
   use_float(y, omp_get_thread_num());
}

int main() {
   float a = 9.99, b = 123.456;

   printf_s("call CopyPrivate from a single thread\n");
   CopyPrivate(9.99, 123.456);

   printf_s("call CopyPrivate from a parallel region\n");
   #pragma omp parallel
   {
      CopyPrivate(a, b);
   }
}
```

```Output
call CopyPrivate from a single thread
Value = 1.001000, thread = 0
Value = 1.002000, thread = 0
Value = 1.003000, thread = 0
Value = 1.004000, thread = 0
call CopyPrivate from a parallel region
Value = 1.005000, thread = 0
Value = 1.005000, thread = 1
Value = 1.006000, thread = 0
Value = 1.006000, thread = 1
Value = 1.007000, thread = 0
Value = 1.007000, thread = 1
Value = 1.008000, thread = 0
Value = 1.008000, thread = 1
```

## <a name="default-openmp"></a>valeurs

Spécifie le comportement des variables non délimitées dans une région parallèle.

```cpp
default(shared | none)
```

### <a name="remarks"></a>Notes

`shared`, qui est en vigueur si la clause `default` n’est pas spécifiée, signifie que toute variable dans une région parallèle sera traitée comme si elle était spécifiée avec la clause [Shared](#shared-openmp) . `none` signifie que toutes les variables utilisées dans une région parallèle qui ne sont pas délimitées par la clause [Private](#private-openmp), [Shared](#shared-openmp), [Reduction](#reduction), [firstprivate](#firstprivate)ou [lastprivate](#lastprivate) entraînent une erreur du compilateur.

`default` s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, consultez [2.7.2.5 default](../../../parallel/openmp/2-7-2-5-default.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `default`, consultez [Private](#private-openmp) .

## <a name="firstprivate"></a>firstprivate

Spécifie que chaque thread doit avoir sa propre instance d’une variable, et que la variable doit être initialisée avec la valeur de la variable, car elle existe avant la construction parallèle.

```cpp
firstprivate(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Variable qui doit avoir des instances dans chaque thread et qui sera initialisée avec la valeur de la variable, car elle existe avant la construction parallèle. Si plusieurs variables sont spécifiées, séparez les noms des variables par une virgule.

### <a name="remarks"></a>Notes

`firstprivate` s’applique aux directives suivantes :

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Pour plus d’informations, consultez [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `firstprivate`, consultez l’exemple dans [Private](#private-openmp).

## <a name="if-openmp"></a>if (OpenMP)

Spécifie si une boucle doit être exécutée en parallèle ou en série.

```cpp
if(expression)
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
Expression intégrale qui, si elle prend la valeur true (différente de zéro), provoque l’exécution en parallèle du code dans la région parallèle. Si l’expression prend la valeur false (zéro), la région parallèle est exécutée en série (par un seul thread).

### <a name="remarks"></a>Notes

`if` s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, consultez [2,3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="lastprivate"></a>lastprivate

Spécifie que la version du contexte englobant de la variable est égale à la version privée de quel thread exécute la dernière itération (construction de boucle) ou dernière section (#pragma sections).

```cpp
lastprivate(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Variable qui est définie comme étant égale à la version privée de quel thread exécute la dernière itération (construction de boucle) ou dernière section (#pragma sections).

### <a name="remarks"></a>Notes

`lastprivate` s’applique aux directives suivantes :

- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, consultez [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la clause `lastprivate`, consultez [Schedule](#schedule) .

## <a name="nowait"></a>NOWAIT

Remplace la barrière implicite dans une directive.

```cpp
nowait
```

### <a name="remarks"></a>Notes

`nowait` s’applique aux directives suivantes :

- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Pour plus d’informations, consultez [2.4.1 pour la construction](../../../parallel/openmp/2-4-1-for-construct.md), [2.4.2 sections Construct](../../../parallel/openmp/2-4-2-sections-construct.md)et [2.4.3 unique Construct](../../../parallel/openmp/2-4-3-single-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="num-threads"></a>num_threads

Définit le nombre de threads dans une équipe de threads.

```cpp
num_threads(num)
```

### <a name="parameters"></a>Paramètres

*num*<br/>
Nombre de threads

### <a name="remarks"></a>Notes

La clause `num_threads` a les mêmes fonctionnalités que la fonction [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) .

`num_threads` s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, consultez [2,3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la clause `num_threads`, consultez [Parallel](openmp-directives.md#parallel) .

## <a name="ordered-openmp-clauses"></a>substitué

Obligatoire sur une instruction Parallel [for](openmp-directives.md#for-openmp) si une directive [ordered](openmp-directives.md#ordered-openmp-directives) doit être utilisée dans la boucle.

```cpp
ordered
```

### <a name="remarks"></a>Notes

`ordered` s’applique à la directive [for](openmp-directives.md#for-openmp) .

Pour plus d’informations, consultez [2.4.1 for Construct](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la clause `ordered`, [consultez ordered](openmp-directives.md#ordered-openmp-directives) .

## <a name="private-openmp"></a>priv

Spécifie que chaque thread doit avoir sa propre instance d’une variable.

```cpp
private(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Variable qui doit avoir des instances dans chaque thread.

### <a name="remarks"></a>Notes

`private` s’applique aux directives suivantes :

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Pour plus d’informations, consultez [2.7.2.1 Private](../../../parallel/openmp/2-7-2-1-private.md).

### <a name="example"></a>Exemple

```c
// openmp_private.c
// compile with: /openmp
#include <windows.h>
#include <assert.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SLEEP_THREAD 1
#define NUM_LOOPS 2

enum Types {
   ThreadPrivate,
   Private,
   FirstPrivate,
   LastPrivate,
   Shared,
   MAX_TYPES
};

int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};
int nThreadPrivate;

#pragma omp threadprivate(nThreadPrivate)
#pragma warning(disable:4700)

int main() {
   int nPrivate = NUM_THREADS;
   int nFirstPrivate = NUM_THREADS;
   int nLastPrivate = NUM_THREADS;
   int nShared = NUM_THREADS;
   int nRet = 0;
   int i;
   int j;
   int nLoop = 0;

   nThreadPrivate = NUM_THREADS;
   printf_s("These are the variables before entry "
           "into the parallel region.\n");
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);
   printf_s("      nPrivate = %d\n", nPrivate);
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d\n", nLastPrivate);
   printf_s("       nShared = %d\n\n", nShared);
   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)
   {
      #pragma omp for schedule(static) lastprivate(nLastPrivate)
      for (i = 0 ; i < NUM_THREADS ; ++i) {
         for (j = 0 ; j < NUM_LOOPS ; ++j) {
            int nThread = omp_get_thread_num();
            assert(nThread < NUM_THREADS);

            if (nThread == SLEEP_THREAD)
               Sleep(100);
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;
            nSave[nThread][Private][j] = nPrivate;
            nSave[nThread][Shared][j] = nShared;
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;
            nSave[nThread][LastPrivate][j] = nLastPrivate;
            nThreadPrivate = nThread;
            nPrivate = nThread;
            nShared = nThread;
            nLastPrivate = nThread;
            --nFirstPrivate;
         }
      }
   }

   for (i = 0 ; i < NUM_LOOPS ; ++i) {
      for (j = 0 ; j < NUM_THREADS ; ++j) {
         printf_s("These are the variables at entry of "
                  "loop %d of thread %d.\n", i + 1, j);
         printf_s("nThreadPrivate = %d\n",
                  nSave[j][ThreadPrivate][i]);
         printf_s("      nPrivate = %d\n",
                  nSave[j][Private][i]);
         printf_s(" nFirstPrivate = %d\n",
                  nSave[j][FirstPrivate][i]);
         printf_s("  nLastPrivate = %d\n",
                  nSave[j][LastPrivate][i]);
         printf_s("       nShared = %d\n\n",
                  nSave[j][Shared][i]);
      }
   }

   printf_s("These are the variables after exit from "
            "the parallel region.\n");
   printf_s("nThreadPrivate = %d (The last value in the "
            "master thread)\n", nThreadPrivate);
   printf_s("      nPrivate = %d (The value prior to "
            "entering parallel region)\n", nPrivate);
   printf_s(" nFirstPrivate = %d (The value prior to "
            "entering parallel region)\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d (The value from the "
            "last iteration of the loop)\n", nLastPrivate);
   printf_s("       nShared = %d (The value assigned, "
            "from the delayed thread, %d)\n\n",
            nShared, SLEEP_THREAD);
}
```

```Output
These are the variables before entry into the parallel region.
nThreadPrivate = 4
      nPrivate = 4
nFirstPrivate = 4
  nLastPrivate = 4
       nShared = 4

These are the variables at entry of loop 1 of thread 0.
nThreadPrivate = 4
      nPrivate = 1310720
nFirstPrivate = 4
  nLastPrivate = 1245104
       nShared = 3

These are the variables at entry of loop 1 of thread 1.
nThreadPrivate = 4
      nPrivate = 4488
nFirstPrivate = 4
  nLastPrivate = 19748
       nShared = 0

These are the variables at entry of loop 1 of thread 2.
nThreadPrivate = 4
      nPrivate = -132514848
nFirstPrivate = 4
  nLastPrivate = -513199792
       nShared = 4

These are the variables at entry of loop 1 of thread 3.
nThreadPrivate = 4
      nPrivate = 1206
nFirstPrivate = 4
  nLastPrivate = 1204
       nShared = 2

These are the variables at entry of loop 2 of thread 0.
nThreadPrivate = 0
      nPrivate = 0
nFirstPrivate = 3
  nLastPrivate = 0
       nShared = 0

These are the variables at entry of loop 2 of thread 1.
nThreadPrivate = 1
      nPrivate = 1
nFirstPrivate = 3
  nLastPrivate = 1
       nShared = 1

These are the variables at entry of loop 2 of thread 2.
nThreadPrivate = 2
      nPrivate = 2
nFirstPrivate = 3
  nLastPrivate = 2
       nShared = 2

These are the variables at entry of loop 2 of thread 3.
nThreadPrivate = 3
      nPrivate = 3
nFirstPrivate = 3
  nLastPrivate = 3
       nShared = 3

These are the variables after exit from the parallel region.
nThreadPrivate = 0 (The last value in the master thread)
      nPrivate = 4 (The value prior to entering parallel region)
nFirstPrivate = 4 (The value prior to entering parallel region)
  nLastPrivate = 3 (The value from the last iteration of the loop)
       nShared = 1 (The value assigned, from the delayed thread, 1)
```

## <a name="reduction"></a>applicables

Spécifie qu’une ou plusieurs variables qui sont privées pour chaque thread font l’objet d’une opération de réduction à la fin de la région parallèle.

```cpp
reduction(operation:var)
```

### <a name="parameters"></a>Paramètres

*opération*<br/>
Opérateur pour l’opération à effectuer sur les variables *var* à la fin de la région parallèle.

*var*<br/>
Une ou plusieurs variables sur lesquelles la réduction scalaire doit être effectuée. Si plusieurs variables sont spécifiées, séparez les noms des variables par une virgule.

### <a name="remarks"></a>Notes

`reduction` s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, consultez [réduction de 2.7.2.6](../../../parallel/openmp/2-7-2-6-reduction.md).

### <a name="example"></a>Exemple

```cpp
// omp_reduction.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SUM_START   1
#define SUM_END     10
#define FUNC_RETS   {1, 1, 1, 1, 1}

int bRets[5] = FUNC_RETS;
int nSumCalc = ((SUM_START + SUM_END) * (SUM_END - SUM_START + 1)) / 2;

int func1( ) {return bRets[0];}
int func2( ) {return bRets[1];}
int func3( ) {return bRets[2];}
int func4( ) {return bRets[3];}
int func5( ) {return bRets[4];}

int main( )
{
    int nRet = 0,
        nCount = 0,
        nSum = 0,
        i,
        bSucceed = 1;

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel reduction(+ : nCount)
    {
        nCount += 1;

        #pragma omp for reduction(+ : nSum)
        for (i = SUM_START ; i <= SUM_END ; ++i)
            nSum += i;

        #pragma omp sections reduction(&& : bSucceed)
        {
            #pragma omp section
            {
                bSucceed = bSucceed && func1( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func2( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func3( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func4( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func5( );
            }
        }
    }

    printf_s("The parallel section was executed %d times "
             "in parallel.\n", nCount);
    printf_s("The sum of the consecutive integers from "
             "%d to %d, is %d\n", 1, 10, nSum);

    if (bSucceed)
        printf_s("All of the functions, func1 through "
                 "func5 succeeded!\n");
    else
        printf_s("One or more of the functions, func1 "
                 "through func5 failed!\n");

    if (nCount != NUM_THREADS)
    {
        printf_s("ERROR: For %d threads, %d were counted!\n",
                 NUM_THREADS, nCount);
        nRet |= 0x1;
   }

    if (nSum != nSumCalc)
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                "but %d was reported!\n",
                SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x10;
    }

    if (bSucceed != (bRets[0] && bRets[1] &&
                     bRets[2] && bRets[3] && bRets[4]))
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                 "but %d was reported!\n",
                 SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x100;
    }
}
```

```Output
The parallel section was executed 4 times in parallel.
The sum of the consecutive integers from 1 to 10, is 55
All of the functions, func1 through func5 succeeded!
```

## <a name="schedule"></a>programmateur

S’applique à la directive [for](openmp-directives.md#for-openmp) .

```cpp
schedule(type[,size])
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Type de planification, `dynamic`, `guided`, `runtime`ou `static`.

*size*<br/>
Facultatif Spécifie la taille des itérations. la *taille* doit être un entier. Non valide lorsque le *type* est `runtime`.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [2.4.1 for Construct](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Exemple

```cpp
// omp_schedule.cpp
// compile with: /openmp
#include <windows.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define STATIC_CHUNK 5
#define DYNAMIC_CHUNK 5
#define NUM_LOOPS 20
#define SLEEP_EVERY_N 3

int main( )
{
    int nStatic1[NUM_LOOPS],
        nStaticN[NUM_LOOPS];
    int nDynamic1[NUM_LOOPS],
        nDynamicN[NUM_LOOPS];
    int nGuided[NUM_LOOPS];

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel
    {
        #pragma omp for schedule(static, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStatic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(static, STATIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStaticN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, DYNAMIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamicN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(guided)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nGuided[i] = omp_get_thread_num( );
        }
    }

    printf_s("------------------------------------------------\n");
    printf_s("| static | static | dynamic | dynamic | guided |\n");
    printf_s("|    1   |    %d   |    1    |    %d    |        |\n",
             STATIC_CHUNK, DYNAMIC_CHUNK);
    printf_s("------------------------------------------------\n");

    for (int i=0; i<NUM_LOOPS; ++i)
    {
        printf_s("|    %d   |    %d   |    %d    |    %d    |"
                 "    %d   |\n",
                 nStatic1[i], nStaticN[i],
                 nDynamic1[i], nDynamicN[i], nGuided[i]);
    }

    printf_s("------------------------------------------------\n");
}
```

```Output
------------------------------------------------
| static | static | dynamic | dynamic | guided |
|    1   |    5   |    1    |    5    |        |
------------------------------------------------
|    0   |    0   |    0    |    2    |    1   |
|    1   |    0   |    3    |    2    |    1   |
|    2   |    0   |    3    |    2    |    1   |
|    3   |    0   |    3    |    2    |    1   |
|    0   |    0   |    2    |    2    |    1   |
|    1   |    1   |    2    |    3    |    3   |
|    2   |    1   |    2    |    3    |    3   |
|    3   |    1   |    0    |    3    |    3   |
|    0   |    1   |    0    |    3    |    3   |
|    1   |    1   |    0    |    3    |    2   |
|    2   |    2   |    1    |    0    |    2   |
|    3   |    2   |    1    |    0    |    2   |
|    0   |    2   |    1    |    0    |    3   |
|    1   |    2   |    2    |    0    |    3   |
|    2   |    2   |    2    |    0    |    0   |
|    3   |    3   |    2    |    1    |    0   |
|    0   |    3   |    3    |    1    |    1   |
|    1   |    3   |    3    |    1    |    1   |
|    2   |    3   |    3    |    1    |    1   |
|    3   |    3   |    0    |    1    |    3   |
------------------------------------------------
```

## <a name="shared-openmp"></a>partagé

Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.

```cpp
shared(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Une ou plusieurs variables à partager. Si plusieurs variables sont spécifiées, séparez les noms des variables par une virgule.

### <a name="remarks"></a>Notes

Une autre façon de partager des variables entre les threads est d’utiliser la clause [copyprivate](#copyprivate) .

`shared` s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, consultez [2.7.2.4 Shared](../../../parallel/openmp/2-7-2-4-shared.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `shared`, consultez [Private](#private-openmp) .
