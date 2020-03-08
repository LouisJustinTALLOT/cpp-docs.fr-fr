---
title: 2. Directives
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882853"
---
# <a name="2-directives"></a>2. Directives

Les directives sont basées sur les directives de `#pragma` définies dans C++ le C et les normes.  Les compilateurs qui prennent en charge le C C++ et l’API OpenMP incluent une option de ligne de commande qui active et autorise l’interprétation de toutes les directives de compilateur openmp.

## <a name="21-directive-format"></a>format de directive 2,1

La syntaxe d’une directive OpenMP est formellement spécifiée par la grammaire de l' [annexe C](c-openmp-c-and-cpp-grammar.md), et de manière informelle, comme suit :

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Chaque directive commence par `#pragma omp`, afin de réduire le risque de conflit avec d’autres directives pragma (non OpenMP ou fournisseur pour OpenMP) portant le même nom. Le reste de la directive suit les conventions du C et C++ des normes pour les directives de compilateur. En particulier, les espaces blancs peuvent être utilisés avant et après la `#`, et parfois des espaces blancs doivent être utilisés pour séparer les mots dans une directive. Les jetons de prétraitement qui suivent le `#pragma omp` sont sujets au remplacement de macros.

Les directives respectent la casse. L’ordre dans lequel les clauses apparaissent dans les directives n’est pas significatif. Les clauses sur les directives peuvent être répétées selon les besoins, conformément aux restrictions indiquées dans la description de chaque clause. Si *variable-List* apparaît dans une clause, elle doit spécifier uniquement des variables. Un seul *nom de directive* peut être spécifié par directive.  Par exemple, la directive suivante n’est pas autorisée :

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Une directive OpenMP s’applique à au plus une instruction réussie, qui doit être un bloc structuré.

## <a name="22-conditional-compilation"></a>2,2 compilation conditionnelle

Le nom de la macro `_OPENMP` est défini par les implémentations conformes à OpenMP en tant que constante décimale *YYYYMM*, qui est l’année et le mois de la spécification approuvée. Cette macro ne doit pas être l’objet d’une `#define` ou d’une directive de prétraitement `#undef`.

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Si les fournisseurs définissent des extensions pour OpenMP, ils peuvent spécifier des macros prédéfinies supplémentaires.

## <a name="23-parallel-construct"></a>2,3 construction parallèle

La directive suivante définit une région parallèle, qui est une région du programme qui doit être exécutée par de nombreux threads en parallèle. Cette directive est la construction fondamentale qui démarre l’exécution parallèle.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

La *clause* est l’une des suivantes :

- `if(` *scalaire-expression* `)`
- `private(` `)` *de liste variable*
- `firstprivate(` `)` *de liste variable*
- `default(shared | none)`
- `shared(` `)` *de liste variable*
- `copyin(` `)` *de liste variable*
- `reduction(` *opérateur* `:``)` *de liste de variables*
- `num_threads(` *entier-expression* `)`

Quand un thread arrive à une construction parallèle, une équipe de threads est créée si l’un des cas suivants est vrai :

- Aucune clause `if` n’est présente.
- L’expression `if` correspond à une valeur différente de zéro.

Ce thread devient le thread principal de l’équipe, avec un numéro de thread égal à 0, et tous les threads de l’équipe, y compris le thread principal, exécutent la région en parallèle. Si la valeur de l’expression `if` est égale à zéro, la région est sérialisée.

Pour déterminer le nombre de threads demandés, les règles suivantes sont prises en compte dans l’ordre. La première règle dont la condition est remplie sera appliquée :

1. Si la clause `num_threads` est présente, la valeur de l’expression entière est le nombre de threads demandés.

1. Si la fonction de bibliothèque `omp_set_num_threads` a été appelée, la valeur de l’argument dans l’appel le plus récemment exécuté est le nombre de threads demandés.

1. Si la variable d’environnement `OMP_NUM_THREADS` est définie, la valeur de cette variable d’environnement est le nombre de threads demandés.

1. Si aucune des méthodes ci-dessus n’est utilisée, le nombre de threads demandés est défini par l’implémentation.

Si la clause `num_threads` est présente, elle remplace le nombre de threads demandés par la fonction de bibliothèque `omp_set_num_threads` ou la variable d’environnement `OMP_NUM_THREADS` uniquement pour la région parallèle à laquelle elle est appliquée. Les régions parallèles ultérieures ne sont pas affectées.

Le nombre de threads qui exécutent la région parallèle dépend également de l’activation ou non de l’ajustement dynamique du nombre de threads. Si l’ajustement dynamique est désactivé, le nombre de threads demandé exécutera la région parallèle. Si l’ajustement dynamique est activé, le nombre de threads demandé est le nombre maximal de threads qui peuvent exécuter la région parallèle.

Si une région parallèle est rencontrée alors que l’ajustement dynamique du nombre de threads est désactivé et que le nombre de threads demandés pour la région parallèle est supérieur au nombre que le système d’exécution peut fournir, le comportement du programme est défini par l’implémentation. Une implémentation peut, par exemple, interrompre l’exécution du programme ou sérialiser la région parallèle.

La fonction de bibliothèque `omp_set_dynamic` et la variable d’environnement `OMP_DYNAMIC` peuvent être utilisées pour activer et désactiver l’ajustement dynamique du nombre de threads.

Le nombre de processeurs physiques qui hébergent réellement les threads à un moment donné est défini par l’implémentation. Une fois créé, le nombre de threads dans l’équipe reste constant pour la durée de cette région parallèle. Il peut être modifié de manière explicite par l’utilisateur ou automatiquement par le système d’exécution d’une région parallèle à une autre.

Les instructions contenues dans l’étendue dynamique de la région parallèle sont exécutées par chaque thread, et chaque thread peut exécuter un chemin d’accès d’instructions différent des autres threads. Les directives rencontrées en dehors de l’étendue lexicale d’une région parallèle sont appelées directives orphelines.

Il existe un cloisonnement implicite à la fin d’une région parallèle. Seul le thread principal de l’équipe continue l’exécution à la fin d’une région parallèle.

