---
title: Un fichier . Exemples
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: 061490d34829175bfbdcd84d6208aa396bb19671
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087299"
---
# <a name="a-examples"></a>Un fichier . Exemples

Voici quelques exemples de constructions définies dans ce document. Une instruction qui suit une directive est composée uniquement lorsque cela est nécessaire, et une instruction non composées est décalé par rapport à une directive qui la précède.

## <a name="a1-a-simple-loop-in-parallel"></a>A.1 une simple boucle en parallèle

L’exemple suivant montre comment paralléliser une boucle à l’aide de la [parallèles pour](2-directives.md#251-parallel-for-construct) la directive. La variable d’itération de boucle est privée par défaut, donc il n’est pas nécessaire de spécifier explicitement dans une clause privée.

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>Compilation conditionnelle A.2

Les exemples suivants illustrent l’utilisation de la compilation conditionnelle à l’aide de la macro OpenMP [_OPENMP](2-directives.md#22-conditional-compilation). Avec la compilation de OpenMP, le `_OPENMP` macro est définie.

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

L’opérateur de préprocesseur défini permet plusieurs macros à tester dans une directive unique.

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>A.3 des régions parallèles

Le [parallèles](2-directives.md#23-parallel-construct) directive peut être utilisée dans les programmes parallèles de granularité grossière. Dans l’exemple suivant, chaque thread dans la région parallèle décide quelle partie du tableau global `x` travailler, en fonction du nombre de threads :

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>A.4 la clause nowait

S’il existe de nombreuses boucles indépendants dans une région parallèle, vous pouvez utiliser la [nowait](2-directives.md#241-for-construct) clause afin d’éviter la barrière implicite à la fin de la `for` directive, comme suit :

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

## <a name="a5-the-critical-directive"></a>A.5 la directive critical

L’exemple suivant inclut plusieurs [critique](2-directives.md#262-critical-construct) directives. L’exemple illustre un modèle de file d’attente dans laquelle une tâche est dépilée et a travaillé sur. Pour vous protéger contre le nombre de threads du retrait de la même tâche, l’opération de retrait doit être dans un `critical` section. Étant donné que les deux files d’attente dans cet exemple sont indépendantes, qu’elles sont protégées par `critical` directives avec des noms différents, *xaxis* et *yaxis*.

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

## <a name="a6-the-lastprivate-clause"></a>A.6 la clause lastprivate

Exécution correcte parfois dépend de la valeur de la dernière itération d’une boucle assigne à une variable. Ces programmes doivent répertorier toutes les variables de ce type en tant qu’arguments à un [lastprivate](2-directives.md#2723-lastprivate) clause afin que les valeurs des variables sont les mêmes que lorsque la boucle est exécutée de manière séquentielle.

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

Dans l’exemple précédent, la valeur de `i` à la fin de la région parallèle est égal à `n-1`, comme dans le cas séquentiel.

## <a name="a7-the-reduction-clause"></a>A.7 la clause reduction

L’exemple suivant montre le [réduction](2-directives.md#2726-reduction) clause :

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>A.8 des sections Parallel

Dans l’exemple suivant (pour [section 2.4.2](2-directives.md#242-sections-construct)), fonctions *xaxis*, *yaxis*, et *zaxis* peuvent être exécutées simultanément. Le premier `section` directive est facultative.  Tous les `section` directives doivent apparaître dans l’étendue lexicale de la `parallel sections` construire.

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

## <a name="a9-single-directives"></a>A.9 de directives simples

L’exemple suivant montre le [unique](2-directives.md#243-single-construct) directive. Dans l’exemple, un seul thread (généralement le premier thread qui rencontre le `single` directive) imprime le message de progression. L’utilisateur ne doit pas faire d’hypothèses comme pour le thread qui exécutera le `single` section. Tous les autres threads ignorera la `single` section et arrêter à la barrière à la fin de la `single` construire. Si les autres threads puissent poursuivre sans attendre que le thread s’exécutant le `single` section, un `nowait` clause peut être spécifiée sur la `single` directive.

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

## <a name="a10-sequential-ordering"></a>Ordre séquentiel A.10

[Classés sections](2-directives.md#266-ordered-construct) sont utiles pour le classement de manière séquentielle la sortie de travail qui a effectué en parallèle. Le programme suivant imprime les index dans un ordre séquentiel :

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

## <a name="a11-a-fixed-number-of-threads"></a>A.11 A fixe le nombre de threads

Certains programmes s’appuient sur un nombre fixe, spécifiée à l’avance de threads pour exécuter correctement.  Étant donné que le paramètre par défaut pour l’ajustement dynamique du nombre de threads est défini par l’implémentation, ces programmes peuvent choisir de désactiver la fonctionnalité de threads dynamiques et de définir le nombre de threads explicitement pour conserver la portabilité. L’exemple suivant montre comment effectuer cette opération à l’aide de [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function), et [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function):

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

Dans cet exemple, le programme s’exécute correctement uniquement si elle est exécutée par 16 threads. Si l’implémentation n’est pas capable de prendre en charge 16 threads, le comportement de cet exemple est défini par l’implémentation.

Le nombre de threads de l’exécution d’une région parallèle reste constante pendant une région parallèle, quel que soit les paramètre de threads dynamiques. Le mécanisme de threads dynamiques détermine le nombre de threads à utiliser au début de la région parallèle et les conserve à la constante pendant la durée de la région.

## <a name="a12-the-atomic-directive"></a>A.12 la directive atomic

L’exemple suivant permet d’éviter des conditions de concurrence (mises à jour simultanées d’un élément de *x* par nombreux threads) à l’aide de la [atomique](2-directives.md#264-atomic-construct) directive :

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

L’avantage d’utiliser le `atomic` directive dans cet exemple est qu’elle autorise les mises à jour de deux éléments différents de x être exécutées en parallèle. Si un [critique](2-directives.md#262-critical-construct) directive est utilisée à la place, puis toutes les mises à jour aux éléments de *x* sont exécutées en série (bien que non dans des garanties ordre).

Le `atomic` directive s’applique uniquement à l’instruction C ou C++, il suit immédiatement.  Par conséquent, les éléments de *y* ne sont pas mis à jour atomiquement dans cet exemple.

## <a name="a13-a-flush-directive-with-a-list"></a>A.13 A la directive flush avec une liste

L’exemple suivant utilise la `flush` directive pour la synchronisation de point à point des objets spécifiques entre les paires de threads :

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

## <a name="a14-a-flush-directive-without-a-list"></a>A.14 A la directive flush sans liste

L’exemple suivant (pour [section 2.6.5](2-directives.md#265-flush-directive)) permet de distinguer les objets partagés affectés par un `flush` directive avec aucune liste à partir des objets partagés qui ne sont pas affectés :

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

## <a name="a15-the-number-of-threads-used"></a>A.15 le nombre de threads utilisés

Prenons l’exemple suivant incorrecte (pour [section 3.1.2](3-run-time-library-functions.md#312-omp_get_num_threads-function)) :

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

Le `omp_get_num_threads()` appeler retourne 1 dans la section de série du code, par conséquent, *np* sera toujours égal à 1 dans l’exemple précédent. Pour déterminer le nombre de threads qui seront déployées pour la région parallèle, l’appel doit être à l’intérieur de la région parallèle.

L’exemple suivant montre comment réécrire ce programme sans inclure une requête pour le nombre de threads :

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>A.16 verrous

Dans l’exemple suivant (pour [section 3.2](3-run-time-library-functions.md#32-lock-functions)), l’argument pour les fonctions de verrouillage doit avoir le type `omp_lock_t`, et qu’il n’est pas nécessaire de le videz.  Les fonctions de verrouillage entraînent les threads pour être inactif en attendant d’entrée à la première section critique, mais pour effectuer d’autres tâches en attendant d’entrée à la seconde.  Le `omp_set_lock` blocs de fonction, mais la `omp_test_lock` fonction ne, ce qui permet le travail en `skip()` à faire.

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

## <a name="a17-nestable-locks"></a>Verrous pouvant être imbriqués A.17

L’exemple suivant (pour [section 3.2](3-run-time-library-functions.md#32-lock-functions)) montre comment un verrou pouvant être peut être utilisé pour synchroniser les mises à jour à la fois à un ensemble de la structure et de ses membres.

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

## <a name="a18-nested-for-directives"></a>Nested A.18 directives for

L’exemple suivant de `for` [imbrication de directives](2-directives.md#29-directive-nesting) est conforme, car intérieurs et extérieurs `for` directives lier à différentes régions parallèles :

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

Une variante suivante de l’exemple précédent est également conforme :

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

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 exemples illustrant l’imbrication incorrecte de partage de travail directives

Les exemples de cette section illustrent la [imbrication de directives](2-directives.md#29-directive-nesting) règles.

L’exemple suivant n’est pas conforme, car les intérieurs et extérieurs `for` directives sont imbriqués et les lier au même `parallel` directive :

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

La version dynamiquement imbriquée suivante de l’exemple précédent est également non conforme :

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

L’exemple suivant n’est pas conforme, car le `for` et `single` directives sont imbriqués, et ils sont liés à la même région parallèle :

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

L’exemple suivant n’est pas conforme, car un `barrier` directive à l’intérieur d’un `for` peut entraîner un blocage :

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

L’exemple suivant n’est pas conforme, car le `barrier` entraîne un blocage dû au fait que qu’un seul thread à la fois peut entrer dans la section critique :

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

L’exemple suivant n’est pas conforme, car le `barrier` entraîne un blocage dû au fait que seul un thread exécute le `single` section :

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

## <a name="a20-bind-barrier-directives"></a>Directives A.20 liaison barrier

La liaison de directives règles d’appel pour un `barrier` directive à lier à la forme plus proche `parallel` directive. Pour plus d’informations sur la liaison de directives, consultez [section 2.8](2-directives.md#28-directive-binding).

Dans l’exemple suivant, l’appel de *principal* à *sub2* est conforme, car le `barrier` (dans *sub3*) est lié à la région parallèle dans *sub2* . L’appel de *principal* à *sub1* est conforme, car le `barrier` lie à la région parallèle de la sous-routine *sub2*.  L’appel de *principal* à *sub3* est conforme, car le `barrier` ne lier à n’importe quelle région parallèle et est ignoré. En outre, le `barrier` synchronise uniquement l’équipe de threads dans la région parallèle englobante et pas tous les threads créés dans *sub1*.

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

## <a name="a21-scope-variables-with-the-private-clause"></a>A.21 des variables de portée avec la clause private

Les valeurs de `i` et `j` dans l’exemple suivant ne sont pas définies à la sortie à partir de la région parallèle :

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

Pour plus d’informations sur la `private` clause, consultez [section 2.7.2.1](2-directives.md#2721-private).

## <a name="a22-the-defaultnone-clause"></a>A.22 la clause default (None)

L’exemple suivant permet de distinguer les variables qui sont affectés par la `default(none)` clause à partir de variables qui ne sont pas :

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

Pour plus d’informations sur la `default` clause, consultez [section 2.7.2.5](2-directives.md#2725-default).

## <a name="a23-examples-of-the-ordered-directive"></a>A.23 exemples de directive ordered

Il est possible d’avoir de nombreuses sections ordonnées avec un `for` spécifié avec le `ordered` clause. Le premier exemple n’est pas conforme, car l’API spécifie la règle suivante :

« Une itération d’une boucle avec une `for` construction ne doit pas exécuter le même `ordered` directive plus qu’une seule fois et il ne doivent pas exécuter plusieurs `ordered` directive. » (Consultez [section 2.6.6](2-directives.md#266-ordered-construct).)

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

L’exemple conforme suivant un `for` avec plus d’une section classée :

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

## <a name="a24-example-of-the-private-clause"></a>A.24 exemple de la clause private

Le [privé](2-directives.md#2721-private) clause d’une région parallèle n’est en vigueur pour l’étendue lexicale de la région, mais pas pour l’étendue dynamique de la région.  Par conséquent, dans l’exemple qui suit, toutes les utilisations de la variable *un* au sein de la `for` boucle dans la routine *f* fait référence à une copie privée de *un*, tandis que d’une utilisation dans routine *g* fait référence au modèle global *un*.

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

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>A.25 exemples de la clause d’attribut de données copyprivate

**Exemple 1 :** Le [copyprivate](2-directives.md#2728-copyprivate) clause peut être utilisée pour diffuser des valeurs acquis par un seul thread directement à toutes les instances des variables privées dans les autres threads.

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

Si la routine *init* est appelée à partir d’une région de série, son comportement n’est pas affecté par la présence des directives. Après l’appel à la *get_values* routine a été exécutée par un thread, aucun thread ne quitte la construction jusqu'à ce que les objets privés désignés par *un*, *b*, *x*, et *y* dans tous les threads ont deviennent définis avec les valeurs lues.

**Exemple 2 :** Contrairement à l’exemple précédent, supposons que la lecture doit être effectuée par un thread particulier, par exemple le thread principal. Dans ce cas, le `copyprivate` clause ne peut pas être utilisée pour effectuer la diffusion directement, mais il peut être utilisé pour fournir l’accès à un objet partagé temporaire.

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

**Exemple 3 :** Supposons que le nombre d’objets de verrou requis dans une région parallèle ne peut pas être déterminé facilement avant de l’indiquer. Le `copyprivate` clause peut être utilisée pour fournir l’accès aux objets de verrou partagé sont alloués dans cette région parallèle.

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

## <a name="a26-the-threadprivate-directive"></a>A.26 la directive threadprivate

Les exemples suivants montrent comment utiliser le [threadprivate](2-directives.md#271-threadprivate-directive) directive pour donner un compteur distinct à chaque thread.

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

## <a name="a27-c99-variable-length-arrays"></a>Tableaux de longueur variable C99 A.27

L’exemple suivant montre comment utiliser des tableaux de longueur Variable C99 (en) dans un [firstprivate](2-directives.md#2722-firstprivate) directive.

> [!NOTE]
> Tableaux de longueur variable ne sont pas actuellement pris en charge dans Visual C++.

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-numthreads-clause"></a>A.28 la clause num_threads

L’exemple suivant montre le [num_threads](2-directives.md#23-parallel-construct) clause. La région parallèle est exécutée avec un maximum de 10 threads.

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

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>A.29 les constructions de partage de travail à l’intérieur d’une construction critical

L’exemple suivant montre à l’aide d’une construction de partage de travail à l’intérieur d’un `critical` construire. Cet exemple est conforme, car le partage de travail construire et `critical` construction ne liez pas à la même région parallèle.

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

## <a name="a30-reprivatization"></a>Reprivatisation A.30

L’exemple suivant montre la reprivatisation des variables. Variables privées peuvent être marqués `private` dans une directive imbriquée. Vous n’avez pas besoin de partager ces variables dans la région parallèle englobante.

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

## <a name="a31-thread-safe-lock-functions"></a>A.31 fonctions de verrouillage Thread-safe

L’exemple C++ suivant montre comment initialiser un tableau de verrous dans une région parallèle à l’aide de [fonctions omp_init_lock](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

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
