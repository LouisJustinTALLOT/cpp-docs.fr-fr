---
title: 2. Directives
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087338"
---
# <a name="2-directives"></a>2. Directives

Directives sont basées sur `#pragma` directives définis dans les normes C et C++.  Les compilateurs qui prennent en charge les API C++ OpenMP C inclut une option de ligne de commande qui active et permet l’interprétation de toutes les directives de compilateur OpenMP.

## <a name="21-directive-format"></a>2.1 format des directives

La syntaxe d’une directive OpenMP est formellement spécifiée par la grammaire dans [annexe C](c-openmp-c-and-cpp-grammar.md)et de manière informelle comme suit :

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Chaque directive commence par `#pragma omp`afin de réduire le risque potentiel de conflit avec d’autres directives de pragma (non OpenMP ou fournisseur extensions OpenMP) portant le même nom. Le reste de la directive suit les conventions des normes pour les directives de compilateur C et C++. En particulier, un espace blanc peut être utilisé avant et après le `#`, et parfois un espace blanc doit être utilisé pour séparer les mots dans une directive. Prétraitement des jetons après la `#pragma omp` subissent un remplacement de macro.

Directives respectent la casse. L’ordre des clauses dans les directives ne sont pas significative. Clauses sur les directives peuvent être répétées en fonction des besoins, soumis aux restrictions répertoriées dans la description de chaque clause. Si *variable-list* s’affiche dans une clause, il doit spécifier uniquement les variables. Seul *nom de la directive* peut être spécifiée par la directive.  Par exemple, la directive suivante n’est pas autorisée :

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Une directive OpenMP s’applique au plus une réussie instruction, qui doit être un bloc structuré.

## <a name="22-conditional-compilation"></a>2.2 compilation conditionnelle

Le `_OPENMP` nom de la macro est définie par les implémentations conformes OpenMP en tant que constante décimale *yyyymm*, qui sera l’année et le mois de la spécification approuvée. Cette macro ne doit pas faire l’objet d’un `#define` ou un `#undef` directive de prétraitement.

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Si les fournisseurs définissent les extensions de OpenMP, ils peuvent spécifier supplémentaires macros prédéfinies.

## <a name="23-parallel-construct"></a>2.3 construction parallèle

La directive suivante définit une région parallèle, ce qui est une région du programme qui doit être exécuté par un grand nombre de threads en parallèle. Cette directive est la construction fondamentale qui démarre l’exécution en parallèle.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

Le *clause* est une des opérations suivantes :

- `if(` *scalar-expression* `)`
- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `default(shared | none)`
- `shared(` *variable-list* `)`
- `copyin(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `num_threads(` *integer-expression* `)`

Lorsqu’un thread atteint une construction parallèle, une équipe de threads est créée si un des cas suivants est vrai :

- Ne `if` clause est spécifiée.
- Le `if` expression correspond à une valeur différente de zéro.

Ce thread devient le thread principal de l’équipe, avec un nombre de threads de 0, et tous les threads dans l’équipe, notamment le thread principal, exécutent la région en parallèle. Si la valeur de la `if` expression est égale à zéro, la région est sérialisée.

Pour déterminer le nombre de threads qui sont demandées, les règles suivantes seront considérés dans l’ordre. La première règle dont la condition est remplie sera appliquée :

1. Si le `num_threads` clause est spécifiée, la valeur de l’expression entière est le nombre de threads demandé.

1. Si le `omp_set_num_threads` fonction de bibliothèque a été appelée, la valeur de l’argument dans l’appel exécuté le plus récemment est le nombre de threads demandé.

1. Si la variable d’environnement `OMP_NUM_THREADS` est définie, la valeur de cette variable d’environnement est le nombre de threads demandé.

1. Si aucune des méthodes ci-dessus est utilisé, le nombre de threads demandé est défini par l’implémentation.

Si le `num_threads` clause est spécifiée, puis elle remplace le nombre de threads demandé par le `omp_set_num_threads` fonction de bibliothèque ou le `OMP_NUM_THREADS` variable d’environnement uniquement pour la région parallèle, il est appliqué à. Plus tard des régions parallèles ne sont pas affectées par ce dernier.

Le nombre de threads qui s’exécutent de la région parallèle dépend également si l’ajustement dynamique du nombre de threads est activé. Si l’ajustement dynamique est désactivée, le nombre demandé de threads exécutera la région parallèle. Si l’ajustement dynamique est activé le nombre demandé de threads est le nombre maximal de threads pouvant être exécutées à la région parallèle.

Si une région parallèle est rencontrée pendant que l’ajustement dynamique du nombre de threads est désactivé, et le nombre de threads demandé pour la région parallèle est supérieur au nombre que le système d’exécution peut fournir, le comportement du programme est défini par l’implémentation. Une implémentation susceptibles, par exemple, d’interrompre l’exécution du programme, ou il peut sérialiser la région parallèle.

Le `omp_set_dynamic` fonction de bibliothèque et le `OMP_DYNAMIC` variable d’environnement peut être utilisée pour activer et désactiver l’ajustement dynamique du nombre de threads.

Le nombre de processeurs physiques hébergeant les threads à un moment donné est défini par l’implémentation. Une fois créé, le nombre de threads dans l’équipe reste constante pendant la durée de cette région parallèle. Il peut être modifié explicitement par l’utilisateur ou automatiquement par le système d’exécution d’une région parallèle à l’autre.

Les instructions contenues dans l’étendue dynamique de la région parallèle sont exécutées par chaque thread, et chaque thread peut exécuter un chemin d’accès d’instructions est différent des autres threads. Directives rencontrés en dehors de l’étendue lexicale d’une région parallèle sont appelés des directives orphelins.

Il existe une barrière implicite à la fin d’une région parallèle. Seul le thread principal de l’équipe continue l’exécution à la fin d’une région parallèle.

Si un thread dans une équipe de l’exécution d’une région parallèle rencontre une autre construction parallèle, il crée une nouvelle équipe, et il devient le maître de cette nouvelle équipe. Les régions parallèles imbriquées sont sérialisées par défaut. Par conséquent, par défaut, une région parallèle imbriquée est exécutée par une équipe composée d’un seul thread. Le comportement par défaut peut être modifié à l’aide de la fonction de bibliothèque runtime `omp_set_nested` ou la variable d’environnement `OMP_NESTED`. Toutefois, le nombre de threads dans une équipe qui s’exécutent une région parallèle imbriquée est défini par l’implémentation.

Restrictions à le `parallel` directive sont les suivantes :

- Au maximum, un `if` clause peut apparaître sur la directive.

- Il a n’est pas spécifié si les effets à l’intérieur d’if expression ou `num_threads` expression se produisent.

- Un `throw` exécutée à l’intérieur d’une région parallèle doit provoquer l’exécution de reprise dans l’étendue dynamique de la même bloc structuré, et elle doit être interceptée par le même thread qui a levé l’exception.

- Un seul `num_threads` clause peut apparaître sur la directive. Le `num_threads` expression est évaluée en dehors du contexte de la région parallèle et doit correspondre à une valeur entière positive.

- L’ordre d’évaluation de la `if` et `num_threads` clauses n’est pas spécifié.

### <a name="cross-references"></a>Références croisées

- `private`, `firstprivate`, `default`, `shared`, `copyin`, et `reduction` clauses ([section 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable d’environnement
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) fonction de bibliothèque
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) variable d’environnement
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) (fonction)
- [OMP_NESTED](4-environment-variables.md#44-omp_nested) variable d’environnement
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) fonction de bibliothèque

## <a name="24-work-sharing-constructs"></a>2.4 constructions de partage de travail

Une construction de partage de travail répartit l’exécution de l’instruction associée parmi les membres de l’équipe qui la rencontrer. Les directives de partage de travail ne pas lancer de nouveaux threads, et il n’existe plus aucune barrière implicite sur ENTRÉE pour une construction de partage de travail.

La séquence de partage de travail construit et `barrier` directives rencontrés doivent être le même pour chaque thread dans une équipe.

OpenMP définit les constructions de partage de travail suivantes, et ces constructions sont décrits dans les sections qui suivent :

- [pour](#241-for-construct) (directive)
- [sections](#242-sections-construct) (directive)
- [seul](#243-single-construct) (directive)

### <a name="241-for-construct"></a>2.4.1 construction for

Le `for` directive identifie une construction de partage de travail itérative qui spécifie que les itérations de la boucle associée seront exécutées en parallèle. Les itérations de la `for` boucle sont réparties entre les threads qui existent déjà dans l’équipe de l’exécution de la construction parallèle auquel elle est liée. La syntaxe de la `for` construction se présente comme suit :

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

La clause est une des opérations suivantes :

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:` *variable-list* `)`
- `ordered`
- `schedule(` *kind* [`,` *chunk_size*] `)`
- `nowait`

