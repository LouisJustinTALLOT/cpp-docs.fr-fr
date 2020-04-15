---
title: Clauses OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP clauses
- copyin
- copyprivate
- default
- firstprivate
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
ms.openlocfilehash: 1c4c7961a173eb47394d03e9aabdd14574e62b08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363899"
---
# <a name="openmp-clauses"></a>Clauses OpenMP

Fournit des liens vers des clauses utilisées dans l’API OpenMP.

Visual CMD prend en charge les clauses OpenMP suivantes.

Pour les attributs généraux :

|Clause|Description|
|------|-----------|
|[if](#if-openmp)|Précise si une boucle doit être exécutée en parallèle ou en série.|
|[num_threads](#num-threads)|Définit le nombre de threads dans une équipe de thread.|
|[Commandé](#ordered-openmp-clauses)|Exigé sur un parallèle [pour](openmp-directives.md#for-openmp) la déclaration si une directive [ordonnée](openmp-directives.md#ordered-openmp-directives) doit être utilisée dans la boucle.|
|[Horaire](#schedule)|S’applique à [la](openmp-directives.md#for-openmp) directive.|
|[Nowait](#nowait)|L’écarte la barrière implicite dans une directive.|

Pour les attributs de partage de données :

|Clause|Description|
|------|-----------|
|[Privé](#private-openmp)|Spécifie que chaque thread doit avoir sa propre instance d’une variable.|
|[firstprivate](#firstprivate)|Précise que chaque thread doit avoir sa propre instance d’une variable, et que la variable doit être paraminée avec la valeur de la variable, car elle existe avant la construction parallèle.|
|[lastprivate](#lastprivate)|Précise que la version du contexte ci-joint de la variable est définie à la même manière que la version privée du fil n’exécute l’itération finale (pour la construction en boucle) ou la dernière section (#pragma sections).|
|[Partagé](#shared-openmp)|Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.|
|[default](#default-openmp)|Spécifie le comportement des variables non tracées dans une région parallèle.|
|[reduction](#reduction)|Précise qu’une ou plusieurs variables privées à chaque thread font l’objet d’une opération de réduction à la fin de la région parallèle.|
|[copyin](#copyin)|Permet aux threads d’accéder à la valeur du fil de maître, pour une variable [threadprivate.](openmp-directives.md#threadprivate)|
|[copyprivate](#copyprivate)|Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.|

## <a name="copyin"></a><a name="copyin"></a>copyin (copyin)

Permet aux threads d’accéder à la valeur du fil de maître, pour une variable [threadprivate.](openmp-directives.md#threadprivate)

```cpp
copyin(var)
```

### <a name="parameters"></a>Paramètres

*Var*<br/>
La `threadprivate` variable qui sera pararalisée avec la valeur de la variable dans le fil principal, telle qu’elle existe avant la construction parallèle.

### <a name="remarks"></a>Notes

`copyin`s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, voir [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).

### <a name="example"></a>Exemple

Voir [threadprivate](openmp-directives.md#threadprivate) pour un `copyin`exemple d’utilisation .

## <a name="copyprivate"></a><a name="copyprivate"></a>copyprivate

Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.

```cpp
copyprivate(var)
```

### <a name="parameters"></a>Paramètres

*Var*<br/>
Une ou plusieurs variables à partager. Si plus d’une variable est spécifiée, séparez les noms variables avec une virgule.

### <a name="remarks"></a>Notes

`copyprivate`s’applique à la directive [unique.](openmp-directives.md#single)

Pour plus d’informations, voir [2.7.2.8 copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md).

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

## <a name="default"></a><a name="default-openmp"></a>Par défaut

Spécifie le comportement des variables non tracées dans une région parallèle.

```cpp
default(shared | none)
```

### <a name="remarks"></a>Notes

`shared`, qui est en `default` vigueur si la clause n’est pas précisée, signifie que toute variable dans une région parallèle sera traitée comme si elle avait été spécifiée avec la clause [partagée.](#shared-openmp) `none`signifie que toutes les variables utilisées dans une région parallèle qui ne sont pas portées avec le [privé](#private-openmp), [partagé](#shared-openmp), [réduction](#reduction), [premier privé](#firstprivate), ou dernière clause [privée](#lastprivate) provoquera une erreur de compilateur.

`default`s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, voir [2.7.2.5 par défaut](../../../parallel/openmp/2-7-2-5-default.md).

### <a name="example"></a>Exemple

Voir [privé](#private-openmp) par exemple `default`d’utilisation .

## <a name="firstprivate"></a><a name="firstprivate"></a>firstprivate

Précise que chaque thread doit avoir sa propre instance d’une variable, et que la variable doit être paraminée avec la valeur de la variable, car elle existe avant la construction parallèle.

```cpp
firstprivate(var)
```

### <a name="parameters"></a>Paramètres

*Var*<br/>
La variable d’avoir des instances dans chaque thread et qui sera parasélisée avec la valeur de la variable, car elle existe avant la construction parallèle. Si plus d’une variable est spécifiée, séparez les noms variables avec une virgule.

### <a name="remarks"></a>Notes

`firstprivate`s’applique aux directives suivantes :

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Pour plus d’informations, voir [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).

### <a name="example"></a>Exemple

Par exemple d’utiliser `firstprivate`, voir l’exemple en [privé](#private-openmp).

## <a name="if-openmp"></a><a name="if-openmp"></a>si (OpenMP)

Précise si une boucle doit être exécutée en parallèle ou en série.

```cpp
if(expression)
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
Une expression intégrale qui, si elle évalue à vrai (non zéro), provoque le code dans la région parallèle à exécuter en parallèle. Si l’expression s’évalue à faux (zéro), la région parallèle est exécutée en série (par un seul thread).

### <a name="remarks"></a>Notes

`if`s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, voir [2.3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

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

## <a name="lastprivate"></a><a name="lastprivate"></a>lastprivate

Précise que la version du contexte ci-joint de la variable est définie à la même manière que la version privée du fil n’exécute l’itération finale (pour la construction en boucle) ou la dernière section (#pragma sections).

```cpp
lastprivate(var)
```

### <a name="parameters"></a>Paramètres

*Var*<br/>
La variable qui est définie à égalité avec la version privée du thread n’exécute l’itération finale (pour la construction en boucle) ou la dernière section (#pragma sections).

### <a name="remarks"></a>Notes

`lastprivate`s’applique aux directives suivantes :

- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, voir [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).

### <a name="example"></a>Exemple

Voir [l’horaire](#schedule) pour `lastprivate` un exemple d’utilisation de la clause.

## <a name="nowait"></a><a name="nowait"></a>Nowait

L’écarte la barrière implicite dans une directive.

```cpp
nowait
```

### <a name="remarks"></a>Notes

`nowait`s’applique aux directives suivantes :

- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Pour plus d’informations, voir [2.4.1 pour la construction](../../../parallel/openmp/2-4-1-for-construct.md), [2.4.2 sections construire](../../../parallel/openmp/2-4-2-sections-construct.md), et [2.4.3 construction unique](../../../parallel/openmp/2-4-3-single-construct.md).

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

## <a name="num_threads"></a><a name="num-threads"></a>num_threads

Définit le nombre de threads dans une équipe de thread.

```cpp
num_threads(num)
```

### <a name="parameters"></a>Paramètres

*num*<br/>
Le nombre de threads

### <a name="remarks"></a>Notes

La `num_threads` clause a la même fonctionnalité que la fonction [omp_set_num_threads.](openmp-functions.md#omp-set-num-threads)

`num_threads`s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, voir [2.3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Exemple

Voir [parallèle](openmp-directives.md#parallel) par exemple `num_threads` d’utilisation de la clause.

## <a name="ordered"></a><a name="ordered-openmp-clauses"></a>Commandé

Exigé sur un parallèle [pour](openmp-directives.md#for-openmp) la déclaration si une directive [ordonnée](openmp-directives.md#ordered-openmp-directives) doit être utilisée dans la boucle.

```cpp
ordered
```

### <a name="remarks"></a>Notes

`ordered`s’applique à [la](openmp-directives.md#for-openmp) directive.

Pour plus d’informations, voir [2.4.1 pour la construction](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Exemple

Voir [commandé](openmp-directives.md#ordered-openmp-directives) par exemple `ordered` d’utilisation de clause.

## <a name="private"></a><a name="private-openmp"></a>Privé

Spécifie que chaque thread doit avoir sa propre instance d’une variable.

```cpp
private(var)
```

### <a name="parameters"></a>Paramètres

*Var*<br/>
La variable d’avoir des instances dans chaque thread.

### <a name="remarks"></a>Notes

`private`s’applique aux directives suivantes :

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Pour plus d’informations, voir [2.7.2.1 privé](../../../parallel/openmp/2-7-2-1-private.md).

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

## <a name="reduction"></a><a name="reduction"></a>Réduction

Précise qu’une ou plusieurs variables privées à chaque thread font l’objet d’une opération de réduction à la fin de la région parallèle.

```cpp
reduction(operation:var)
```

### <a name="parameters"></a>Paramètres

*Opération*<br/>
L’opérateur pour l’opération à faire sur les variables *var* à la fin de la région parallèle.

*Var*<br/>
Une ou plusieurs variables sur lesquelles faire la réduction scalaire. Si plus d’une variable est spécifiée, séparez les noms variables avec une virgule.

### <a name="remarks"></a>Notes

`reduction`s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, voir [2.7.2.6 réduction](../../../parallel/openmp/2-7-2-6-reduction.md).

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

## <a name="schedule"></a><a name="schedule"></a>Horaire

S’applique à [la](openmp-directives.md#for-openmp) directive.

```cpp
schedule(type[,size])
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Le genre d’horaire, `runtime`soit `static` `dynamic`, `guided`, , ou .

*Taille*<br/>
(Facultatif) Spécifie la taille des itérations. *la taille* doit être un intégrant. Non valide lorsque `runtime`le *type* est .

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [2.4.1 pour la construction](../../../parallel/openmp/2-4-1-for-construct.md).

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

## <a name="shared"></a><a name="shared-openmp"></a>Partagé

Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.

```cpp
shared(var)
```

### <a name="parameters"></a>Paramètres

*Var*<br/>
Une ou plusieurs variables à partager. Si plus d’une variable est spécifiée, séparez les noms variables avec une virgule.

### <a name="remarks"></a>Notes

Une autre façon de partager les variables entre les threads est avec la clause [copyprivate.](#copyprivate)

`shared`s’applique aux directives suivantes :

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

Pour plus d’informations, voir [2.7.2.4 partagé](../../../parallel/openmp/2-7-2-4-shared.md).

### <a name="example"></a>Exemple

Voir [privé](#private-openmp) par exemple `shared`d’utilisation .