Si un thread d’une équipe qui exécute une région parallèle rencontre une autre construction parallèle, il crée une nouvelle équipe et il devient le maître de cette nouvelle équipe. Les régions parallèles imbriquées sont sérialisées par défaut. Par conséquent, par défaut, une région parallèle imbriquée est exécutée par une équipe composée d’un thread. Le comportement par défaut peut être modifié à l’aide de la fonction de la bibliothèque Runtime `omp_set_nested` ou de la variable d’environnement `OMP_NESTED`. Toutefois, le nombre de threads dans une équipe qui exécutent une région parallèle imbriquée est défini par l’implémentation.

Les restrictions à la directive `parallel` sont les suivantes :

- Au maximum, une clause `if` peut apparaître sur la directive.

- Il n’est pas spécifié si des effets secondaires à l’intérieur de l’expression if ou de `num_threads` expression se produisent.

- Une `throw` exécutée dans une région parallèle doit entraîner la reprise de l’exécution dans l’étendue dynamique du même bloc structuré et doit être interceptée par le thread qui a levé l’exception.

- Une seule clause `num_threads` peut apparaître dans la directive. L’expression `num_threads` est évaluée en dehors du contexte de la région parallèle, et doit correspondre à une valeur entière positive.

- L’ordre d’évaluation des clauses `if` et `num_threads` n’est pas spécifié.

### <a name="cross-references"></a>Références croisées