Le `for` directive impose des restrictions sur la structure correspondante `for` boucle. Plus précisément, correspondants `for` boucle doit avoir la forme canonique :

`for (` *Init-expr* `;` *var logique op b* `;` *incr-expr* `)`

*init-expr*<br/>
Une des valeurs suivantes :

- *var* = *lb*
- *type entier var* = *lb*

*incr-expr*<br/>
Une des valeurs suivantes :

- `++` *var*
- *var* `++`
- `--` *var*
- *var* `--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
Une variable d’entier signé. Si cette variable serait partagée dans le cas contraire, il est implicitement rendu privé pour la durée de la `for`. Ne modifiez pas cette variable dans le corps de la `for` instruction. Sauf si la variable est spécifiée `lastprivate`, sa valeur après la boucle est indéterminée.

*logical-op*<br/>
Une des valeurs suivantes :

- `<`
- `<=`
- `>`
- `>=`

*lb*, *b*, et *incr*<br>
Expressions d’entier invariant une boucle. Il n’existe aucune synchronisation pendant l’évaluation de ces expressions, afin que tous les effets évaluées produire des résultats indéterminés.

La forme canonique permet le nombre d’itérations de boucle à calculer sur ENTRÉE pour la boucle. Ce calcul est effectué avec des valeurs dans le type de *var*, après les promotions intégrales. En particulier, si la valeur de *b* `-` *lb* `+` *incr* ne peut pas être représentée dans la mesure où le type, le résultat est indéterminé. Plus, si *logique op* est `<` ou `<=`, puis *incr-expr* doit entraîner la production *var* à augmenter à chaque itération de la boucle.   Si *logique op* est `>` ou `>=`, puis *incr-expr* doit entraîner la production *var* pour obtenir plus petits sur chaque itération de la boucle.

Le `schedule` clause spécifie comment les itérations de la `for` boucle sont réparties entre les threads de l’équipe. L’exactitude d’un programme ne doit pas dépendre de thread qui exécute une itération particulière. La valeur de *chunk_size*, si spécifiée, doit être une expression d’entier invariant boucle avec une valeur positive. Il n’existe aucune synchronisation lors de l’évaluation de cette expression, afin que tous les effets évaluées produire des résultats indéterminés. La planification *type* peut prendre l’une des valeurs suivantes :

Tableau 2-1 : `schedule` clause *type* valeurs

|||
|-|-|
|statique|Lorsque `schedule(static,` *chunk_size* `)` est spécifié, les itérations sont divisées en segments d’une taille spécifiée par *chunk_size*. Les segments sont affectées de manière statique les threads dans l’équipe de manière tourniquet (round-robin) dans l’ordre le numéro de thread. En cas de non *chunk_size* est spécifié, l’espace d’itération est divisé en blocs qui sont approximativement égales en taille, avec un segment unique attribué à chaque thread.|
|dynamic|Lorsque `schedule(dynamic,` *chunk_size* `)` est spécifié, les itérations sont divisées en une série de blocs, chacun contenant *chunk_size* itérations. Chaque segment est affecté à un thread est en attente d’une affectation. Le thread s’exécute le bloc d’itérations et puis attend son affectation suivante, jusqu'à ce qu’aucun bloc ne reste à affecter. Le dernier segment doit être assignée peut avoir un plus petit nombre d’itérations. En cas de non *chunk_size* est spécifié, la valeur par défaut est 1.|
|guidée|Lorsque `schedule(guided,` *chunk_size* `)` est spécifié, les itérations sont associées aux threads en blocs avec la réduction des tailles. Lorsqu’un thread termine son segment attribué d’itérations, il a attribué dynamiquement un autre segment, jusqu'à ce qu’aucun reste. Pour un *chunk_size* 1, la taille de chaque segment est approximativement le nombre d’itérations non attribués divisé par le nombre de threads. Ces tailles diminuent presque exponentielle à 1. Pour un *chunk_size* avec la valeur *k* supérieure à 1, les tailles de diminuer presque exponentielle à *k*, sauf que le dernier segment peut avoir moins de *k* itérations. En cas de non *chunk_size* est spécifié, la valeur par défaut est 1.|
|runtime|Lorsque `schedule(runtime)` est spécifié, la décision en matière de planification est différée jusqu'à l’exécution. La planification *type* et taille des segments peut être choisi au moment de l’exécution en définissant la variable d’environnement `OMP_SCHEDULE`. Si cette variable d’environnement n’est pas définie, la planification qui en résulte est défini par l’implémentation. Lorsque `schedule(runtime)` est spécifié, *chunk_size* ne doit pas être spécifié.|

En l’absence de défini explicitement `schedule` clause, la valeur par défaut `schedule` est défini par l’implémentation.

Un programme OpenMP conformes ne doivent pas s’appuient sur une planification particulière pour l’exécution correcte. Un programme ne doit pas s’appuient sur une planification *type* correspondant précisément à la description ci-dessus, car il est possible d’avoir des variations dans les implémentations de la même planification *type* sur différents compilateurs. Les descriptions peuvent être utilisées pour sélectionner la planification qui convient à une situation particulière.

Le `ordered` clause doit être présent lorsque `ordered` directives lier à la `for` construire.

Il existe une barrière implicite à la fin d’un `for` construire, sauf si un `nowait` clause est spécifiée.

Restrictions à le `for` directive sont les suivantes :

- Le `for` boucle doit être un bloc structuré et, en outre, son exécution ne doit pas se terminer par un `break` instruction.

- Les valeurs de la boucle contrôlent les expressions de la `for` boucle associé à un `for` directive doit être le même pour tous les threads dans l’équipe.

- Le `for` variable d’itération de boucle doit avoir un type entier signé.

- Un seul `schedule` clause peut apparaître sur un `for` directive.

- Un seul `ordered` clause peut apparaître sur un `for` directive.

- Un seul `nowait` clause peut apparaître sur un `for` directive.

- Il s’agit if non spécifiée ou la fréquence à laquelle des effets dans n’importe quel côté le *chunk_size*, *lb*, *b*, ou *incr* expressions se produisent.

- La valeur de la *chunk_size* expression doit être identiques pour tous les threads dans l’équipe.

#### <a name="cross-references"></a>Références croisées

- `private`, `firstprivate`, `lastprivate`, et `reduction` clauses ([section 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) variable d’environnement
- [classés](#266-ordered-construct) construire
- [planification](d-using-the-schedule-clause.md) clause

### <a name="242-sections-construct"></a>2.4.2 les sections construction

Le `sections` directive identifie une construction de partage de travail noniterative qui spécifie un ensemble de constructions qui doivent être divisée entre les threads dans une équipe. Chaque section est exécutée une fois par un thread dans l’équipe. La syntaxe de la `sections` directive se présente comme suit :

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

La clause est une des opérations suivantes :

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `nowait`

Chaque section est précédée par un `section` directive, bien que le `section` directive est facultative pour la première section. Le `section` directives doivent apparaître dans l’étendue lexicale de la `sections` directive. Il existe une barrière implicite à la fin d’un `sections` construire, sauf si un `nowait` est spécifié.

Restrictions à le `sections` directive sont les suivantes :

- Un `section` directive ne doit pas apparaître en dehors de l’étendue lexicale de la `sections` directive.

- Un seul `nowait` clause peut apparaître sur un `sections` directive.

#### <a name="cross-references"></a>Références croisées

- `private`, `firstprivate`, `lastprivate`, et `reduction` clauses ([section 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 construction single

Le `single` directive identifie une construction qui spécifie que le bloc structuré associé est exécuté par un seul thread dans l’équipe (pas nécessairement le thread principal). La syntaxe de la `single` directive se présente comme suit :

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

La clause est une des opérations suivantes :

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `copyprivate(` *variable-list* `)`
- `nowait`

Il existe une barrière implicite après le `single` construire, sauf si un `nowait` clause est spécifiée.

Restrictions à le `single` directive sont les suivantes :

- Un seul `nowait` clause peut apparaître sur un `single` directive.
- Le `copyprivate` clause ne doit pas être utilisée avec le `nowait` clause.

#### <a name="cross-references"></a>Références croisées

- `private`, `firstprivate`, et `copyprivate` clauses ([section 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 combiné constructions de partage de travail parallèle

Constructions de partage de travail parallèles combinées sont des raccourcis permettant de spécifier une région parallèle qui a uniquement une construction de partage de travail. La sémantique de ces directives est les mêmes que si vous définissiez explicitement un `parallel` directive suivie d’une construction de partage de travail unique.

Les sections suivantes décrivent les constructions de partage de travail parallèles combinées :

- [parallèle pour](#251-parallel-for-construct) (directive)
- [sections parallèles](#252-parallel-sections-construct) (directive)

### <a name="251-parallel-for-construct"></a>2.5.1 construction parallel for

Le `parallel for` directive est un raccourci pour un `parallel` région qui contient une seule `for` directive. La syntaxe de la `parallel for` directive se présente comme suit :

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Cette directive permet toutes les clauses de la `parallel` directive et le `for` directive, sauf le `nowait` clause, avec une signification identique et des restrictions. La sémantique est identique à spécifier explicitement un `parallel` directive immédiatement suivie d’un `for` directive.

#### <a name="cross-references"></a>Références croisées

- [parallèle](#23-parallel-construct) (directive)
- [pour](#241-for-construct) (directive)
- [Clauses d’attributs de données](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 des sections parallel construction

Le `parallel sections` directive fournit un formulaire contextuel pour spécifier un `parallel` région qui a une seule `sections` directive. La sémantique est identique à spécifier explicitement un `parallel` directive immédiatement suivie d’un `sections` directive. La syntaxe de la `parallel sections` directive se présente comme suit :

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

Le *clause* peut prendre l’une des clauses du acceptées par le `parallel` et `sections` directives, sauf le `nowait` clause.

#### <a name="cross-references"></a>Références croisées

- [parallèle](#23-parallel-construct) (directive)
- [sections](#242-sections-construct) (directive)

## <a name="26-master-and-synchronization-directives"></a>2.6 directives Master et synchronisation

Les sections suivantes décrivent :

- [maître](#261-master-construct) construire
- [critique](#262-critical-construct) construire
- [cloisonnement](#263-barrier-directive) (directive)
- [atomique](#264-atomic-construct) construire
- [vider](#265-flush-directive) (directive)
- [classés](#266-ordered-construct) construire

### <a name="261-master-construct"></a>2.6.1 construction master

Le `master` directive identifie une construction qui spécifie un bloc structuré qui est exécuté par le thread principal de l’équipe. La syntaxe de la `master` directive se présente comme suit :

```cpp
#pragma omp master new-linestructured-block
```

Autres threads de l’équipe ne s’exécutent pas le bloc structuré associé. Il n’existe plus aucune barrière implicite sur entrée ou sortie à partir de la construction master.

### <a name="262-critical-construct"></a>2.6.2 construction critical

Le `critical` directive identifie une construction qui limite l’exécution du bloc structuré associé à un seul thread à la fois. La syntaxe de la `critical` directive se présente comme suit :

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

Facultatif *nom* peut être utilisé pour identifier la zone critique. Identificateurs utilisés pour identifier une zone critique ont une liaison externe et se trouvent dans un espace de noms qui se distingue les espaces de noms utilisés par les étiquettes, les balises, les membres et les identificateurs ordinaires.

Un thread attend au début d’une zone critique aucun autre thread n’exécute une zone critique (n’importe où dans le programme) portant le même nom. Tous les sans nom `critical` directives mappent le même nom pas spécifié.

### <a name="263-barrier-directive"></a>2.6.3 la directive barrier

Le `barrier` directive synchronise tous les threads dans une équipe. Dans ce cas, chaque thread dans l’équipe attend jusqu'à ce que toutes les autres ont atteint ce point. La syntaxe de la `barrier` directive se présente comme suit :

```cpp
#pragma omp barrier new-line
```

Une fois que tous les threads de l’équipe ont rencontré le cloisonnement, chaque thread dans l’équipe commence l’exécution des instructions après la directive de cloisonnement en parallèle. Étant donné que le `barrier` directive n’a pas une instruction de langage C dans le cadre de sa syntaxe, il existe certaines restrictions sur son positionnement dans un programme. Pour plus d’informations sur la grammaire formelle, consultez [annexe C](c-openmp-c-and-cpp-grammar.md). L’exemple ci-dessous illustre ces restrictions.

```cpp
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```

### <a name="264-atomic-construct"></a>2.6.4 construction atomic

Le `atomic` directive garantit qu’un emplacement de mémoire spécifique est mis à jour atomiquement, au lieu d’exposer à la possibilité de multiples, simultanées d’écriture de threads. La syntaxe de la `atomic` directive se présente comme suit :

```cpp
#pragma omp atomic new-lineexpression-stmt
```

L’instruction d’expression doit avoir la valeur de l’une des formes suivantes :

- *x binop* `=` *expr*
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

Dans les expressions précédentes :

- *x* est une expression lvalue avec type scalaire.

- *Expr* est une expression avec un type scalaire, et il ne référence pas l’objet désigné par *x*.

- *binop* n’est pas un opérateur surchargé et fait partie de `+`, `*`, `-`, `/`, `&`, `^`, `|`, `<<`, ou `>>`.

Bien qu’il soit défini par l’implémentation si une implémentation remplace tous les `atomic` directives avec `critical` directives qui ont le même unique *nom*, la `atomic` directive autorise une meilleure optimisation . Souvent les instructions de matériel sont disponibles pouvant effectuer la mise à jour atomique avec le moins de surcharge.

Uniquement la charge et le magasin de l’objet désigné par *x* sont atomique ; la version d’évaluation de *expr* n’est pas atomique. Pour éviter des conditions de concurrence, toutes les mises à jour de l’emplacement en parallèle doivent être protégés avec le `atomic` directive, sauf ceux qui sont connus comme étant libre des conditions de concurrence.

Restrictions à le `atomic` directive sont les suivantes :

- Toutes les références atomiques à l’emplacement de stockage x tout au long du programme doivent avoir un type compatible.

#### <a name="examples"></a>Exemples

```cpp
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```

### <a name="265-flush-directive"></a>2.6.5 directive flush

La `flush` directive, explicite ou implicite, spécifie un point de séquence de « inter-threads » au niveau duquel l’implémentation est requise pour garantir que tous les threads dans une équipe ont une vue cohérente de certains objets (spécifiées ci-dessous) en mémoire. Cela signifie que les précédentes versions d’évaluation des expressions qui font référence à ces objets sont terminées et les évaluations suivantes n’ont pas encore commencé. Par exemple, compilateurs doivent restaurer les valeurs des objets à partir des registres vers la mémoire et matériel a peut-être besoin vider les mémoires tampons d’écriture vers la mémoire et recharger les valeurs des objets de la mémoire.

La syntaxe de la `flush` directive se présente comme suit :

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Si les objets qui nécessitent une synchronisation peuvent désignées par des variables, ces variables peuvent être spécifiées dans le paramètre facultatif *variable-list*. Si un pointeur est présent dans le *variable-list*, le pointeur lui-même est vidé, pas l’objet le pointeur fait référence à.

Un `flush` directive sans un *variable-list* synchronise les objets partagés à l’exception des objets inaccessibles avec une durée de stockage automatique. (Cela est susceptible d’avoir plus de frais qu’un `flush` avec un *variable-list*.) Un `flush` directive sans un *variable-list* est implicite pour les directives suivantes :

- `barrier`
- À l’entrée et la sortie à partir de `critical`
- À l’entrée et la sortie à partir de `ordered`
- À l’entrée et la sortie à partir de `parallel`
- À la sortie à partir de `for`
- À la sortie à partir de `sections`
- À la sortie à partir de `single`
- À l’entrée et la sortie à partir de `parallel for`
- À l’entrée et la sortie à partir de `parallel sections`

La directive n’est pas impliquée si un `nowait` clause est spécifiée. Il convient de noter que le `flush` directive n’est pas impliquée pour les éléments suivants :

- Lors de l’entrée à `for`
- Entrée ou sortie à partir de `master`
- Lors de l’entrée à `sections`
- Lors de l’entrée à `single`

Une référence qui accède à la valeur d’un objet avec un type qualifié volatile se comporte comme s’il existait un `flush` directive en spécifiant le point de séquence précédent de cet objet. Une référence qui modifie la valeur d’un objet avec un type qualifié volatile se comporte comme s’il existait un `flush` directive en spécifiant le point de séquence suivante de cet objet.

Étant donné que le `flush` directive n’a pas une instruction de langage C dans le cadre de sa syntaxe, il existe certaines restrictions sur son positionnement dans un programme. Pour plus d’informations sur la grammaire formelle, consultez [annexe C](c-openmp-c-and-cpp-grammar.md). L’exemple ci-dessous illustre ces restrictions.

```cpp
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

