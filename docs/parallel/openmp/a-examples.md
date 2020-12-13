---
description: 'En savoir plus sur : A. exemples'
title: R. Exemples
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: d52b59f9f83cf791c03fb49ca726273a2c977e58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342541"
---
# <a name="a-examples"></a>R. Exemples

Voici quelques exemples des constructions définies dans ce document. Une instruction qui suit une directive est composée uniquement lorsque cela est nécessaire, et une instruction non composée est mise en retrait d’une directive qui la précède.

## <a name="a1-a-simple-loop-in-parallel"></a>A. 1 une boucle simple en parallèle

L’exemple suivant montre comment paralléliser une boucle à l’aide de la directive [Parallel for](2-directives.md#251-parallel-for-construct) . La variable d’itération de la boucle est privée par défaut. il n’est donc pas nécessaire de la spécifier explicitement dans une clause Private.

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>A. 2 compilation conditionnelle

Les exemples suivants illustrent l’utilisation de la compilation conditionnelle à l’aide de la [_OPENMP](2-directives.md#22-conditional-compilation)de macro OpenMP. Avec la compilation OpenMP, la `_OPENMP` macro devient définie.

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

L’opérateur de préprocesseur défini permet à plusieurs macros d’être testées dans une seule directive.

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>A. 3 régions parallèles

La directive [Parallel](2-directives.md#23-parallel-construct) peut être utilisée dans des programmes parallèles de granularité grossière. Dans l’exemple suivant, chaque thread de la région parallèle détermine la partie du tableau global `x` à utiliser, en fonction du numéro de thread :

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>A. 4 la clause NOWAIT

S’il existe de nombreuses boucles indépendantes dans une région parallèle, vous pouvez utiliser la clause [NOWAIT](2-directives.md#241-for-construct) pour éviter le cloisonnement implicite à la fin de la `for` directive, comme suit :

```cpp
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```

## <a name="a5-the-critical-directive"></a>A. 5 la directive critique

L’exemple suivant comprend plusieurs directives [critiques](2-directives.md#262-critical-construct) . L’exemple illustre un modèle de mise en file d’attente dans lequel une tâche est déplacée dans la file d’attente et utilisée. Pour se protéger contre de nombreux threads qui défilent la même tâche, l’opération de défile d’attente doit être dans une `critical` section. Étant donné que les deux files d’attente de cet exemple sont indépendantes, elles sont protégées par des `critical` directives avec des noms différents, *XAXIS* et *YAxis*.

```cpp
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```

## <a name="a6-the-lastprivate-clause"></a>A. 6 la clause lastprivate

Une exécution correcte dépend parfois de la valeur que la dernière itération d’une boucle affecte à une variable. Ces programmes doivent répertorier toutes les variables de ce type comme arguments d’une clause [lastprivate](2-directives.md#2723-lastprivate) afin que les valeurs des variables soient les mêmes que lorsque la boucle est exécutée de manière séquentielle.

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

Dans l’exemple précédent, la valeur de `i` à la fin de la région parallèle est égale à `n-1` , comme dans le cas séquentiel.

## <a name="a7-the-reduction-clause"></a>A. 7 la clause Reduction

L’exemple suivant illustre la clause [Reduction](2-directives.md#2726-reduction) :

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>A. 8 sections parallèles

Dans l’exemple suivant (pour la [section 2.4.2](2-directives.md#242-sections-construct)), les fonctions *XAXIS*, *YAxis* et *Zaxis* peuvent être exécutées simultanément. La première `section` directive est facultative.  Toutes les `section` directives doivent apparaître dans l’étendue lexicale de la `parallel sections` construction.

```cpp
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```

## <a name="a9-single-directives"></a>A. 9 directives uniques

L’exemple suivant illustre la directive [unique](2-directives.md#243-single-construct) . Dans l’exemple, un seul thread (généralement le premier thread qui rencontre la `single` directive) imprime le message de progression. L’utilisateur ne doit pas faire d’hypothèses quant au thread qui exécutera la `single` section. Tous les autres threads ignoreront la `single` section et s’arrêteront au niveau du cloisonnement à la fin de la `single` construction. Si d’autres threads peuvent continuer sans attendre que le thread exécute la `single` section, une `nowait` clause peut être spécifiée dans la `single` directive.

```cpp
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```

## <a name="a10-sequential-ordering"></a>A. 10 ordre séquentiel

Les [sections ordonnées](2-directives.md#266-ordered-construct) sont utiles pour classer séquentiellement la sortie du travail effectué en parallèle. Le programme suivant imprime les index dans l’ordre séquentiel :

```cpp
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```

## <a name="a11-a-fixed-number-of-threads"></a>A. 11 un nombre fixe de threads

Certains programmes s’appuient sur un nombre fixe de threads prédéfinis pour s’exécuter correctement.  Étant donné que le paramètre par défaut pour l’ajustement dynamique du nombre de threads est défini par l’implémentation, ces programmes peuvent choisir de désactiver la fonctionnalité threads dynamiques et de définir le nombre de threads de manière explicite pour assurer la portabilité. L’exemple suivant montre comment effectuer cette opération à l’aide de [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function), et [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function):

```cpp
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

Dans cet exemple, le programme s’exécute correctement uniquement s’il est exécuté par 16 threads. Si l’implémentation ne peut pas prendre en charge 16 threads, le comportement de cet exemple est défini par l’implémentation.

Le nombre de threads qui exécutent une région parallèle reste constant pendant une région parallèle, quel que soit le paramètre threads dynamiques. Le mécanisme de threads dynamiques détermine le nombre de threads à utiliser au début de la région parallèle et la maintient constante pour la durée de la région.

## <a name="a12-the-atomic-directive"></a>A. 12 la directive Atomic

L’exemple suivant évite les conditions de concurrence critique (mises à jour simultanées d’un élément *x* par de nombreux threads) à l’aide de la directive [Atomic](2-directives.md#264-atomic-construct) :

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

L’avantage de l’utilisation de la `atomic` directive dans cet exemple est qu’elle permet d’effectuer des mises à jour de deux éléments différents de x en parallèle. Si une directive [critique](2-directives.md#262-critical-construct) est utilisée à la place, toutes les mises à jour des éléments de *x* sont exécutées en série (mais pas dans un ordre garanti).

La `atomic` directive s’applique uniquement à l’instruction C ou C++ qui la suit immédiatement.  Par conséquent, les éléments de *y* ne sont pas mis à jour atomiquement dans cet exemple.

## <a name="a13-a-flush-directive-with-a-list"></a>A. 13 une directive Flush avec une liste

L’exemple suivant utilise la `flush` directive pour la synchronisation point-à-point d’objets spécifiques entre des paires de threads :

```cpp
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```

## <a name="a14-a-flush-directive-without-a-list"></a>A. 14 une directive Flush sans liste

L’exemple suivant (pour la [section 2.6.5](2-directives.md#265-flush-directive)) distingue les objets partagés affectés par une `flush` directive sans liste des objets partagés qui ne sont pas affectés :

```cpp
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```

## <a name="a15-the-number-of-threads-used"></a>A. 15 le nombre de threads utilisés

Prenons l’exemple incorrect suivant (pour la [section 3.1.2](3-run-time-library-functions.md#312-omp_get_num_threads-function)) :

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

L' `omp_get_num_threads()` appel retourne 1 dans la section série du code, de sorte que *NP* sera toujours égal à 1 dans l’exemple précédent. Pour déterminer le nombre de threads qui seront déployés pour la région parallèle, l’appel doit être à l’intérieur de la région parallèle.

L’exemple suivant montre comment réécrire ce programme sans inclure une requête pour le nombre de threads :

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>Verrous A. 16

Dans l’exemple suivant (pour la [section 3,2](3-run-time-library-functions.md#32-lock-functions)), l’argument des fonctions de verrouillage doit avoir le type `omp_lock_t` et il n’est pas nécessaire de le vider.  Les fonctions de verrouillage entraînent l’inactivité des threads lors de l’attente de l’entrée dans la première section critique, mais pour effectuer d’autres tâches en attendant une entrée pour la seconde.  La `omp_set_lock` fonction bloque, mais la `omp_test_lock` fonction ne permet pas d’effectuer le travail dans `skip()` .

```cpp
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```

## <a name="a17-nestable-locks"></a>A. 17 verrous imbriqués

L’exemple suivant (pour la [section 3,2](3-run-time-library-functions.md#32-lock-functions)) montre comment un verrou imbriqué peut être utilisé pour synchroniser les mises à jour à la fois dans une structure entière et dans l’un de ses membres.

```cpp
#include <omp.h>
typedef struct {int a,b; omp_nest_lock_t lck;} pair;

void incr_a(pair *p, int a)
{
    // Called only from incr_pair, no need to lock.
    p->a += a;
}

void incr_b(pair *p, int b)
{
    // Called both from incr_pair and elsewhere,
    // so need a nestable lock.

    omp_set_nest_lock(&p->lck);
    p->b += b;
    omp_unset_nest_lock(&p->lck);
}

void incr_pair(pair *p, int a, int b)
{
    omp_set_nest_lock(&p->lck);
    incr_a(p, a);
    incr_b(p, b);
    omp_unset_nest_lock(&p->lck);
}

void f(pair *p)
{
    extern int work1(), work2(), work3();
    #pragma omp parallel sections
    {
        #pragma omp section
            incr_pair(p, work1(), work2());
        #pragma omp section
            incr_b(p, work3());
    }
}
```

## <a name="a18-nested-for-directives"></a>A. 18 directives for imbriquées

L’exemple suivant d' `for` [imbrication](2-directives.md#29-directive-nesting) de directives est conforme, car les directives Inner et Outer sont `for` liées à différentes régions parallèles :

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

La variante suivante de l’exemple précédent est également conforme :

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A. 19 exemples illustrant l’imbrication incorrecte de directives de partage de travail

Les exemples de cette section illustrent les règles d' [imbrication de directives](2-directives.md#29-directive-nesting) .

L’exemple suivant n’est pas conforme car les directives Inner et Outer `for` sont imbriquées et sont liées à la même `parallel` directive :

```cpp
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

La version imbriquée dynamiquement suivante de l’exemple précédent est également non conforme :

```cpp
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

L’exemple suivant n’est pas conforme, car `for` les `single` directives et sont imbriquées, et elles sont liées à la même région parallèle :

```cpp
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

L’exemple suivant n’est pas conforme, car une `barrier` directive à l’intérieur d’une `for` peut entraîner un interblocage :

```cpp
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

L’exemple suivant n’est pas conforme car le `barrier` provoque un interblocage en raison du fait qu’un seul thread à la fois peut accéder à la section critique :

```cpp
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

L’exemple suivant n’est pas conforme car le `barrier` provoque un interblocage en raison du fait qu’un seul thread exécute `single` la section :

```cpp
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```

## <a name="a20-bind-barrier-directives"></a>A. 20 directives de cloisonnement de liaison

Les règles de liaison de directive appellent pour `barrier` qu’une directive soit liée à la directive englobante la plus proche `parallel` . Pour plus d’informations sur la liaison de directive, consultez la [section 2,8](2-directives.md#28-directive-binding).

Dans l’exemple suivant, l’appel de *main* à *Sub2* est conforme, car `barrier` (dans *SUB3*) est lié à la région parallèle dans *Sub2*. L’appel de *main* à *Sub1* est conforme, car le `barrier` lie à la région parallèle dans la sous-routine *Sub2*.  L’appel de *main* à *SUB3* est conforme, car le `barrier` n’est pas lié à une région parallèle et est ignoré. En outre, le `barrier` synchronise uniquement l’équipe de threads dans la région parallèle englobante, et non pas tous les threads créés dans *Sub1*.

```cpp
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```

## <a name="a21-scope-variables-with-the-private-clause"></a>A. 21 variables de portée avec la clause Private

Les valeurs de `i` et `j` dans l’exemple suivant ne sont pas définies à la sortie de la région parallèle :

```cpp
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

Pour plus d’informations sur la `private` clause, consultez la [section 2.7.2.1](2-directives.md#2721-private).

## <a name="a22-the-defaultnone-clause"></a>A. 22 la clause par défaut (None)

L’exemple suivant distingue les variables qui sont affectées par la `default(none)` clause des variables qui ne sont pas :

```cpp
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

Pour plus d’informations sur la `default` clause, consultez la [section 2.7.2.5](2-directives.md#2725-default).

## <a name="a23-examples-of-the-ordered-directive"></a>A. 23 exemples de la directive ordered

Il est possible d’avoir plusieurs sections ordonnées avec un `for` spécifié avec la `ordered` clause. Le premier exemple est non conforme, car l’API spécifie la règle suivante :

« Une itération d’une boucle avec une `for` construction ne doit pas exécuter la même `ordered` directive plus d’une fois, et elle ne doit pas exécuter plus d’une `ordered` directive. » (Voir la [section 2.6.6](2-directives.md#266-ordered-construct).)

Dans cet exemple non conforme, toutes les itérations exécutent deux sections ordonnées :

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

L’exemple conforme suivant illustre un `for` avec plusieurs sections ordonnées :

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```

## <a name="a24-example-of-the-private-clause"></a>A. 24 exemple de la clause Private

La clause [Private](2-directives.md#2721-private) d’une région parallèle est uniquement en vigueur pour l’étendue lexicale de la région, et non pour l’étendue dynamique de la région.  Par conséquent, dans l’exemple qui suit, toute utilisation de la variable *a* dans `for` la boucle de la routine *f* fait référence à une copie privée d' *un*, alors qu’une utilisation dans la routine *g* fait référence au global *a*.

```cpp
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>A. 25 exemples de la clause d’attribut de données copyprivate

**Exemple 1 :** La clause [copyprivate](2-directives.md#2728-copyprivate) peut être utilisée pour diffuser les valeurs acquises par un seul thread directement à toutes les instances des variables privées dans les autres threads.

```cpp
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

Si routine *init* est appelé à partir d’une région de série, son comportement n’est pas affecté par la présence des directives. Une fois que l’appel à la routine *get_values* a été exécuté par un thread, aucun thread ne quitte la construction jusqu’à ce que les objets privés désignés par *a*, *b*, *x* et *y* dans tous les threads aient été définis avec les valeurs lues.

**Exemple 2 :** Par opposition à l’exemple précédent, supposons que la lecture doit être effectuée par un thread particulier, par exemple le thread principal. Dans ce cas, la `copyprivate` clause ne peut pas être utilisée pour effectuer la diffusion directement, mais elle peut être utilisée pour fournir l’accès à un objet partagé temporaire.

```cpp
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**Exemple 3 :** Supposons que le nombre d’objets Lock requis dans une région parallèle ne puisse pas être facilement déterminé avant son entrée. La `copyprivate` clause peut être utilisée pour fournir l’accès aux objets Lock partagés qui sont alloués dans cette région parallèle.

```cpp
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```

## <a name="a26-the-threadprivate-directive"></a>A. 26 la directive threadprivate

Les exemples suivants montrent comment utiliser la directive [threadprivate](2-directives.md#271-threadprivate-directive) pour attribuer à chaque thread un compteur séparé.

### <a name="example-1"></a>Exemple 1

```cpp
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

### <a name="example-2"></a>Exemple 2

```cpp
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```

## <a name="a27-c99-variable-length-arrays"></a>A. 27 tableaux de longueur variable C99

L’exemple suivant montre comment utiliser des tableaux de longueur variable C99 (VLAs) dans une directive [firstprivate](2-directives.md#2722-firstprivate) .

> [!NOTE]
> Les tableaux de longueur variable ne sont actuellement pas pris en charge dans Visual C++.

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-num_threads-clause"></a>A. 28 la clause num_threads

L’exemple suivant illustre la clause [num_threads](2-directives.md#23-parallel-construct) . La région parallèle est exécutée avec un maximum de 10 threads.

```cpp
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>A. 29 constructions de partage de travail à l’intérieur d’une construction critique

L’exemple suivant illustre l’utilisation d’une construction de partage de travail à l’intérieur d’une `critical` construction. Cet exemple est conforme, car la construction de partage de travail et la `critical` construction ne sont pas liées à la même région parallèle.

```cpp
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```

## <a name="a30-reprivatization"></a>A. 30 reprivatisation

L’exemple suivant illustre la reprivatisation des variables. Les variables privées peuvent être marquées `private` à nouveau dans une directive imbriquée. Vous n’avez pas besoin de partager ces variables dans la région parallèle englobante.

```cpp
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```

## <a name="a31-thread-safe-lock-functions"></a>A. 31 fonctions de verrouillage thread-safe

L’exemple C++ suivant montre comment initialiser un tableau de verrous dans une région parallèle à l’aide de [omp_init_lock](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

```cpp
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```