- clauses `private`, `firstprivate`, `default`, `shared`, `copyin`et `reduction` ([section 2.7.2](#272-data-sharing-attribute-clauses))
- Variable d’environnement [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- fonction de la bibliothèque de [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- Variable d’environnement [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) fonction)
- Variable d’environnement [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- fonction de la bibliothèque de [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)

## <a name="24-work-sharing-constructs"></a>2,4 constructions de partage de travail

Une construction de partage de travail distribue l’exécution de l’instruction associée parmi les membres de l’équipe qui la rencontrent. Les directives de partage de travail ne lancent pas de nouveaux threads, et il n’existe pas de barrière implicite sur l’entrée d’une construction de partage de travail.

La séquence de constructions de partage de travail et de directives de `barrier` rencontrées doit être la même pour chaque thread d’une équipe.

OpenMP définit les constructions de partage de travail suivantes, et ces constructions sont décrites dans les sections suivantes :

- [pour](#241-for-construct) la directive
- [sections](#242-sections-construct) (directive)
- directive [unique](#243-single-construct)

### <a name="241-for-construct"></a>2.4.1 pour la construction

La directive `for` identifie une construction de partage de travail itérative qui spécifie que les itérations de la boucle associée seront exécutées en parallèle. Les itérations de la boucle `for` sont réparties entre les threads qui existent déjà dans l’équipe qui exécute la construction parallèle à laquelle elle est liée. La syntaxe de la construction `for` se présente comme suit :

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

La clause est l’une des suivantes :

- `private(` `)` *de liste variable*
- `firstprivate(` `)` *de liste variable*
- `lastprivate(` `)` *de liste variable*
- `reduction(` *opérateur* `:` `)` *de liste de variables*
- `ordered`
- `schedule(` *genre* [`,` *chunk_size*] `)`
- `nowait`

La directive `for` place des restrictions sur la structure de la boucle `for` correspondante. Plus précisément, la boucle `for` correspondante doit avoir une forme canonique :

`for (` *init-expr* `;` *var logique-op b* `;` *incr-expr* `)`

*init-expr*<br/>
Celui-ci peut avoir l'une des valeurs suivantes :

- *var* = *lb*
- *variable de type integer* = *lb*

*incr-expr*<br/>
Celui-ci peut avoir l'une des valeurs suivantes :

- `++` *var*
- `++` *var*
- `--` *var*
- `--` *var*
- *variable* `+=` *incr*
- *variable* `-=` *incr*
- *`=`* var *`+`* *incr*
- *var* `=` *incr* `+` *variable*
- *`=`* var *`-`* *incr*

*var*<br/>
Variable de type entier signé. Si cette variable serait partagée, elle est implicitement rendue privée pour la durée de la `for`. Ne modifiez pas cette variable dans le corps de l’instruction `for`. À moins que la variable ne soit spécifiée `lastprivate`, sa valeur après la boucle est indéterminée.

*opérations logiques*<br/>
Celui-ci peut avoir l'une des valeurs suivantes :

- `<`
- `<=`
- `>`
- `>=`

*lb*, *b*et *incr*<br>
Expressions d’entiers invariants de boucle. Aucune synchronisation n’est effectuée pendant l’évaluation de ces expressions, de sorte que tous les effets secondaires évalués produisent des résultats indéterminés.

La forme canonique permet de calculer le nombre d’itérations de boucle lors de l’entrée dans la boucle. Ce calcul est effectué avec des valeurs dans le type *var*, après les promotions intégrales. En particulier, si la valeur de *b* `-` *lb* `+` *incr* ne peut pas être représentée dans ce type, le résultat est indéterminé. De plus, si *Logical-op* est `<` ou `<=`, *incr-expr* doit entraîner l’augmentation de *var* à chaque itération de la boucle.   Si *Logical-op* est `>` ou `>=`, *incr-expr* doit faire en sorte que *var* soit plus petit sur chaque itération de la boucle.

La clause `schedule` spécifie le mode de répartition des itérations de la boucle `for` entre les threads de l’équipe. L’exactitude d’un programme ne doit pas dépendre du thread qui exécute une itération particulière. La valeur de *chunk_size*, si elle est spécifiée, doit être une expression entière d’invariant de boucle avec une valeur positive. Il n’existe aucune synchronisation pendant l’évaluation de cette expression, donc tous les effets secondaires évalués produisent des résultats indéterminés. Le *genre* de planification peut être l’une des valeurs suivantes :

Tableau 2-1 : valeurs de *type* de la clause `schedule`

|||
|-|-|
|statique|Lorsque `schedule(static,` *chunk_size* `)` est spécifié, les itérations sont divisées en segments d’une taille spécifiée par *chunk_size*. Les segments sont attribués de manière statique aux threads de l’équipe en mode tourniquet (Round Robin) dans l’ordre du numéro de thread. Quand aucun *chunk_size* n’est spécifié, l’espace d’itération est divisé en segments dont la taille est approximativement égale, avec un segment affecté à chaque thread.|
|dynamique|Lorsque `schedule(dynamic,` *chunk_size* `)` est spécifié, les itérations sont divisées en une série de segments, chacun contenant *chunk_size* itérations. Chaque segment est assigné à un thread qui attend une attribution. Le thread exécute le segment des itérations, puis attend la prochaine affectation, jusqu’à ce qu’il ne reste aucun segment à assigner. Le dernier segment à affecter peut avoir un plus petit nombre d’itérations. Quand aucun *chunk_size* n’est spécifié, la valeur par défaut est 1.|
|guider|Lorsque `schedule(guided,` *chunk_size* `)` est spécifié, les itérations sont assignées aux threads dans des segments avec des tailles décroissantes. Quand un thread termine son bloc d’itérations affecté, il reçoit dynamiquement un autre bloc, jusqu’à ce qu’il ne reste aucun élément. Pour un *chunk_size* de 1, la taille de chaque segment est approximativement le nombre d’itérations non assignées divisé par le nombre de threads. Ces tailles diminuent presque de façon exponentielle jusqu’à 1. Pour un *chunk_size* avec la valeur *k* supérieure à 1, les tailles diminuent presque de façon exponentielle jusqu’à *k*, sauf que le dernier segment peut avoir moins de *k* itérations. Quand aucun *chunk_size* n’est spécifié, la valeur par défaut est 1.|
|runtime|Lorsque `schedule(runtime)` est spécifié, la décision relative à la planification est différée jusqu’au moment de l’exécution. Le *type* et la taille de la planification des segments peuvent être choisis au moment de l’exécution en définissant la variable d’environnement `OMP_SCHEDULE`. Si cette variable d’environnement n’est pas définie, la planification résultante est définie par l’implémentation. Lorsque `schedule(runtime)` est spécifié, *chunk_size* ne doit pas être spécifié.|

En l’absence d’une clause `schedule` définie explicitement, la `schedule` par défaut est définie par l’implémentation.

Un programme conforme à OpenMP ne doit pas reposer sur une planification particulière pour une exécution correcte. Un programme ne doit pas reposer sur un *type* de planification conforme précisément à la description ci-dessus, car il est possible d’avoir des variations dans les implémentations du même *type* de planification entre différents compilateurs. Les descriptions peuvent être utilisées pour sélectionner la planification appropriée à une situation particulière.

La clause `ordered` doit être présente lorsque `ordered` directives sont liées à la construction `for`.

Il existe un cloisonnement implicite à la fin d’une construction `for`, sauf si une clause `nowait` est spécifiée.

Les restrictions à la directive `for` sont les suivantes :

- La boucle `for` doit être un bloc structuré et, par ailleurs, son exécution ne doit pas être terminée par une instruction `break`.

- Les valeurs des expressions de contrôle de boucle de la boucle `for` associée à une directive `for` doivent être les mêmes pour tous les threads de l’équipe.

- La variable d’itération de la boucle `for` doit avoir un type entier signé.

- Une seule clause `schedule` peut apparaître dans une directive `for`.

- Une seule clause `ordered` peut apparaître dans une directive `for`.

- Une seule clause `nowait` peut apparaître dans une directive `for`.

- Il n’est pas spécifié si ou la fréquence à laquelle les effets secondaires dans les expressions *chunk_size*, *lb*, *b*ou *incr* se produisent.

- La valeur de l’expression de *chunk_size* doit être la même pour tous les threads de l’équipe.

#### <a name="cross-references"></a>Références croisées

- clauses `private`, `firstprivate`, `lastprivate`et `reduction` ([section 2.7.2](#272-data-sharing-attribute-clauses))
- Variable d’environnement [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)
- construction [ordonnée](#266-ordered-construct)
- clause [Schedule](d-using-the-schedule-clause.md)

### <a name="242-sections-construct"></a>2.4.2 construction de sections

La directive `sections` identifie une construction de partage de travail non itérative qui spécifie un ensemble de constructions qui doivent être réparties parmi les threads d’une équipe. Chaque section est exécutée une seule fois par un thread de l’équipe. La syntaxe de la directive `sections` se présente comme suit :

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

La clause est l’une des suivantes :

- `private(` `)` *de liste variable*
- `firstprivate(` `)` *de liste variable*
- `lastprivate(` `)` *de liste variable*
- `reduction(` *opérateur* `:``)` *de liste de variables*
- `nowait`

Chaque section est précédée d’une directive `section`, bien que la directive `section` soit facultative pour la première section. Les directives `section` doivent apparaître dans l’étendue lexicale de la directive `sections`. Il existe un cloisonnement implicite à la fin d’une construction de `sections`, sauf si un `nowait` est spécifié.

Les restrictions à la directive `sections` sont les suivantes :

- Une directive de `section` ne doit pas figurer en dehors de l’étendue lexicale de la directive `sections`.

- Une seule clause `nowait` peut apparaître dans une directive `sections`.

#### <a name="cross-references"></a>Références croisées

- clauses `private`, `firstprivate`, `lastprivate`et `reduction` ([section 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 construction unique

La directive `single` identifie une construction qui spécifie que le bloc structuré associé est exécuté par un seul thread de l’équipe (pas nécessairement le thread principal). La syntaxe de la directive `single` se présente comme suit :

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

La clause est l’une des suivantes :

- `private(` `)` *de liste variable*
- `firstprivate(` `)` *de liste variable*
- `copyprivate(` `)` *de liste variable*
- `nowait`

Il existe un cloisonnement implicite après la construction `single`, sauf si une clause `nowait` est spécifiée.

Les restrictions à la directive `single` sont les suivantes :

- Une seule clause `nowait` peut apparaître dans une directive `single`.
- La clause `copyprivate` ne doit pas être utilisée avec la clause `nowait`.

#### <a name="cross-references"></a>Références croisées

- clauses `private`, `firstprivate`et `copyprivate` ([section 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2,5 constructions combinées de partage de travail parallèles

Les constructions combinées de partage de travail parallèles sont des raccourcis permettant de spécifier une région parallèle qui n’a qu’une seule construction de partage de travail. La sémantique de ces directives est identique à la spécification explicite d’une directive `parallel` suivie d’une seule construction de partage de travail.

Les sections suivantes décrivent les constructions de partage de travail parallèles combinées :

- [Parallel pour](#251-parallel-for-construct) la directive
- directive de [sections parallèles](#252-parallel-sections-construct)

### <a name="251-parallel-for-construct"></a>2.5.1 construction parallèle for

La directive `parallel for` est un raccourci pour une région `parallel` qui contient une seule directive `for`. La syntaxe de la directive `parallel for` se présente comme suit :

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Cette directive autorise toutes les clauses de la directive `parallel` et de la directive `for`, à l’exception de la clause `nowait`, avec des significations et des restrictions identiques. La sémantique est identique à la spécification explicite d’une directive `parallel` immédiatement suivie d’une directive `for`.

#### <a name="cross-references"></a>Références croisées

- [Parallel](#23-parallel-construct) (directive)
- [pour](#241-for-construct) la directive
- [Clauses d’attribut de données](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>construction de sections parallèles 2.5.2

La directive `parallel sections` fournit un formulaire de raccourci pour spécifier une région `parallel` qui n’a qu’une seule directive `sections`. La sémantique est identique à la spécification explicite d’une directive `parallel` immédiatement suivie d’une directive `sections`. La syntaxe de la directive `parallel sections` se présente comme suit :

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

La *clause* peut être l’une des clauses acceptées par les directives `parallel` et `sections`, à l’exception de la clause `nowait`.

#### <a name="cross-references"></a>Références croisées

- [Parallel](#23-parallel-construct) (directive)
- [sections](#242-sections-construct) (directive)

## <a name="26-master-and-synchronization-directives"></a>2,6 directives principales et de synchronisation

Les sections suivantes décrivent :

- construction [principale](#261-master-construct)
- construction [critique](#262-critical-construct)
- [barrière](#263-barrier-directive) (directive)
- [Atomic](#264-atomic-construct) (construction)
- [flush](#265-flush-directive) (directive)
- construction [ordonnée](#266-ordered-construct)

### <a name="261-master-construct"></a>base de construction Master 2.6.1

La directive `master` identifie une construction qui spécifie un bloc structuré qui est exécuté par le thread principal de l’équipe. La syntaxe de la directive `master` se présente comme suit :

```cpp
#pragma omp master new-linestructured-block
```

Les autres threads de l’équipe n’exécutent pas le bloc structuré associé. Il n’existe aucune barrière implicite à l’entrée ou à la sortie de la construction principale.

### <a name="262-critical-construct"></a>construction critique 2.6.2

La directive `critical` identifie une construction qui limite l’exécution du bloc structuré associé à un thread unique à la fois. La syntaxe de la directive `critical` se présente comme suit :

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

Un *nom* facultatif peut être utilisé pour identifier la région critique. Les identificateurs utilisés pour identifier une région critique ont une liaison externe et se trouvent dans un espace de noms distinct des espaces de noms utilisés par les étiquettes, les balises, les membres et les identificateurs ordinaires.

Un thread attend au début d’une région critique jusqu’à ce qu’aucun autre thread n’exécute une région critique (n’importe où dans le programme) avec le même nom. Toutes les directives de `critical` sans nom mappent au même nom non spécifié.

### <a name="263-barrier-directive"></a>directive de cloisonnement 2.6.3

La directive `barrier` synchronise tous les threads d’une équipe. En cas de rencontre, chaque thread de l’équipe attend que tous les autres threads aient atteint ce point. La syntaxe de la directive `barrier` se présente comme suit :

```cpp
#pragma omp barrier new-line
```

Une fois que tous les threads de l’équipe ont rencontré le cloisonnement, chaque thread de l’équipe commence à exécuter les instructions après la directive de cloisonnement en parallèle. Étant donné que la directive `barrier` n’a pas d’instruction de langage C dans le cadre de sa syntaxe, il existe des restrictions quant à son emplacement dans un programme. Pour plus d’informations sur la grammaire formelle, consultez l' [annexe C](c-openmp-c-and-cpp-grammar.md). L’exemple ci-dessous illustre ces restrictions.

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

### <a name="264-atomic-construct"></a>2.6.4 (construction atomique)

La directive `atomic` garantit qu’un emplacement de mémoire spécifique est mis à jour atomiquement, au lieu de l’exposer à la possibilité de plusieurs threads d’écriture simultanés. La syntaxe de la directive `atomic` se présente comme suit :

```cpp
#pragma omp atomic new-lineexpression-stmt
```

L’instruction d’expression doit avoir l’une des formes suivantes :

- *x binop* `=` *expr*
- `++` *x*
- `++` *x*
- `--` *x*
- `--` *x*

Dans les expressions précédentes :

- *x* est une expression lvalue avec un type scalaire.

- *expr* est une expression avec un type scalaire et ne fait pas référence à l’objet désigné par *x*.

- *binop* n’est pas un opérateur surchargé et est l’un des `+`, `*`, `-`, `/`, `&`, `^`, `|`, `<<`ou `>>`.

Bien qu’elle soit définie par l’implémentation si une implémentation remplace toutes les directives `atomic` par des directives `critical` qui ont le même *nom*unique, la directive `atomic` permet une meilleure optimisation. Des instructions matérielles sont souvent disponibles pour effectuer la mise à jour atomique avec la surcharge la plus faible.

Seule la charge et le magasin de l’objet désigné par *x* sont atomiques ; l’évaluation de *expr* n’est pas atomique. Pour éviter les conditions de concurrence, toutes les mises à jour de l’emplacement en parallèle doivent être protégées par la directive `atomic`, à l’exception de celles qui sont connues comme étant libres de conditions de concurrence.

Les restrictions à la directive `atomic` sont les suivantes :

- Toutes les références atomiques à l’emplacement de stockage x de l’ensemble du programme doivent avoir un type compatible.

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

### <a name="265-flush-directive"></a>2.6.5, directive Flush

La directive `flush`, qu’elle soit explicite ou implicite, spécifie un point de séquence « inter-threads » auquel l’implémentation est requise pour s’assurer que tous les threads d’une équipe disposent d’une vue cohérente de certains objets (spécifiés ci-dessous) en mémoire. Cela signifie que les évaluations précédentes d’expressions qui font référence à ces objets sont terminées et que les évaluations suivantes n’ont pas encore commencé. Par exemple, les compilateurs doivent restaurer les valeurs des objets des registres vers la mémoire, et le matériel peut avoir besoin de vider les mémoires tampons d’écriture dans la mémoire et de recharger les valeurs des objets à partir de la mémoire.

La syntaxe de la directive `flush` se présente comme suit :

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Si les objets qui nécessitent une synchronisation peuvent tous être désignés par des variables, ces variables peuvent être spécifiées dans la *liste*de variables facultative. Si un pointeur est présent dans la *liste de variables*, le pointeur lui-même est vidé, et non l’objet auquel le pointeur fait référence.

Une `flush` directive sans *variable-List* synchronise tous les objets partagés, à l’exception des objets inaccessibles avec une durée de stockage automatique. (Cela peut avoir plus de surcharge qu’un `flush` avec une *liste de variables*.) Une directive `flush` sans *liste de variables* est implicite pour les directives suivantes :

- `barrier`
- À l’entrée et à la sortie de `critical`
- À l’entrée et à la sortie de `ordered`
- À l’entrée et à la sortie de `parallel`
- À la sortie de `for`
- À la sortie de `sections`
- À la sortie de `single`
- À l’entrée et à la sortie de `parallel for`
- À l’entrée et à la sortie de `parallel sections`

La directive n’est pas impliquée si une clause `nowait` est présente. Il convient de noter que la directive `flush` n’est pas implicite pour les éléments suivants :

- À l’entrée pour `for`
- À l’entrée ou à la sortie de `master`
- À l’entrée pour `sections`
- À l’entrée pour `single`

Une référence qui accède à la valeur d’un objet avec un type qualifié volatil se comporte comme s’il existait une `flush` directive spécifiant cet objet au point de séquence précédent. Une référence qui modifie la valeur d’un objet avec un type qualifié volatil se comporte comme s’il existait une `flush` directive spécifiant cet objet au point de séquence suivant.

Étant donné que la directive `flush` n’a pas d’instruction de langage C dans le cadre de sa syntaxe, il existe des restrictions quant à son emplacement dans un programme. Pour plus d’informations sur la grammaire formelle, consultez l' [annexe C](c-openmp-c-and-cpp-grammar.md). L’exemple ci-dessous illustre ces restrictions.

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

Les restrictions à la directive `flush` sont les suivantes :

- Une variable spécifiée dans une directive `flush` ne doit pas avoir de type référence.

### <a name="266-ordered-construct"></a>construction ordonnée 2.6.6

Le bloc structuré qui suit une directive `ordered` est exécuté dans l’ordre dans lequel les itérations sont exécutées dans une boucle séquentielle. La syntaxe de la directive `ordered` se présente comme suit :

```cpp
#pragma omp ordered new-linestructured-block
```

Une directive `ordered` doit se trouver dans l’étendue dynamique d’une construction `for` ou `parallel for`. La directive `for` ou `parallel for` à laquelle la construction de `ordered` crée une liaison doit avoir une clause `ordered` spécifiée comme décrit dans la [section 2.4.1](#241-for-construct). Dans l’exécution d’une construction `for` ou `parallel for` avec une clause `ordered`, les constructions `ordered` sont exécutées de façon stricte dans l’ordre dans lequel elles sont exécutées dans une exécution séquentielle de la boucle.

Les restrictions à la directive `ordered` sont les suivantes :

- Une itération d’une boucle avec une construction `for` ne doit pas exécuter la même directive ordonnée plusieurs fois, et elle ne doit pas exécuter plus d’une directive `ordered`.

## <a name="27-data-environment"></a>2,7 environnement de données

Cette section présente une directive et plusieurs clauses pour contrôler l’environnement de données pendant l’exécution des régions parallèles, comme suit :

- Une directive [threadprivate](#271-threadprivate-directive) est fournie pour rendre les variables de portée de fichier, de portée espace de noms ou de portée de bloc statiques locales sur un thread.

- Les clauses qui peuvent être spécifiées dans les directives pour contrôler les attributs de partage de variables pendant la durée des constructions parallèles ou de partage de travail sont décrites dans la [section 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 (directive threadprivate)

La directive `threadprivate` rend l’étendue de fichier nommée, la portée de l’espace de noms ou les variables de portée de bloc statiques spécifiées dans la *liste de variables* privée d’un thread. *variable-List* est une liste séparée par des virgules de variables qui n’ont pas de type incomplet. La syntaxe de la directive `threadprivate` se présente comme suit :

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Chaque copie d’une variable `threadprivate` est initialisée une seule fois, à un point non spécifié du programme avant la première référence à cette copie, et de la manière habituelle (c’est-à-dire que la copie principale est initialisée dans une exécution en série du programme). Notez que si un objet est référencé dans un initialiseur explicite d’une variable `threadprivate`, et que la valeur de l’objet est modifiée avant la première référence à une copie de la variable, le comportement n’est pas spécifié.

Comme pour toute variable privée, un thread ne doit pas référencer la copie d’un objet `threadprivate` d’un autre thread. Dans les régions et les régions principales du programme, les références sont représentées par la copie de l’objet du thread principal.

Après l’exécution de la première région parallèle, les données des objets `threadprivate` sont conservées uniquement si le mécanisme de threads dynamiques a été désactivé et si le nombre de threads reste inchangé pour toutes les régions parallèles.

Les restrictions à la directive `threadprivate` sont les suivantes :

- Une directive de `threadprivate` pour les variables de portée de fichier ou de portée espace de noms doit apparaître en dehors d’une définition ou d’une déclaration, et doit précéder lexicalement toutes les références aux variables de sa liste.

- Chaque variable de la *liste variable* d’une directive `threadprivate` au niveau de la portée de fichier ou d’espace de noms doit faire référence à une déclaration de variable au niveau de la portée de fichier ou d’espace de noms qui précède lexicalement la directive.

- Une directive de `threadprivate` pour les variables de portée de bloc statiques doit apparaître dans l’étendue de la variable et non dans une portée imbriquée. La directive doit précéder lexicalement toutes les références aux variables de sa liste.

- Chaque variable de la *liste de variables* d’une directive `threadprivate` dans la portée de bloc doit faire référence à une déclaration de variable dans la même portée qui précède lexicalement la directive. La déclaration de variable doit utiliser le spécificateur de classe de stockage statique.

- Si une variable est spécifiée dans une directive `threadprivate` dans une unité de traduction, elle doit être spécifiée dans une `threadprivate` directive dans chaque unité de traduction dans laquelle elle est déclarée.

- Une variable `threadprivate` ne doit pas apparaître dans une clause, à l’exception de la clause `copyin`, `copyprivate`, `schedule`, `num_threads`ou `if`.

- L’adresse d’une variable de `threadprivate` n’est pas une constante d’adresse.

- Une variable `threadprivate` ne doit pas avoir un type incomplet ou un type référence.

- Une variable `threadprivate` avec un type de classe non POD doit avoir un constructeur de copie accessible et non ambigu s’il est déclaré avec un initialiseur explicite.

L’exemple suivant illustre la manière dont la modification d’une variable qui apparaît dans un initialiseur peut provoquer un comportement non spécifié, ainsi que la façon d’éviter ce problème en utilisant un objet auxiliaire et un constructeur de copie.

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
- Variable d’environnement [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2, clauses d’attributs de partage de données

Plusieurs directives acceptent des clauses qui permettent à un utilisateur de contrôler les attributs de partage de variables pour la durée de la région. Les clauses d’attribut de partage s’appliquent uniquement aux variables dans l’étendue lexicale de la directive sur laquelle la clause apparaît. Toutes les clauses suivantes ne sont pas autorisées dans toutes les directives. La liste des clauses qui sont valides sur une directive particulière est décrite par la directive.

Si une variable est visible lorsqu’une construction de partage de travail ou parallèle est rencontrée, et que la variable n’est pas spécifiée dans une clause d’attribut de partage ou une directive de `threadprivate`, la variable est partagée. Les variables statiques déclarées dans l’étendue dynamique d’une région parallèle sont partagées. La mémoire allouée au tas (par exemple, à C++ l’aide de `malloc()` dans C++C ou ou dans l’opérateur `new` dans) est partagée. (Toutefois, le pointeur vers cette mémoire peut être privé ou partagé.) Les variables avec une durée de stockage automatique déclarée dans l’étendue dynamique d’une région parallèle sont privées.

La plupart des clauses acceptent un argument de *liste* de variables, qui est une liste séparée par des virgules de variables qui sont visibles. Si une variable référencée dans une clause d’attribut de partage de données a un type dérivé d’un modèle et qu’il n’existe aucune autre référence à cette variable dans le programme, le comportement n’est pas défini.

Toutes les variables qui apparaissent dans les clauses de directive doivent être visibles. Les clauses peuvent être répétées en fonction des besoins, mais aucune variable ne peut être spécifiée dans plusieurs clauses, à la différence qu’une variable peut être spécifiée à la fois dans une `firstprivate` et dans une clause `lastprivate`.

Les sections suivantes décrivent les clauses d’attributs de partage de données :

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [partagé](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

La clause `private` déclare que les variables de la liste de variables doivent être privées pour chaque thread d’une équipe. La syntaxe de la clause `private` se présente comme suit :

```cpp
private(variable-list)
```

Le comportement d’une variable spécifiée dans une clause `private` est le suivant. Un nouvel objet avec une durée de stockage automatique est alloué pour la construction. La taille et l’alignement du nouvel objet sont déterminés par le type de la variable. Cette allocation se produit une fois pour chaque thread de l’équipe, et un constructeur par défaut est appelé pour un objet de classe, si nécessaire ; dans le cas contraire, la valeur initiale est indéterminée.  L’objet d’origine référencé par la variable a une valeur indéterminée au moment de l’entrée dans la construction, ne doit pas être modifié dans l’étendue dynamique de la construction et a une valeur indéterminée à la sortie de la construction.

Dans l’étendue lexicale de la construction de directive, la variable fait référence au nouvel objet privé alloué par le thread.

Les restrictions de la clause `private` sont les suivantes :

- Une variable avec un type de classe spécifié dans une clause `private` doit avoir un constructeur par défaut accessible et non ambigu.

- Une variable spécifiée dans une clause `private` ne doit pas avoir un type qualifié `const`, sauf si elle a un type de classe avec un membre `mutable`.

- Une variable spécifiée dans une clause `private` ne doit pas avoir un type incomplet ou un type référence.

- Les variables qui apparaissent dans la clause `reduction` d’une directive `parallel` ne peuvent pas être spécifiées dans une clause `private` sur une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

La clause `firstprivate` fournit un sur-ensemble des fonctionnalités fournies par la clause `private`. La syntaxe de la clause `firstprivate` se présente comme suit :

```cpp
firstprivate(variable-list)
```

Les variables spécifiées dans *une liste de variables* ont `private` sémantique des clauses, comme décrit dans la [section 2.7.2.1](#2721-private). L’initialisation ou la construction se produit comme si elle était effectuée une fois par thread, avant l’exécution du thread de la construction. Pour une clause `firstprivate` sur une construction parallèle, la valeur initiale du nouvel objet privé est la valeur de l’objet d’origine qui existe immédiatement avant la construction parallèle pour le thread qui l’rencontre. Pour une clause `firstprivate` sur une construction de partage de travail, la valeur initiale du nouvel objet privé pour chaque thread qui exécute la construction de partage de travail est la valeur de l’objet d’origine qui existe avant le moment où le même thread rencontre la construction de partage de travail. En outre, pour C++ les objets, le nouvel objet privé pour chaque thread est une copie construite à partir de l’objet d’origine.

Les restrictions de la clause `firstprivate` sont les suivantes :

- Une variable spécifiée dans une clause `firstprivate` ne doit pas avoir un type incomplet ou un type référence.

- Une variable avec un type de classe spécifié comme `firstprivate` doit avoir un constructeur de copie accessible et non ambigu.

- Les variables privées dans une région parallèle ou qui s’affichent dans la clause `reduction` d’une directive `parallel` ne peuvent pas être spécifiées dans une clause `firstprivate` sur une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

La clause `lastprivate` fournit un sur-ensemble des fonctionnalités fournies par la clause `private`. La syntaxe de la clause `lastprivate` se présente comme suit :

```cpp
lastprivate(variable-list)
```

Les variables spécifiées dans la *liste de variables* ont `private` la sémantique de la clause. Quand une clause `lastprivate` apparaît sur la directive qui identifie une construction de partage de travail, la valeur de chaque variable `lastprivate` de la dernière itération de la boucle associée, ou de la directive lexicale de la dernière section, est assignée à l’objet d’origine de la variable. Les variables qui n’ont pas de valeur assignée par la dernière itération du `for` ou `parallel for`, ou par la dernière section lexicale de la directive `sections` ou `parallel sections`, ont des valeurs indéterminées après la construction. Les sous-objets non assignés ont également une valeur indéterminée après la construction.

Les restrictions de la clause `lastprivate` sont les suivantes :

- Toutes les restrictions pour `private` s’appliquent.

- Une variable avec un type de classe spécifié comme `lastprivate` doit avoir un opérateur d’assignation de copie accessible et non ambigu.

- Les variables privées dans une région parallèle ou qui s’affichent dans la clause `reduction` d’une directive `parallel` ne peuvent pas être spécifiées dans une clause `lastprivate` sur une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2724-shared"></a>2.7.2.4 shared

Cette clause partage les variables qui s’affichent dans la *liste variable* parmi tous les threads d’une équipe. Tous les threads d’une équipe accèdent à la même zone de stockage pour les variables de `shared`.

La syntaxe de la clause `shared` se présente comme suit :

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

La clause `default` permet à l’utilisateur d’affecter les attributs de partage de données des variables. La syntaxe de la clause `default` se présente comme suit :

```cpp
default(shared | none)
```

La spécification de `default(shared)` équivaut à répertorier explicitement chaque variable actuellement visible dans une clause `shared`, sauf si elle est `threadprivate` ou `const`qualifiée. En l’absence d’une clause `default` explicite, le comportement par défaut est le même que si `default(shared)` été spécifié.

Si vous spécifiez `default(none)`, il faut qu’au moins l’un des éléments suivants soit vrai pour chaque référence à une variable dans l’étendue lexicale de la construction parallèle :

- La variable est explicitement listée dans une clause d’attribut de partage de données d’une construction qui contient la référence.

- La variable est déclarée dans la construction parallèle.

- La variable est `threadprivate`.

- La variable a un type qualifié par `const`.

- La variable est la variable de contrôle de boucle pour une `for` boucle qui suit immédiatement une directive `for` ou `parallel for`, et la référence à la variable apparaît à l’intérieur de la boucle.

La spécification d’une variable sur une clause `firstprivate`, `lastprivate`ou `reduction` d’une directive entourée provoque une référence implicite à la variable dans le contexte englobant. Ces références implicites sont également soumises aux exigences répertoriées ci-dessus.

Une seule clause `default` peut être spécifiée sur une directive `parallel`.

L’attribut de partage de données par défaut d’une variable peut être substitué à l’aide des clauses `private`, `firstprivate`, `lastprivate`, `reduction`et `shared`, comme illustré dans l’exemple suivant :

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

Cette clause effectue une réduction sur les variables scalaires qui apparaissent dans la *liste de variables*, avec l’opérateur *op*. La syntaxe de la clause `reduction` se présente comme suit :

`reduction(` *op* `:` `)` *de liste de variables*

Une réduction est généralement spécifiée pour une instruction de l’une des façons suivantes :

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* (sauf en cas de soustraction)
- `++` *x*
- `++` *x*
- `--` *x*
- `--` *x*

où :

*x*<br/>
Une des variables de réduction spécifiées dans la liste.

*liste de variables*<br/>
Liste séparée par des virgules de variables de réduction scalaires.

*expr*<br/>
Expression avec un type scalaire qui ne fait pas référence à *x*.

*opérationnel*<br/>
N’est pas un opérateur surchargé, mais l’un des `+`, `*`, `-`, `&`, `^`, `|`, `&&`ou `||`.

*binop*<br/>
N’est pas un opérateur surchargé, mais l’un des `+`, `*`, `-`, `&`, `^`ou `|`.

Voici un exemple de la clause `reduction` :

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Comme indiqué dans l’exemple, un opérateur peut être masqué dans un appel de fonction. L’utilisateur doit veiller à ce que l’opérateur spécifié dans la clause `reduction` corresponde à l’opération de réduction.

Bien que l’opérande droit de l’opérateur `||` n’ait aucun effet secondaire dans cet exemple, ils sont autorisés, mais doivent être utilisés avec précaution. Dans ce contexte, un effet secondaire garanti ne pas se produire pendant l’exécution séquentielle de la boucle peut se produire pendant une exécution parallèle. Cette différence peut se produire parce que l’ordre d’exécution des itérations est indéterminé.

L’opérateur est utilisé pour déterminer la valeur initiale de toutes les variables privées utilisées par le compilateur pour la réduction et pour déterminer l’opérateur de finalisation. La spécification explicite de l’opérateur permet à l’instruction de réduction de se trouver en dehors de l’étendue lexicale de la construction. N’importe quel nombre de clauses `reduction` peut être spécifié sur la directive, mais une variable peut apparaître dans au plus une clause `reduction` pour cette directive.

Une copie privée de chaque variable de la *liste de variables* est créée, une pour chaque thread, comme si la clause `private` avait été utilisée. La copie privée est initialisée en fonction de l’opérateur (consultez le tableau suivant).

À la fin de la région pour laquelle la clause `reduction` a été spécifiée, l’objet d’origine est mis à jour pour refléter le résultat de la combinaison de sa valeur d’origine avec la valeur finale de chacune des copies privées à l’aide de l’opérateur spécifié. Les opérateurs de réduction sont tous associatifs (à l’exception de la soustraction) et le compilateur peut réassocier librement le calcul de la valeur finale. (Les résultats partiels d’une réduction de soustraction sont ajoutés pour former la valeur finale.)

La valeur de l’objet d’origine devient indéterminée lorsque le premier thread atteint la clause conteneur et reste tant que le calcul de la réduction n’est pas terminé.  Normalement, le calcul sera terminé à la fin de la construction ; Toutefois, si la clause `reduction` est utilisée sur une construction à laquelle `nowait` est également appliqué, la valeur de l’objet d’origine reste indéterminée jusqu’à ce qu’une synchronisation de cloisonnement ait été effectuée pour s’assurer que tous les threads ont terminé la clause `reduction`.

Le tableau suivant répertorie les opérateurs qui sont valides et leurs valeurs d’initialisation canoniques. La valeur d’initialisation réelle sera cohérente avec le type de données de la variable de réduction.

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

Les restrictions de la clause `reduction` sont les suivantes :

- Le type des variables dans la clause `reduction` doit être valide pour l’opérateur de réduction, sauf que les types pointeur et les types référence ne sont jamais autorisés.

- Une variable spécifiée dans la clause `reduction` ne doit pas être qualifiée d' `const`.

- Les variables privées dans une région parallèle ou qui s’affichent dans la clause `reduction` d’une directive `parallel` ne peuvent pas être spécifiées dans une clause `reduction` sur une directive de partage de travail qui est liée à la construction parallèle.

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

La clause `copyin` fournit un mécanisme permettant d’assigner la même valeur à `threadprivate` variables pour chaque thread de l’équipe qui exécute la région parallèle. Pour chaque variable spécifiée dans une clause `copyin`, la valeur de la variable dans le thread principal de l’équipe est copiée, comme dans le cas d’une assignation, aux copies thread-Private au début de la région parallèle. La syntaxe de la clause `copyin` se présente comme suit :

```cpp

copyin(
variable-list
)
```

Les restrictions de la clause `copyin` sont les suivantes :

- Une variable spécifiée dans la clause `copyin` doit avoir un opérateur d’assignation de copie accessible et non ambigu.

- Une variable spécifiée dans la clause `copyin` doit être une variable `threadprivate`.

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

La clause `copyprivate` fournit un mécanisme permettant d’utiliser une variable privée pour diffuser une valeur d’un membre d’une équipe vers les autres membres. C’est une alternative à l’utilisation d’une variable partagée pour la valeur lors de la fourniture d’une telle variable partagée serait difficile (par exemple, dans une récurrence nécessitant une variable différente à chaque niveau). La clause `copyprivate` ne peut apparaître que dans la directive `single`.

La syntaxe de la clause `copyprivate` se présente comme suit :

```cpp

copyprivate(
variable-list
)
```

L’effet de la clause `copyprivate` sur les variables de sa liste variable se produit après l’exécution du bloc structuré associé à la construction `single`, et avant que les threads de l’équipe aient quitté le cloisonnement à la fin de la construction. Ensuite, dans tous les autres threads de l’équipe, pour chaque variable de la *liste variable*, cette variable devient définie (comme dans le cas d’une assignation) avec la valeur de la variable correspondante dans le thread qui a exécuté le bloc structuré de la construction.

Les restrictions de la clause `copyprivate` sont les suivantes :

- Une variable spécifiée dans la clause `copyprivate` ne doit pas apparaître dans une clause `private` ou `firstprivate` pour la même directive `single`.

- Si une directive `single` avec une clause `copyprivate` est rencontrée dans l’étendue dynamique d’une région parallèle, toutes les variables spécifiées dans la clause `copyprivate` doivent être privées dans le contexte englobant.

- Une variable spécifiée dans la clause `copyprivate` doit avoir un opérateur d’assignation de copie non ambigu accessible.

## <a name="28-directive-binding"></a>2,8 liaison de directive

La liaison dynamique des directives doit respecter les règles suivantes :

- Les directives `for`, `sections`, `single`, `master`et `barrier` sont liées au `parallel`englobant dynamiquement, le cas échéant, quelle que soit la valeur de toute clause `if` qui peut être présente sur cette directive. Si aucune région parallèle n’est en cours d’exécution, les directives sont exécutées par une équipe composée uniquement du thread principal.

- La directive `ordered` est liée au `for`englobant dynamiquement.

- La directive `atomic` applique un accès exclusif en ce qui concerne les directives `atomic` dans tous les threads, pas seulement l’équipe actuelle.

- La directive `critical` applique un accès exclusif en ce qui concerne les directives `critical` dans tous les threads, pas seulement l’équipe actuelle.

- Une directive ne peut jamais être liée à une directive en dehors de la `parallel`englobante dynamique la plus proche.

## <a name="29-directive-nesting"></a>2,9 imbrication de directives

L’imbrication dynamique de directives doit respecter les règles suivantes :

- Une directive de `parallel` dynamiquement dans une autre `parallel` établit logiquement une nouvelle équipe, composée uniquement du thread actuel, à moins que le parallélisme imbriqué soit activé.

- les directives `for`, `sections`et `single` qui lient au même `parallel` ne sont pas autorisées à être imbriquées les unes dans les autres.

- les directives de `critical` portant le même nom ne peuvent pas être imbriquées les unes dans les autres. Notez que cette restriction n’est pas suffisante pour empêcher l’interblocage.

- les directives `for`, `sections`et `single` ne sont pas autorisées dans l’étendue dynamique des `critical`, des `ordered`et des régions `master` si les directives sont liées au même `parallel` que les régions.

- les directives de `barrier` ne sont pas autorisées dans l’étendue dynamique des régions `for`, `ordered`, `sections`, `single`, `master`et `critical` si les directives lient les mêmes `parallel` que les régions.

- les directives de `master` ne sont pas autorisées dans l’étendue dynamique des directives `for`, `sections`et `single` si les directives `master` sont liées au même `parallel` que les directives de partage de travail.

- les directives de `ordered` ne sont pas autorisées dans l’étendue dynamique des `critical` régions si celles-ci sont liées à la même `parallel` que les régions.

- Toute directive autorisée lorsqu’elle est exécutée dynamiquement à l’intérieur d’une région parallèle est également autorisée lorsqu’elle est exécutée en dehors d’une région parallèle. Lorsqu’elle est exécutée dynamiquement en dehors d’une région parallèle spécifiée par l’utilisateur, la directive est exécutée par une équipe composée uniquement du thread principal.