Restrictions à le `flush` directive sont les suivantes :

- Une variable spécifiée dans un `flush` directive ne doit pas avoir un type référence.

### <a name="266-ordered-construct"></a>2.6.6 construction ordonnée

Ce qui suit le bloc structuré une `ordered` directive est exécutée dans l’ordre dans lequel les itérations seraient exécutées dans une boucle séquentielle. La syntaxe de la `ordered` directive se présente comme suit :

```cpp
#pragma omp ordered new-linestructured-block
```

Un `ordered` directive doit se trouver dans l’étendue dynamique d’un `for` ou `parallel for` construire. Le `for` ou `parallel for` directive auquel le `ordered` lie de construction doit avoir un `ordered` clause spécifié comme décrit dans [section 2.4.1](#241-for-construct). Dans l’exécution d’un `for` ou `parallel for` construire avec un `ordered` clause, `ordered` constructions sont strictement exécutées dans l’ordre dans lequel ils sont exécutés dans une exécution séquentielle de la boucle.

Restrictions à le `ordered` directive sont les suivantes :

- Une itération d’une boucle avec une `for` construction ne doit pas exécuter plusieurs fois la même directive ordonnée et qu’il ne doit pas exécuter plusieurs `ordered` directive.

## <a name="27-data-environment"></a>2.7 environnement des données

Cette section présente une directive et plusieurs clauses pour contrôler l’environnement de données pendant l’exécution des régions parallèles, comme suit :

- Un [threadprivate](#271-threadprivate-directive) directive est fournie pour portée de fichier, portée de l’espace de noms ou les variables statiques de portée de bloc local à un thread.

- Les clauses qui peuvent être spécifiées sur les directives pour contrôler les attributs de partage de variables pour la durée des constructions parallèles ou partage de travail sont décrits dans [section 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate (directive)

Le `threadprivate` directive rend la portée de fichier nommée, portée de l’espace de noms ou des variables statiques de portée de bloc spécifiés dans le *variable-list* privé à un thread. *liste de la variable* est une liste séparée par des virgules de variables qui n’ont pas un type incomplet. La syntaxe de la `threadprivate` directive se présente comme suit :

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Chaque copie d’un `threadprivate` variable est initialisée une seule fois, à un point non spécifié dans le programme avant la première référence à cette copie et de la manière habituelle (par exemple, comme la copie principale serait initialisée dans une exécution en série du programme). Notez que si un objet est référencé dans un initialiseur explicit d’un `threadprivate` variable et la valeur de l’objet est modifié avant la première référence à une copie de la variable, puis le comportement n’est pas spécifié.

Comme avec n’importe quelle variable privée, un thread ne doit pas référencer copie d’un autre thread d’un `threadprivate` objet. Au cours de la série régions et les régions principales du programme, les références seront à la copie du thread principal de l’objet.

Après l’exécution de la première région parallèle, les données dans le `threadprivate` persistent uniquement si la dynamique threads mécanisme a été désactivée et si le nombre de threads reste inchangé pour toutes les régions parallèles des objets est garantie.

Les restrictions à le `threadprivate` directive sont les suivantes :

- Un `threadprivate` directive pour les variables de portée de fichier ou de la portée de l’espace de noms doit apparaître en dehors de toute définition ou la déclaration et doit précéder lexicalement toutes les références aux variables dans sa liste.

- Chaque variable dans le *variable-list* d’un `threadprivate` directive à la portée de fichier ou un espace de noms doit faire référence à une déclaration de variable à la portée de fichier ou un espace de noms qui précède lexicalement la directive.

- Un `threadprivate` directive pour les variables de portée de bloc statique doit apparaître dans la portée de la variable et non dans une étendue imbriquée. La directive doit précéder lexicalement toutes les références aux variables dans sa liste.

- Chaque variable dans le *variable-list* d’un `threadprivate` directive dans la portée de bloc doit faire référence à une déclaration de variable dans la même portée lexicale précédant la directive. La déclaration de variable doit utiliser le spécificateur de classe de stockage statique.

- Si une variable est spécifiée dans un `threadprivate` directive dans une unité de traduction, il doit être spécifié dans un `threadprivate` directive dans chaque unité de traduction dans laquelle elle est déclarée.

- Un `threadprivate` variable ne doit pas apparaître dans une clause à l’exception de la `copyin`, `copyprivate`, `schedule`, `num_threads`, ou `if` clause.

- L’adresse d’un `threadprivate` variable n’est pas une constante d’adresse.

- A `threadprivate` variable ne doit pas avoir un type incomplet ou un type référence.

- A `threadprivate` variable de type de classe non POD doit avoir un constructeur de copie accessible et non équivoque si elle est déclarée avec un initialiseur explicit.

L’exemple suivant illustre comment la modification d’une variable qui s’affiche dans un initialiseur peut provoquer comportement non spécifié et également comment éviter ce problème à l’aide d’un objet auxiliaire et un constructeur de copie.

```cpp
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

#### <a name="cross-references"></a>Références croisées

- [threads dynamiques](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) variable d’environnement

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 clauses d’attributs de partage de données

Plusieurs directives acceptent les clauses qui permettent à un utilisateur contrôler les attributs de partage des variables pendant la durée de la région. Les clauses d’attributs de partage s’appliquent uniquement aux variables dans l’étendue lexicale de la directive sur laquelle la clause apparaît. Pas toutes les clauses suivantes sont autorisées sur toutes les directives. La liste des clauses qui ne sont valides sur une directive particulière sont décrits avec la directive.

Si une variable est visible lorsqu’une action parallèle ou partage de travail de construction est rencontrée, et la variable n’est pas spécifiée dans une clause d’attribut partage ou `threadprivate` directive, puis la variable est partagée. Variables statiques déclarées dans l’étendue dynamique d’une région parallèle sont partagés. Segment de mémoire alloué de la mémoire (par exemple, à l’aide de `malloc()` en C ou C++ ou le `new` opérateur en C++) est partagé. (Le pointeur à cette mémoire, toutefois, permettre être privés ou partagés.) Variables avec une durée de stockage automatique déclarée dans l’étendue dynamique d’une région parallèle sont privés.

La plupart des clauses accepte un *variable-list* argument, qui est une liste séparée par des virgules de variables qui sont visibles. Si une variable est référencée dans une clause d’attribut de partage de données a un type dérivé d’un modèle et il n’existe aucune autre référence à cette variable dans le programme, le comportement est indéfini.

Toutes les variables qui apparaissent dans les clauses de directive doivent être visibles. Clauses peuvent être répétées en fonction des besoins, mais aucune variable ne peut-être être spécifiée dans plusieurs clauses, sauf qu’une variable peut être spécifiée à la fois dans un `firstprivate` et un `lastprivate` clause.

Les sections suivantes décrivent les clauses d’attributs de partage de données :

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [shared](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

Le `private` clause déclare les variables dans la liste de variable, être privée pour chaque thread dans une équipe. La syntaxe de la `private` clause se présente comme suit :

```cpp
private(variable-list)
```

Le comportement d’une variable spécifiée dans un `private` clause se présente comme suit. Un nouvel objet avec une durée de stockage automatique est affectée pour la construction. La taille et l’alignement du nouvel objet sont déterminés par le type de la variable. Cette allocation se produit une fois pour chaque thread dans l’équipe, et un constructeur par défaut est appelé pour un objet de classe si nécessaire. Sinon, la valeur initiale est indéterminée.  L’objet d’origine référencé par la variable a une valeur indéterminée lors de l’entrée à la construction ne doit pas être modifiée dans l’étendue dynamique de la construction et a une valeur indéterminée la sortie de la construction.

Dans l’étendue lexicale de la construction de directive, la variable fait référence le nouvel objet privé alloué par le thread.

Les restrictions à le `private` clause sont les suivantes :

- Une variable avec un type de classe qui est spécifié dans un `private` clause doit avoir un constructeur par défaut accessible et non équivoque.

- Une variable spécifiée dans un `private` clause ne doit pas avoir un `const`-type qualifié, sauf si elle a une classe de type avec un `mutable` membre.

- Une variable spécifiée dans un `private` clause ne doit pas avoir un type incomplet ou un type référence.

- Variables qui apparaissent dans le `reduction` clause d’une `parallel` directive ne peut pas être spécifiée dans un `private` clause sur une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

Le `firstprivate` clause offre un sur-ensemble de la fonctionnalité fournie par le `private` clause. La syntaxe de la `firstprivate` clause se présente comme suit :

```cpp
firstprivate(variable-list)
```

Variables spécifiées dans *variable-list* ont `private` la sémantique de clause, comme décrit dans [section 2.7.2.1](#2721-private). L’initialisation ou une construction qui se passe comme si elle a été effectuée qu’une fois par thread, avant l’exécution du thread de la construction. Pour un `firstprivate` clause sur une construction parallèle, la valeur initiale du nouvel objet privé est la valeur de l’objet d’origine existe immédiatement avant la construction parallèle pour le thread qu’il rencontre. Pour un `firstprivate` clause sur une construction de partage de travail, la valeur initiale du nouvel objet privée pour chaque thread qui exécute la construction de partage de travail est la valeur de l’objet d’origine qui existe avant le point dans le temps que le même thread que rencontre le construction de partage de travail. En outre, pour les objets C++, le nouvel objet privé pour chaque thread est copie construit à partir de l’objet d’origine.

Les restrictions à le `firstprivate` clause sont les suivantes :

- Une variable spécifiée dans un `firstprivate` clause ne doit pas avoir un type incomplet ou un type référence.

- Une variable avec un type de classe qui est spécifié comme `firstprivate` doivent avoir un constructeur de copie accessible et non équivoque.

- Les variables qui sont privés au sein d’une région parallèle ou qui apparaissent dans le `reduction` clause d’une `parallel` directive ne peut pas être spécifiée dans un `firstprivate` clause sur une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

Le `lastprivate` clause offre un sur-ensemble de la fonctionnalité fournie par le `private` clause. La syntaxe de la `lastprivate` clause se présente comme suit :

```cpp
lastprivate(variable-list)
```

Variables spécifiées dans le *variable-list* ont `private` sémantique de la clause. Quand un `lastprivate` clause apparaît sur la directive qui identifie une construction de partage de travail, la valeur de chaque `lastprivate` à partir de la manière séquentielle dernière itération de la boucle associée, ou la directive de section lexicalement dernier, la variable est assignée à la objet d’origine de la variable. Les variables qui ne sont pas affectées une valeur par la dernière itération de la `for` ou `parallel for`, ou en la lexicalement la dernière section de la `sections` ou `parallel sections` directive, ont des valeurs indéterminées après la construction. Non affectés sous-objets ont également une valeur indéterminée après la construction.

Les restrictions à le `lastprivate` clause sont les suivantes :

- Toutes les restrictions pour `private` s’appliquent.

- Une variable avec un type de classe qui est spécifié comme `lastprivate` doit avoir un opérateur d’assignation de copie accessible et non équivoque.

- Les variables qui sont privés au sein d’une région parallèle ou qui apparaissent dans le `reduction` clause d’une `parallel` directive ne peut pas être spécifiée dans un `lastprivate` clause sur une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2724-shared"></a>2.7.2.4 shared

Cette clause partage les variables qui apparaissent dans le *variable-list* parmi tous les threads dans une équipe. La même zone de stockage pour accèdent à tous les threads au sein d’une équipe `shared` variables.

La syntaxe de la `shared` clause se présente comme suit :

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

Le `default` clause permet à l’utilisateur d’affecter les attributs de partage de données de variables. La syntaxe de la `default` clause se présente comme suit :

```cpp
default(shared | none)
```

Spécification `default(shared)` équivaut à répertorier explicitement chaque variable actuellement visible dans un `shared` clause, sauf s’il est `threadprivate` ou `const`-qualifié. En l’absence d’un texte explicite `default` clause, le comportement par défaut est le même qu’if `default(shared)` ont été spécifiés.

Spécification `default(none)` requiert qu’au moins un des éléments suivants doit être remplie pour chaque référence à une variable dans l’étendue lexicale de la construction parallèle :

- La variable est explicitement répertoriée dans une clause d’attribut de partage de données d’une construction qui contient la référence.

- La variable est déclarée au sein de la construction parallèle.

- La variable est `threadprivate`.

- La variable a un `const`-type qualifié.

- La variable est la variable de contrôle de boucle pour un `for` boucle qui le suit immédiatement un `for` ou `parallel for` directive et la référence variable apparaît à l’intérieur de la boucle.

Spécification d’une variable sur une `firstprivate`, `lastprivate`, ou `reduction` clause d’une directive délimitée provoque une référence implicite à la variable dans le contexte englobant. De telles références implicites sont également soumis aux spécifications ci-dessus.

Un seul `default` clause peut être spécifiée sur un `parallel` directive.

Attributs de partage de données peut être substituée à l’aide de la valeur par défaut d’une variable le `private`, `firstprivate`, `lastprivate`, `reduction`, et `shared` clauses, comme illustré dans l’exemple suivant :

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

Cette clause effectue une réduction sur les variables scalaires qui s’affichent dans *variable-list*, avec l’opérateur *op*. La syntaxe de la `reduction` clause se présente comme suit :

`reduction(` *op* `:` *variable-list* `)`

Une réduction est généralement spécifiée pour une instruction avec l’une des formes suivantes :

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* (à l’exception de la soustraction)
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

où :

*x*<br/>
Une des variables de réduction spécifiés dans la liste.

*variable-list*<br/>
Une liste séparée par des virgules des variables de réduction scalaire.

*expr*<br/>
Une expression avec un type scalaire qui ne référence pas *x*.

*op*<br/>
Pas un opérateur surchargé, mais un des `+`, `*`, `-`, `&`, `^`, `|`, `&&`, ou `||`.

*binop*<br/>
Pas un opérateur surchargé, mais un des `+`, `*`, `-`, `&`, `^`, ou `|`.

Voici un exemple de la `reduction` clause :

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Comme indiqué dans l’exemple, un opérateur peut être masqué à l’intérieur d’un appel de fonction. L’utilisateur doit être prudent que l’opérateur spécifié dans le `reduction` clause correspond à l’opération de réduction.

Bien que l’opérande de droite de la `||` opérateur n’a pas d’effets dans cet exemple, ils sont autorisés, mais doivent être utilisées avec précaution. Dans ce contexte, un effet secondaire qui a ne peut ne pas se produisent pendant l’exécution séquentielle de la boucle peut se produire pendant l’exécution en parallèle. Cette différence peut se produire, car l’ordre d’exécution des itérations est indéterminé.

L’opérateur est utilisé pour déterminer la valeur initiale de toutes les variables privées utilisé par le compilateur pour réduire et pour déterminer l’opérateur de la finalisation. Spécification explicite de l’opérateur permet de se trouver en dehors de l’étendue lexicale de la construction de l’instruction de réduction. Un nombre quelconque de `reduction` clauses peuvent être spécifiés dans la directive, mais une variable peut apparaître dans un `reduction` clause pour cette directive.

Une copie privée de chaque variable dans *variable-list* est créé, un pour chaque thread, comme si le `private` clause avait été utilisée. La copie privée est initialisée en fonction de l’opérateur (voir le tableau suivant).

À la fin de la région pour laquelle le `reduction` clause a été spécifiée, l’objet d’origine est mis à jour pour refléter le résultat de la combinaison de sa valeur d’origine avec la valeur finale de chacun des copies privées à l’aide de l’opérateur spécifié. Les opérateurs de réduction sont associatifs tout (à l’exception de la soustraction), et le compilateur peut réassocier librement le calcul de la valeur finale. (Les résultats partiels d’une réduction de la soustraction sont ajoutés pour former la valeur finale).

La valeur de l’objet d’origine devient indéterminée lorsque le premier thread atteint la clause de conteneur et qu’il reste ainsi jusqu'à ce que le calcul de réduction est terminé.  En règle générale, le calcul se termine à la fin de la construction ; Toutefois, si le `reduction` clause est utilisée dans une construction à laquelle `nowait` est également appliqué, la valeur de l’objet d’origine reste indéterminée jusqu'à ce qu’une synchronisation de la barrière a été effectuée pour vous assurer que tous les threads ont terminé la `reduction`clause.

Le tableau suivant répertorie les opérateurs qui ne sont valides et leurs valeurs d’initialisation canonique. La valeur de l’initialisation réelle sera cohérente avec le type de données de la variable de réduction.

|Opérateur|Initialisation|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

Les restrictions à le `reduction` clause sont les suivantes :

- Le type des variables dans le `reduction` clause doit être valide pour l’opérateur de réduction, à ceci près que les types pointeur et les types référence ne sont jamais autorisées.

- Une variable qui est spécifiée dans le `reduction` clause ne doit pas être `const`-qualifié.

- Les variables qui sont privés au sein d’une région parallèle ou qui apparaissent dans le `reduction` clause d’une `parallel` directive ne peut pas être spécifiée dans un `reduction` clause sur une directive de partage de travail qui est liée à la construction parallèle.

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```

#### <a name="2727-copyin"></a>2.7.2.7 copyin

Le `copyin` clause fournit un mécanisme pour affecter la même valeur pour `threadprivate` variables pour chaque thread dans l’équipe de l’exécution de la région parallèle. Pour chaque variable spécifiée dans un `copyin` clause, la valeur de la variable dans le thread principal de l’équipe est copié, comme si, par assignation, dans les copies privées de thread au début de la région parallèle. La syntaxe de la `copyin` clause se présente comme suit :

```cpp

copyin(
variable-list
)
```

Les restrictions à le `copyin` clause sont les suivantes :

- Une variable qui est spécifiée dans le `copyin` clause doit avoir un opérateur d’assignation de copie accessible et non équivoque.

- Une variable qui est spécifiée dans le `copyin` clause doit être un `threadprivate` variable.

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

Le `copyprivate` clause fournit un mécanisme pour utiliser une variable privée pour diffuser une valeur à partir d’un membre d’une équipe aux autres membres. Il est une alternative à l’utilisation d’une variable partagée pour la valeur lors de la fourniture de ce type d’une variable partagée serait difficile (par exemple, dans une récursivité nécessitant une variable différente à chaque niveau). Le `copyprivate` clause ne peut apparaître qu’à la `single` directive.

La syntaxe de la `copyprivate` clause se présente comme suit :

```cpp

copyprivate(
variable-list
)
```

L’effet de la `copyprivate` clause sur les variables dans sa liste de variable se produit après l’exécution du bloc structuré associé à la `single` construire, et avant que des threads dans l’équipe ont quitté la barrière à la fin de la construction. Ensuite, dans tous les autres threads dans l’équipe, pour chaque variable dans le *variable-list*, cette variable devient définie (par affectation) avec la valeur correspondante variable dans le thread qui a exécuté la construction de structure bloc.

Restrictions à le `copyprivate` clause sont les suivantes :

- Une variable qui est spécifiée dans le `copyprivate` clause ne doit pas apparaître dans un `private` ou `firstprivate` clause pour le même `single` directive.

- Si un `single` directive avec un `copyprivate` clause est rencontrée dans l’étendue dynamique d’une région parallèle, toutes les variables spécifiées dans le `copyprivate` clause doit être privée dans le contexte englobant.

- Une variable qui est spécifiée dans le `copyprivate` clause doit avoir un opérateur d’assignation de copie non équivoque accessible.

## <a name="28-directive-binding"></a>2.8 liaison de directives

Liaison dynamique des directives doit respecter les règles suivantes :

- Le `for`, `sections`, `single`, `master`, et `barrier` directives lier dynamiquement englobante `parallel`, s’il en existe, quelle que soit la valeur de n’importe quel `if` clause pouvant être présent sur ce directive. Si aucune région parallèle n’est en cours d’exécution, les directives sont exécutées par une équipe composée du thread principal uniquement.

- Le `ordered` directive lie à dynamiquement englobante `for`.

- Le `atomic` directive applique un accès exclusif au niveau `atomic` directives dans tous les threads, pas seulement l’équipe actuelle.

- Le `critical` directive applique un accès exclusif au niveau `critical` directives dans tous les threads, pas seulement l’équipe actuelle.

- Une directive ne peut jamais lier dynamiquement à n’importe quelle directive en dehors de la plus proche englobante `parallel`.

## <a name="29-directive-nesting"></a>2.9 imbrication de directives

L’imbrication dynamique de directives doit respecter les règles suivantes :

- Un `parallel` directive dynamiquement à l’intérieur d’un autre `parallel` logiquement établit une nouvelle équipe, qui se compose du thread actuel uniquement, à moins qu’imbriqués de parallélisme est activée.

- `for`, `sections`, et `single` directives lier au même `parallel` ne sont pas autorisés à être imbriqués les uns des autres.

- `critical` directives portant le même nom ne sont pas autorisés à être imbriqués les uns des autres. Notez que cette restriction n’est pas suffisante pour empêcher tout interblocage.

- `for`, `sections`, et `single` directives ne sont pas autorisés dans l’étendue dynamique de `critical`, `ordered`, et `master` régions si les directives lié à la même `parallel` en tant que les régions.

- `barrier` directives ne sont pas autorisés dans l’étendue dynamique de `for`, `ordered`, `sections`, `single`, `master`, et `critical` régions si les directives lié à la même `parallel` en tant que les régions.

- `master` directives ne sont pas autorisés dans l’étendue dynamique de `for`, `sections`, et `single` directives si le `master` directives lier au même `parallel` en tant que les directives de partage de travail.

- `ordered` directives ne sont pas autorisés dans l’étendue dynamique de `critical` régions si les directives lié à la même `parallel` en tant que les régions.

- N’importe quelle directive qui est autorisé lors de l’exécution dynamiquement à l’intérieur d’une région parallèle est également autorisée lors de l’exécution en dehors d’une région parallèle. Lors de l’exécution dynamiquement en dehors d’une région parallèle spécifié par l’utilisateur, la directive est exécutée par une équipe composée du thread principal uniquement.
