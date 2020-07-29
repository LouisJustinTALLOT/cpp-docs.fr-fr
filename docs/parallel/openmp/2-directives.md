---
title: 2. Directives
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: c3aadcf34e013c66dec81ca4b09dce4144294ac3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228399"
---
# <a name="2-directives"></a>2. Directives

Les directives sont basées sur des `#pragma` directives définies dans les normes C et C++.  Les compilateurs qui prennent en charge l’API C et C++ OpenMP incluent une option de ligne de commande qui active et autorise l’interprétation de toutes les directives de compilateur OpenMP.

## <a name="21-directive-format"></a>format de directive 2,1

La syntaxe d’une directive OpenMP est formellement spécifiée par la grammaire de l' [annexe C](c-openmp-c-and-cpp-grammar.md), et de manière informelle, comme suit :

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Chaque directive commence par `#pragma omp` , afin de réduire le risque de conflit avec d’autres directives pragma (non OpenMP ou d’extensions fournisseur pour OpenMP) portant le même nom. Le reste de la directive suit les conventions des normes C et C++ pour les directives de compilateur. En particulier, les espaces blancs peuvent être utilisés avant et après `#` , et parfois des espaces blancs doivent être utilisés pour séparer les mots dans une directive. Les jetons de prétraitement qui suivent le `#pragma omp` sont soumis au remplacement de macros.

Les directives respectent la casse. L’ordre dans lequel les clauses apparaissent dans les directives n’est pas significatif. Les clauses sur les directives peuvent être répétées selon les besoins, conformément aux restrictions indiquées dans la description de chaque clause. Si *variable-List* apparaît dans une clause, elle doit spécifier uniquement des variables. Un seul *nom de directive* peut être spécifié par directive.  Par exemple, la directive suivante n’est pas autorisée :

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Une directive OpenMP s’applique à au plus une instruction réussie, qui doit être un bloc structuré.

## <a name="22-conditional-compilation"></a>2,2 compilation conditionnelle

Le `_OPENMP` nom de la macro est défini par les implémentations conformes à OpenMP en tant que constante décimale *YYYYMM*, qui est l’année et le mois de la spécification approuvée. Cette macro ne doit pas être l’objet d’une ou d’une `#define` `#undef` directive de prétraitement.

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

- `if(`*scalaire-expression*`)`
- `private(`*liste de variables*`)`
- `firstprivate(`*liste de variables*`)`
- `default(shared | none)`
- `shared(`*liste de variables*`)`
- `copyin(`*liste de variables*`)`
- `reduction(`*opérateur* `:` *liste de variables*  `)`
- `num_threads(`*Integer-expression*`)`

Quand un thread arrive à une construction parallèle, une équipe de threads est créée si l’un des cas suivants est vrai :

- Aucune `if` clause n’est présente.
- L' `if` expression est évaluée à une valeur différente de zéro.

Ce thread devient le thread principal de l’équipe, avec un numéro de thread égal à 0, et tous les threads de l’équipe, y compris le thread principal, exécutent la région en parallèle. Si la valeur de l' `if` expression est égale à zéro, la région est sérialisée.

Pour déterminer le nombre de threads demandés, les règles suivantes sont prises en compte dans l’ordre. La première règle dont la condition est remplie sera appliquée :

1. Si la `num_threads` clause est présente, la valeur de l’expression entière est le nombre de threads demandés.

1. Si la `omp_set_num_threads` fonction de bibliothèque a été appelée, la valeur de l’argument dans l’appel le plus récemment exécuté est le nombre de threads demandés.

1. Si la variable `OMP_NUM_THREADS` d’environnement est définie, la valeur de cette variable d’environnement est le nombre de threads demandés.

1. Si aucune des méthodes ci-dessus n’est utilisée, le nombre de threads demandés est défini par l’implémentation.

Si la `num_threads` clause est présente, elle remplace le nombre de threads demandés par la `omp_set_num_threads` fonction de bibliothèque ou la `OMP_NUM_THREADS` variable d’environnement uniquement pour la région parallèle à laquelle elle est appliquée. Les régions parallèles ultérieures ne sont pas affectées.

Le nombre de threads qui exécutent la région parallèle dépend également de l’activation ou non de l’ajustement dynamique du nombre de threads. Si l’ajustement dynamique est désactivé, le nombre de threads demandé exécutera la région parallèle. Si l’ajustement dynamique est activé, le nombre de threads demandé est le nombre maximal de threads qui peuvent exécuter la région parallèle.

Si une région parallèle est rencontrée alors que l’ajustement dynamique du nombre de threads est désactivé et que le nombre de threads demandés pour la région parallèle est supérieur au nombre que le système d’exécution peut fournir, le comportement du programme est défini par l’implémentation. Une implémentation peut, par exemple, interrompre l’exécution du programme ou sérialiser la région parallèle.

La `omp_set_dynamic` fonction de bibliothèque et la `OMP_DYNAMIC` variable d’environnement peuvent être utilisées pour activer et désactiver l’ajustement dynamique du nombre de threads.

Le nombre de processeurs physiques qui hébergent réellement les threads à un moment donné est défini par l’implémentation. Une fois créé, le nombre de threads dans l’équipe reste constant pour la durée de cette région parallèle. Il peut être modifié de manière explicite par l’utilisateur ou automatiquement par le système d’exécution d’une région parallèle à une autre.

Les instructions contenues dans l’étendue dynamique de la région parallèle sont exécutées par chaque thread, et chaque thread peut exécuter un chemin d’accès d’instructions différent des autres threads. Les directives rencontrées en dehors de l’étendue lexicale d’une région parallèle sont appelées directives orphelines.

Il existe un cloisonnement implicite à la fin d’une région parallèle. Seul le thread principal de l’équipe continue l’exécution à la fin d’une région parallèle.

Si un thread d’une équipe qui exécute une région parallèle rencontre une autre construction parallèle, il crée une nouvelle équipe et il devient le maître de cette nouvelle équipe. Les régions parallèles imbriquées sont sérialisées par défaut. Par conséquent, par défaut, une région parallèle imbriquée est exécutée par une équipe composée d’un thread. Le comportement par défaut peut être modifié à l’aide de la fonction de la bibliothèque Runtime `omp_set_nested` ou de la variable d’environnement `OMP_NESTED` . Toutefois, le nombre de threads dans une équipe qui exécutent une région parallèle imbriquée est défini par l’implémentation.

Les restrictions à la `parallel` directive sont les suivantes :

- Au maximum, une `if` clause peut apparaître sur la directive.

- Il n’est pas spécifié si des effets secondaires à l’intérieur de l’expression ou de l' `num_threads` expression if se produisent.

- Une exécution à `throw` l’intérieur d’une région parallèle doit entraîner la reprise de l’exécution dans l’étendue dynamique du même bloc structuré, et elle doit être interceptée par le thread qui a levé l’exception.

- Une seule `num_threads` clause peut apparaître sur la directive. L' `num_threads` expression est évaluée en dehors du contexte de la région parallèle, et doit correspondre à une valeur entière positive.

- L’ordre d’évaluation des `if` `num_threads` clauses et n’est pas spécifié.

### <a name="cross-references"></a>Références croisées

- `private`clauses,,,, `firstprivate` `default` `shared` `copyin` et `reduction` ([section 2.7.2](#272-data-sharing-attribute-clauses))
- Variable d’environnement [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- fonction de la bibliothèque de [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- Variable d’environnement [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) fonction)
- Variable d’environnement [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- fonction de la bibliothèque de [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)

## <a name="24-work-sharing-constructs"></a>2,4 constructions de partage de travail

Une construction de partage de travail distribue l’exécution de l’instruction associée parmi les membres de l’équipe qui la rencontrent. Les directives de partage de travail ne lancent pas de nouveaux threads, et il n’existe pas de barrière implicite sur l’entrée d’une construction de partage de travail.

La séquence de constructions et de directives de partage de travail `barrier` rencontrées doit être la même pour chaque thread d’une équipe.

OpenMP définit les constructions de partage de travail suivantes, et ces constructions sont décrites dans les sections suivantes :

- [pour](#241-for-construct) la directive
- [sections](#242-sections-construct) (directive)
- directive [unique](#243-single-construct)

### <a name="241-for-construct"></a>2.4.1 pour la construction

La `for` directive identifie une construction de partage de travail itérative qui spécifie que les itérations de la boucle associée seront exécutées en parallèle. Les itérations de la `for` boucle sont réparties entre les threads qui existent déjà dans l’équipe qui exécute la construction parallèle à laquelle elles sont liées. La syntaxe de la `for` construction est la suivante :

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

La clause est l’une des suivantes :

- `private(`*liste de variables*`)`
- `firstprivate(`*liste de variables*`)`
- `lastprivate(`*liste de variables*`)`
- `reduction(`*opérateur* `:` *liste de variables*`)`
- `ordered`
- `schedule(`*genre* [ `,` *chunk_size*]`)`
- `nowait`

La `for` directive place des restrictions sur la structure de la `for` boucle correspondante. Plus précisément, la `for` boucle correspondante doit avoir une forme canonique :

`for (`*init-expr* `;` *var logique-op b* `;` *incr-expr*`)`

*init-expr*<br/>
Celui-ci peut avoir l'une des valeurs suivantes :

- *var*  =  *lb*
- variable de type *entier*  =  *lb*

*incr-expr*<br/>
Celui-ci peut avoir l'une des valeurs suivantes :

- `++`*var*
- *var*`++`
- `--`*var*
- *var*`--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
Variable de type entier signé. Si cette variable serait partagée, elle est implicitement rendue privée pour la durée de `for` . Ne modifiez pas cette variable dans le corps de l' `for` instruction. À moins que la variable ne soit spécifiée `lastprivate` , sa valeur après la boucle est indéterminée.

*opérations logiques*<br/>
Celui-ci peut avoir l'une des valeurs suivantes :

- `<`
- `<=`
- `>`
- `>=`

*lb*, *b*et *incr*<br>
Expressions d’entiers invariants de boucle. Aucune synchronisation n’est effectuée pendant l’évaluation de ces expressions, de sorte que tous les effets secondaires évalués produisent des résultats indéterminés.

La forme canonique permet de calculer le nombre d’itérations de boucle lors de l’entrée dans la boucle. Ce calcul est effectué avec des valeurs dans le type *var*, après les promotions intégrales. En particulier, si la valeur de l’incr. *b* `-` *lb* `+` *incr* ne peut pas être représentée dans ce type, le résultat est indéterminé. En outre, si *Logical-op* est `<` ou `<=` , *incr-expr* doit entraîner l’augmentation de *var* à chaque itération de la boucle.   Si *Logical-op* est `>` ou `>=` , *incr-expr* doit faire en sorte que *var* soit plus petit sur chaque itération de la boucle.

La `schedule` clause spécifie comment les itérations de la `for` boucle sont réparties entre les threads de l’équipe. L’exactitude d’un programme ne doit pas dépendre du thread qui exécute une itération particulière. La valeur de *chunk_size*, si elle est spécifiée, doit être une expression entière d’invariant de boucle avec une valeur positive. Il n’existe aucune synchronisation pendant l’évaluation de cette expression, donc tous les effets secondaires évalués produisent des résultats indéterminés. Le *genre* de planification peut être l’une des valeurs suivantes :

Table 2-1 : `schedule` valeurs de *type* de clause

|||
|-|-|
|statique|Lorsque `schedule(static,` *chunk_size* `)` est spécifié, les itérations sont divisées en segments d’une taille spécifiée par *chunk_size*. Les segments sont attribués de manière statique aux threads de l’équipe en mode tourniquet (Round Robin) dans l’ordre du numéro de thread. Quand aucun *chunk_size* n’est spécifié, l’espace d’itération est divisé en segments dont la taille est approximativement égale, avec un segment affecté à chaque thread.|
|dynamique|Lorsque `schedule(dynamic,` *chunk_size* `)` est spécifié, les itérations sont divisées en une série de segments, chacun contenant *chunk_size* itérations. Chaque segment est assigné à un thread qui attend une attribution. Le thread exécute le segment des itérations, puis attend la prochaine affectation, jusqu’à ce qu’il ne reste aucun segment à assigner. Le dernier segment à affecter peut avoir un plus petit nombre d’itérations. Quand aucun *chunk_size* n’est spécifié, la valeur par défaut est 1.|
|guider|Lorsque `schedule(guided,` *chunk_size* `)` est spécifié, les itérations sont assignées aux threads dans des segments avec des tailles décroissantes. Quand un thread termine son bloc d’itérations affecté, il reçoit dynamiquement un autre bloc, jusqu’à ce qu’il ne reste aucun élément. Pour un *chunk_size* de 1, la taille de chaque segment est approximativement le nombre d’itérations non assignées divisé par le nombre de threads. Ces tailles diminuent presque de façon exponentielle jusqu’à 1. Pour un *chunk_size* avec la valeur *k* supérieure à 1, les tailles diminuent presque de façon exponentielle jusqu’à *k*, sauf que le dernier segment peut avoir moins de *k* itérations. Quand aucun *chunk_size* n’est spécifié, la valeur par défaut est 1.|
|runtime|Lorsque `schedule(runtime)` est spécifié, la décision relative à la planification est différée jusqu’au moment de l’exécution. Le *type* et la taille de la planification des segments peuvent être choisis au moment de l’exécution en définissant la variable d’environnement `OMP_SCHEDULE` . Si cette variable d’environnement n’est pas définie, la planification résultante est définie par l’implémentation. Lorsque `schedule(runtime)` est spécifié, *chunk_size* ne doit pas être spécifié.|

En l’absence d’une clause définie de manière explicite `schedule` , la valeur par défaut `schedule` est définie par l’implémentation.

Un programme conforme à OpenMP ne doit pas reposer sur une planification particulière pour une exécution correcte. Un programme ne doit pas reposer sur un *type* de planification conforme précisément à la description ci-dessus, car il est possible d’avoir des variations dans les implémentations du même *type* de planification entre différents compilateurs. Les descriptions peuvent être utilisées pour sélectionner la planification appropriée à une situation particulière.

La `ordered` clause doit être présente lorsque les `ordered` directives sont liées à la `for` construction.

Il existe un cloisonnement implicite à la fin d’une `for` construction, sauf si une `nowait` clause est spécifiée.

Les restrictions à la `for` directive sont les suivantes :

- La `for` boucle doit être un bloc structuré et, par ailleurs, son exécution ne doit pas être terminée par une **`break`** instruction.

- Les valeurs des expressions de contrôle de boucle de la `for` boucle associée à une `for` directive doivent être les mêmes pour tous les threads de l’équipe.

- La `for` variable d’itération de la boucle doit avoir un type entier signé.

- Une seule `schedule` clause peut apparaître sur une `for` directive.

- Une seule `ordered` clause peut apparaître sur une `for` directive.

- Une seule `nowait` clause peut apparaître sur une `for` directive.

- Il n’est pas spécifié si ou la fréquence à laquelle les effets secondaires dans les expressions *chunk_size*, *lb*, *b*ou *incr* se produisent.

- La valeur de l’expression de *chunk_size* doit être la même pour tous les threads de l’équipe.

#### <a name="cross-references"></a>Références croisées

- `private``firstprivate` `lastprivate` clauses,, et `reduction` ([section 2.7.2](#272-data-sharing-attribute-clauses))
- Variable d’environnement [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)
- construction [ordonnée](#266-ordered-construct)
- clause [Schedule](d-using-the-schedule-clause.md)

### <a name="242-sections-construct"></a>2.4.2 construction de sections

La `sections` directive identifie une construction de partage de travail non itérative qui spécifie un ensemble de constructions qui doivent être réparties parmi les threads d’une équipe. Chaque section est exécutée une seule fois par un thread de l’équipe. La syntaxe de la `sections` directive est la suivante :

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

- `private(`*liste de variables*`)`
- `firstprivate(`*liste de variables*`)`
- `lastprivate(`*liste de variables*`)`
- `reduction(`*opérateur* `:` *liste de variables*  `)`
- `nowait`

Chaque section est précédée d’une `section` directive, bien que la `section` directive soit facultative pour la première section. Les `section` directives doivent apparaître dans l’étendue lexicale de la `sections` directive. Il existe un cloisonnement implicite à la fin d’une `sections` construction, sauf si un `nowait` est spécifié.

Les restrictions à la `sections` directive sont les suivantes :

- Une `section` directive ne doit pas figurer en dehors de l’étendue lexicale de la `sections` directive.

- Une seule `nowait` clause peut apparaître sur une `sections` directive.

#### <a name="cross-references"></a>Références croisées

- `private``firstprivate` `lastprivate` clauses,, et `reduction` ([section 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 construction unique

La `single` directive identifie une construction qui spécifie que le bloc structuré associé est exécuté par un seul thread de l’équipe (pas nécessairement le thread principal). La syntaxe de la `single` directive est la suivante :

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

La clause est l’une des suivantes :

- `private(`*liste de variables*`)`
- `firstprivate(`*liste de variables*`)`
- `copyprivate(`*liste de variables*`)`
- `nowait`

Il existe un cloisonnement implicite après la `single` construction, sauf si une `nowait` clause est spécifiée.

Les restrictions à la `single` directive sont les suivantes :

- Une seule `nowait` clause peut apparaître sur une `single` directive.
- La `copyprivate` clause ne doit pas être utilisée avec la `nowait` clause.

#### <a name="cross-references"></a>Références croisées

- `private``firstprivate` `copyprivate` clauses, et ([section 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2,5 constructions combinées de partage de travail parallèles

Les constructions combinées de partage de travail parallèles sont des raccourcis permettant de spécifier une région parallèle qui n’a qu’une seule construction de partage de travail. La sémantique de ces directives est identique à la spécification explicite d’une `parallel` directive suivie d’une seule construction de partage de travail.

Les sections suivantes décrivent les constructions de partage de travail parallèles combinées :

- [Parallel pour](#251-parallel-for-construct) la directive
- directive de [sections parallèles](#252-parallel-sections-construct)

### <a name="251-parallel-for-construct"></a>2.5.1 construction parallèle for

La `parallel for` directive est un raccourci pour une `parallel` région qui ne contient qu’une seule `for` directive. La syntaxe de la `parallel for` directive est la suivante :

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Cette directive autorise toutes les clauses de la `parallel` directive et de la `for` directive, à l’exception de la `nowait` clause, avec des significations et des restrictions identiques. La sémantique est identique à la spécification explicite d’une `parallel` directive immédiatement suivie d’une `for` directive.

#### <a name="cross-references"></a>Références croisées

- [Parallel](#23-parallel-construct) (directive)
- [pour](#241-for-construct) la directive
- [Clauses d’attribut de données](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>construction de sections parallèles 2.5.2

La `parallel sections` directive fournit un formulaire de raccourci pour spécifier une `parallel` région qui n’a qu’une seule `sections` directive. La sémantique est identique à la spécification explicite d’une `parallel` directive immédiatement suivie d’une `sections` directive. La syntaxe de la `parallel sections` directive est la suivante :

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

La *clause* peut être l’une des clauses acceptées par les `parallel` `sections` directives et, à l’exception de la `nowait` clause.

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

La `master` directive identifie une construction qui spécifie un bloc structuré qui est exécuté par le thread principal de l’équipe. La syntaxe de la `master` directive est la suivante :

```cpp
#pragma omp master new-linestructured-block
```

Les autres threads de l’équipe n’exécutent pas le bloc structuré associé. Il n’existe aucune barrière implicite à l’entrée ou à la sortie de la construction principale.

### <a name="262-critical-construct"></a>construction critique 2.6.2

La `critical` directive identifie une construction qui restreint l’exécution du bloc structuré associé à un thread unique à la fois. La syntaxe de la `critical` directive est la suivante :

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

Un *nom* facultatif peut être utilisé pour identifier la région critique. Les identificateurs utilisés pour identifier une région critique ont une liaison externe et se trouvent dans un espace de noms distinct des espaces de noms utilisés par les étiquettes, les balises, les membres et les identificateurs ordinaires.

Un thread attend au début d’une région critique jusqu’à ce qu’aucun autre thread n’exécute une région critique (n’importe où dans le programme) avec le même nom. Toutes les directives sans nom sont `critical` mappées au même nom non spécifié.

### <a name="263-barrier-directive"></a>directive de cloisonnement 2.6.3

La `barrier` directive synchronise tous les threads d’une équipe. En cas de rencontre, chaque thread de l’équipe attend que tous les autres threads aient atteint ce point. La syntaxe de la `barrier` directive est la suivante :

```cpp
#pragma omp barrier new-line
```

Une fois que tous les threads de l’équipe ont rencontré le cloisonnement, chaque thread de l’équipe commence à exécuter les instructions après la directive de cloisonnement en parallèle. Étant donné que la `barrier` directive n’a pas d’instruction de langage C dans sa syntaxe, il existe des restrictions quant à son emplacement dans un programme. Pour plus d’informations sur la grammaire formelle, consultez l' [annexe C](c-openmp-c-and-cpp-grammar.md). L’exemple ci-dessous illustre ces restrictions.

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

La `atomic` directive garantit qu’un emplacement de mémoire spécifique est mis à jour atomiquement, au lieu de l’exposer à la possibilité de plusieurs threads d’écriture simultanés. La syntaxe de la `atomic` directive est la suivante :

```cpp
#pragma omp atomic new-lineexpression-stmt
```

L’instruction d’expression doit avoir l’une des formes suivantes :

- *binop x* `=` *expr*
- *x*`++`
- `++` *x*
- *x*`--`
- `--` *x*

Dans les expressions précédentes :

- *x* est une expression lvalue avec un type scalaire.

- *expr* est une expression avec un type scalaire et ne fait pas référence à l’objet désigné par *x*.

- *binop* n’est pas un opérateur surchargé et est l’un des opérateurs,,,,,, `+` `*` `-` `/` `&` `^` `|` , `<<` ou `>>` .

Bien qu’elle soit définie par l’implémentation si une implémentation remplace toutes les `atomic` directives par des `critical` directives portant le même *nom*unique, la `atomic` directive permet une meilleure optimisation. Des instructions matérielles sont souvent disponibles pour effectuer la mise à jour atomique avec la surcharge la plus faible.

Seule la charge et le magasin de l’objet désigné par *x* sont atomiques ; l’évaluation de *expr* n’est pas atomique. Pour éviter les conditions de concurrence, toutes les mises à jour de l’emplacement en parallèle doivent être protégées par la `atomic` directive, à l’exception de celles qui sont connues comme étant exemptes de conditions de concurrence.

Les restrictions à la `atomic` directive sont les suivantes :

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

La `flush` directive, qu’elle soit explicite ou implicite, spécifie un point de séquence « inter-threads » auquel l’implémentation est requise pour s’assurer que tous les threads d’une équipe disposent d’une vue cohérente de certains objets (spécifiés ci-dessous) en mémoire. Cela signifie que les évaluations précédentes d’expressions qui font référence à ces objets sont terminées et que les évaluations suivantes n’ont pas encore commencé. Par exemple, les compilateurs doivent restaurer les valeurs des objets des registres vers la mémoire, et le matériel peut avoir besoin de vider les mémoires tampons d’écriture dans la mémoire et de recharger les valeurs des objets à partir de la mémoire.

La syntaxe de la `flush` directive est la suivante :

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Si les objets qui nécessitent une synchronisation peuvent tous être désignés par des variables, ces variables peuvent être spécifiées dans la *liste*de variables facultative. Si un pointeur est présent dans la *liste de variables*, le pointeur lui-même est vidé, et non l’objet auquel le pointeur fait référence.

Une `flush` directive sans *liste de variables* synchronise tous les objets partagés, à l’exception des objets inaccessibles avec une durée de stockage automatique. (Cela peut avoir plus de surcharge qu’un `flush` avec une *liste de variables*.) Une `flush` directive sans *liste de variables* est implicite pour les directives suivantes :

- `barrier`
- À l’entrée et à la sortie de`critical`
- À l’entrée et à la sortie de`ordered`
- À l’entrée et à la sortie de`parallel`
- À la sortie de`for`
- À la sortie de`sections`
- À la sortie de`single`
- À l’entrée et à la sortie de`parallel for`
- À l’entrée et à la sortie de`parallel sections`

La directive n’est pas impliquée si une `nowait` clause est présente. Il convient de noter que la `flush` directive n’est pas implicite pour les éléments suivants :

- À l’entrée à`for`
- À l’entrée ou à la sortie de`master`
- À l’entrée à`sections`
- À l’entrée à`single`

Une référence qui accède à la valeur d’un objet avec un type qualifié volatil se comporte comme s’il existait une `flush` directive spécifiant cet objet au point de séquence précédent. Une référence qui modifie la valeur d’un objet avec un type qualifié volatil se comporte comme s’il existait une `flush` directive spécifiant cet objet au point de séquence suivant.

Étant donné que la `flush` directive n’a pas d’instruction de langage C dans sa syntaxe, il existe des restrictions quant à son emplacement dans un programme. Pour plus d’informations sur la grammaire formelle, consultez l' [annexe C](c-openmp-c-and-cpp-grammar.md). L’exemple ci-dessous illustre ces restrictions.

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

Les restrictions à la `flush` directive sont les suivantes :

- Une variable spécifiée dans une `flush` directive ne doit pas avoir de type référence.

### <a name="266-ordered-construct"></a>construction ordonnée 2.6.6

Le bloc structuré qui suit une `ordered` directive est exécuté dans l’ordre dans lequel les itérations sont exécutées dans une boucle séquentielle. La syntaxe de la `ordered` directive est la suivante :

```cpp
#pragma omp ordered new-linestructured-block
```

Une `ordered` directive doit être dans l’étendue dynamique d’une `for` `parallel for` construction ou. La `for` `parallel for` directive ou à laquelle la `ordered` construction crée une liaison doit avoir une `ordered` clause spécifiée comme décrit dans la [section 2.4.1](#241-for-construct). Dans l’exécution d’une `for` `parallel for` construction ou avec une `ordered` clause, les `ordered` constructions sont exécutées de façon stricte dans l’ordre dans lequel elles seraient exécutées dans une exécution séquentielle de la boucle.

Les restrictions à la `ordered` directive sont les suivantes :

- Une itération d’une boucle avec une `for` construction ne doit pas exécuter la même directive ordonnée plusieurs fois, et elle ne doit pas exécuter plus d’une `ordered` directive.

## <a name="27-data-environment"></a>2,7 environnement de données

Cette section présente une directive et plusieurs clauses pour contrôler l’environnement de données pendant l’exécution des régions parallèles, comme suit :

- Une directive [threadprivate](#271-threadprivate-directive) est fournie pour rendre les variables de portée de fichier, de portée espace de noms ou de portée de bloc statiques locales sur un thread.

- Les clauses qui peuvent être spécifiées dans les directives pour contrôler les attributs de partage de variables pendant la durée des constructions parallèles ou de partage de travail sont décrites dans la [section 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 (directive threadprivate)

La `threadprivate` directive rend la portée de fichier nommée, la portée d’espace de noms ou les variables de portée de bloc statiques spécifiées dans la *liste de variables* privée d’un thread. *variable-List* est une liste séparée par des virgules de variables qui n’ont pas de type incomplet. La syntaxe de la `threadprivate` directive est la suivante :

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Chaque copie d’une `threadprivate` variable est initialisée une seule fois, à un point non spécifié du programme avant la première référence à cette copie, et de manière habituelle (c’est-à-dire que la copie principale est initialisée dans une exécution en série du programme). Notez que si un objet est référencé dans un initialiseur explicite d’une `threadprivate` variable et que la valeur de l’objet est modifiée avant la première référence à une copie de la variable, le comportement n’est pas spécifié.

Comme pour toute variable privée, un thread ne doit pas référencer la copie d’un objet d’un autre thread `threadprivate` . Dans les régions et les régions principales du programme, les références sont représentées par la copie de l’objet du thread principal.

Après l’exécution de la première région parallèle, les données contenues dans les `threadprivate` objets sont conservées uniquement si le mécanisme de threads dynamiques a été désactivé et si le nombre de threads reste inchangé pour toutes les régions parallèles.

Les restrictions de la `threadprivate` directive sont les suivantes :

- Une `threadprivate` directive pour une portée de fichier ou des variables de portée espace de noms doit apparaître en dehors de toute définition ou déclaration, et doit précéder lexicalement toutes les références aux variables de sa liste.

- Chaque variable de la *liste variable* d’une `threadprivate` directive au niveau de la portée de fichier ou d’espace de noms doit faire référence à une déclaration de variable au niveau de la portée de fichier ou d’espace de noms qui précède lexicalement la directive.

- Une `threadprivate` directive pour les variables de portée de bloc statiques doit apparaître dans l’étendue de la variable et non dans une portée imbriquée. La directive doit précéder lexicalement toutes les références aux variables de sa liste.

- Chaque variable de la *liste de variables* d’une `threadprivate` directive dans la portée de bloc doit faire référence à une déclaration de variable dans la même portée qui précède lexicalement la directive. La déclaration de variable doit utiliser le spécificateur de classe de stockage statique.

- Si une variable est spécifiée dans une `threadprivate` directive dans une unité de traduction, elle doit être spécifiée dans une `threadprivate` directive dans chaque unité de traduction dans laquelle elle est déclarée.

- Une `threadprivate` variable ne doit pas apparaître dans une clause, à l’exception de la `copyin` `copyprivate` clause,,, `schedule` `num_threads` ou `if` .

- L’adresse d’une `threadprivate` variable n’est pas une constante d’adresse.

- Une `threadprivate` variable ne doit pas avoir un type incomplet ou un type référence.

- Une `threadprivate` variable avec un type de classe non Pod doit avoir un constructeur de copie accessible et non ambigu s’il est déclaré avec un initialiseur explicite.

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

Si une variable est visible lorsqu’une construction de partage de travail ou parallèle est rencontrée et que la variable n’est pas spécifiée dans une clause ou une directive d’attribut de partage `threadprivate` , la variable est partagée. Les variables statiques déclarées dans l’étendue dynamique d’une région parallèle sont partagées. La mémoire allouée au tas (par exemple, à l’aide `malloc()` de en C ou c++ ou **`new`** de l’opérateur en c++) est partagée. (Toutefois, le pointeur vers cette mémoire peut être privé ou partagé.) Les variables avec une durée de stockage automatique déclarée dans l’étendue dynamique d’une région parallèle sont privées.

La plupart des clauses acceptent un argument de *liste* de variables, qui est une liste séparée par des virgules de variables qui sont visibles. Si une variable référencée dans une clause d’attribut de partage de données a un type dérivé d’un modèle et qu’il n’existe aucune autre référence à cette variable dans le programme, le comportement n’est pas défini.

Toutes les variables qui apparaissent dans les clauses de directive doivent être visibles. Les clauses peuvent être répétées en fonction des besoins, mais aucune variable ne peut être spécifiée dans plusieurs clauses, à la différence qu’une variable peut être spécifiée dans une `firstprivate` clause et une `lastprivate` clause.

Les sections suivantes décrivent les clauses d’attributs de partage de données :

- [priv](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [partagé](#2724-shared)
- [valeurs](#2725-default)
- [applicables](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

La `private` clause déclare que les variables de la liste de variables doivent être privées pour chaque thread d’une équipe. La syntaxe de la `private` clause est la suivante :

```cpp
private(variable-list)
```

Le comportement d’une variable spécifiée dans une `private` clause est le suivant. Un nouvel objet avec une durée de stockage automatique est alloué pour la construction. La taille et l’alignement du nouvel objet sont déterminés par le type de la variable. Cette allocation se produit une fois pour chaque thread de l’équipe, et un constructeur par défaut est appelé pour un objet de classe, si nécessaire ; dans le cas contraire, la valeur initiale est indéterminée.  L’objet d’origine référencé par la variable a une valeur indéterminée au moment de l’entrée dans la construction, ne doit pas être modifié dans l’étendue dynamique de la construction et a une valeur indéterminée à la sortie de la construction.

Dans l’étendue lexicale de la construction de directive, la variable fait référence au nouvel objet privé alloué par le thread.

Les restrictions de la `private` clause sont les suivantes :

- Une variable avec un type de classe spécifié dans une `private` clause doit avoir un constructeur par défaut accessible et non ambigu.

- Une variable spécifiée dans une `private` clause ne doit pas avoir un **`const`** type qualifié, sauf si elle a un type de classe avec un `mutable` membre.

- Une variable spécifiée dans une `private` clause ne doit pas avoir un type incomplet ou un type référence.

- Les variables qui apparaissent dans la `reduction` clause d’une `parallel` directive ne peuvent pas être spécifiées dans une `private` clause d’une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

La `firstprivate` clause fournit un sur-ensemble des fonctionnalités fournies par la `private` clause. La syntaxe de la `firstprivate` clause est la suivante :

```cpp
firstprivate(variable-list)
```

Les variables spécifiées dans la *liste de variables ont une* sémantique de `private` clause, comme décrit dans la [section 2.7.2.1](#2721-private). L’initialisation ou la construction se produit comme si elle était effectuée une fois par thread, avant l’exécution du thread de la construction. Pour une `firstprivate` clause sur une construction parallèle, la valeur initiale du nouvel objet privé est la valeur de l’objet d’origine qui existe immédiatement avant la construction parallèle pour le thread qui l’a rencontré. Pour une `firstprivate` clause sur une construction de partage de travail, la valeur initiale du nouvel objet privé pour chaque thread qui exécute la construction de partage de travail est la valeur de l’objet d’origine qui existe avant le moment où le même thread rencontre la construction de partage de travail. En outre, pour les objets C++, le nouvel objet privé pour chaque thread est construit par copie à partir de l’objet d’origine.

Les restrictions de la `firstprivate` clause sont les suivantes :

- Une variable spécifiée dans une `firstprivate` clause ne doit pas avoir un type incomplet ou un type référence.

- Une variable avec un type de classe spécifié comme `firstprivate` doit avoir un constructeur de copie accessible et non ambigu.

- Les variables privées dans une région parallèle ou qui apparaissent dans la `reduction` clause d’une `parallel` directive ne peuvent pas être spécifiées dans une `firstprivate` clause d’une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

La `lastprivate` clause fournit un sur-ensemble des fonctionnalités fournies par la `private` clause. La syntaxe de la `lastprivate` clause est la suivante :

```cpp
lastprivate(variable-list)
```

Les variables spécifiées dans la liste de variables ont *une sémantique de* `private` clause. Lorsqu’une `lastprivate` clause apparaît sur la directive qui identifie une construction de partage de travail, la valeur de chaque `lastprivate` variable de la dernière itération de la boucle associée, ou la directive lexicale de la dernière section, est assignée à l’objet d’origine de la variable. Les variables qui n’ont pas de valeur assignée par la dernière itération du `for` ou `parallel for` , ou par la dernière section lexicale de la `sections` `parallel sections` directive ou, ont des valeurs indéterminées après la construction. Les sous-objets non assignés ont également une valeur indéterminée après la construction.

Les restrictions de la `lastprivate` clause sont les suivantes :

- Toutes les restrictions pour `private` apply.

- Une variable avec un type de classe spécifié comme `lastprivate` doit avoir un opérateur d’assignation de copie accessible et non ambigu.

- Les variables privées dans une région parallèle ou qui apparaissent dans la `reduction` clause d’une `parallel` directive ne peuvent pas être spécifiées dans une `lastprivate` clause d’une directive de partage de travail qui est liée à la construction parallèle.

#### <a name="2724-shared"></a>2.7.2.4 shared

Cette clause partage les variables qui s’affichent dans la *liste variable* parmi tous les threads d’une équipe. Tous les threads d’une équipe accèdent à la même zone de stockage pour les `shared` variables.

La syntaxe de la `shared` clause est la suivante :

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

La `default` clause permet à l’utilisateur d’affecter les attributs de partage de données des variables. La syntaxe de la `default` clause est la suivante :

```cpp
default(shared | none)
```

La spécification de équivaut `default(shared)` à répertorier explicitement chaque variable actuellement visible dans une `shared` clause, sauf si elle est `threadprivate` ou est **`const`** qualifiée. En l’absence de clause explicite `default` , le comportement par défaut est le même que si `default(shared)` a été spécifié.

La spécification de `default(none)` requiert qu’au moins une des conditions suivantes soit vraie pour chaque référence à une variable dans l’étendue lexicale de la construction parallèle :

- La variable est explicitement listée dans une clause d’attribut de partage de données d’une construction qui contient la référence.

- La variable est déclarée dans la construction parallèle.

- La variable est `threadprivate` .

- La variable a un **`const`** type qualifié.

- La variable est la variable de contrôle de boucle pour une `for` boucle qui suit immédiatement une `for` `parallel for` directive ou, et la référence à la variable apparaît à l’intérieur de la boucle.

La spécification d’une variable sur une `firstprivate` `lastprivate` clause, ou `reduction` d’une directive entourée provoque une référence implicite à la variable dans le contexte englobant. Ces références implicites sont également soumises aux exigences répertoriées ci-dessus.

Une seule `default` clause peut être spécifiée sur une `parallel` directive.

L’attribut de partage de données par défaut d’une variable peut être substitué à l’aide des `private` `firstprivate` clauses,, `lastprivate` , `reduction` et `shared` , comme illustré dans l’exemple suivant :

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

Cette clause effectue une réduction sur les variables scalaires qui apparaissent dans la *liste de variables*, avec l’opérateur *op*. La syntaxe de la `reduction` clause est la suivante :

`reduction(`*opération* `:` *liste de variables*`)`

Une réduction est généralement spécifiée pour une instruction de l’une des façons suivantes :

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* (sauf en cas de soustraction)
- *x*`++`
- `++` *x*
- *x*`--`
- `--` *x*

où :

*x*<br/>
Une des variables de réduction spécifiées dans la liste.

*liste de variables*<br/>
Liste séparée par des virgules de variables de réduction scalaires.

*Expr*<br/>
Expression avec un type scalaire qui ne fait pas référence à *x*.

*opérationnel*<br/>
N’est pas un opérateur surchargé, mais un de,,,,,, `+` `*` `-` `&` `^` `|` `&&` ou `||` .

*binop*<br/>
N’est pas un opérateur surchargé, mais un de,,,, `+` `*` `-` `&` `^` ou `|` .

Voici un exemple de la `reduction` clause :

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Comme indiqué dans l’exemple, un opérateur peut être masqué dans un appel de fonction. L’utilisateur doit veiller à ce que l’opérateur spécifié dans la `reduction` clause corresponde à l’opération de réduction.

Bien que l’opérande droit de l' `||` opérateur n’ait aucun effet secondaire dans cet exemple, il est autorisé, mais doit être utilisé avec précaution. Dans ce contexte, un effet secondaire garanti ne pas se produire pendant l’exécution séquentielle de la boucle peut se produire pendant une exécution parallèle. Cette différence peut se produire parce que l’ordre d’exécution des itérations est indéterminé.

L’opérateur est utilisé pour déterminer la valeur initiale de toutes les variables privées utilisées par le compilateur pour la réduction et pour déterminer l’opérateur de finalisation. La spécification explicite de l’opérateur permet à l’instruction de réduction de se trouver en dehors de l’étendue lexicale de la construction. N’importe quel nombre de `reduction` clauses peut être spécifié sur la directive, mais une variable peut apparaître dans au plus une `reduction` clause pour cette directive.

Une copie privée de chaque variable de la *liste de variables* est créée, une pour chaque thread, comme si la `private` clause avait été utilisée. La copie privée est initialisée en fonction de l’opérateur (consultez le tableau suivant).

À la fin de la région pour laquelle la `reduction` clause a été spécifiée, l’objet d’origine est mis à jour pour refléter le résultat de la combinaison de sa valeur d’origine avec la valeur finale de chacune des copies privées à l’aide de l’opérateur spécifié. Les opérateurs de réduction sont tous associatifs (à l’exception de la soustraction) et le compilateur peut réassocier librement le calcul de la valeur finale. (Les résultats partiels d’une réduction de soustraction sont ajoutés pour former la valeur finale.)

La valeur de l’objet d’origine devient indéterminée lorsque le premier thread atteint la clause conteneur et reste tant que le calcul de la réduction n’est pas terminé.  Normalement, le calcul sera terminé à la fin de la construction ; Toutefois, si la `reduction` clause est utilisée sur une construction à laquelle `nowait` est également appliqué, la valeur de l’objet d’origine reste indéterminée jusqu’à ce qu’une synchronisation de cloisonnement ait été effectuée pour s’assurer que tous les threads ont terminé la `reduction` clause.

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

Les restrictions de la `reduction` clause sont les suivantes :

- Le type des variables dans la `reduction` clause doit être valide pour l’opérateur de réduction, sauf que les types pointeur et les types référence ne sont jamais autorisés.

- Une variable spécifiée dans la `reduction` clause ne doit pas être **`const`** qualifiée.

- Les variables privées dans une région parallèle ou qui apparaissent dans la `reduction` clause d’une `parallel` directive ne peuvent pas être spécifiées dans une `reduction` clause d’une directive de partage de travail qui est liée à la construction parallèle.

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

La `copyin` clause fournit un mécanisme permettant d’assigner la même valeur aux `threadprivate` variables pour chaque thread de l’équipe qui exécute la région parallèle. Pour chaque variable spécifiée dans une `copyin` clause, la valeur de la variable dans le thread principal de l’équipe est copiée, comme dans le cas d’une assignation, aux copies thread-Private au début de la région parallèle. La syntaxe de la `copyin` clause est la suivante :

```cpp

copyin(
variable-list
)
```

Les restrictions de la `copyin` clause sont les suivantes :

- Une variable spécifiée dans la `copyin` clause doit avoir un opérateur d’assignation de copie accessible et non ambigu.

- Une variable spécifiée dans la `copyin` clause doit être une `threadprivate` variable.

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

La `copyprivate` clause fournit un mécanisme permettant d’utiliser une variable privée pour diffuser une valeur d’un membre d’une équipe vers les autres membres. C’est une alternative à l’utilisation d’une variable partagée pour la valeur lors de la fourniture d’une telle variable partagée serait difficile (par exemple, dans une récurrence nécessitant une variable différente à chaque niveau). La `copyprivate` clause ne peut apparaître que dans la `single` directive.

La syntaxe de la `copyprivate` clause est la suivante :

```cpp

copyprivate(
variable-list
)
```

L’effet de la `copyprivate` clause sur les variables dans sa liste de variables se produit après l’exécution du bloc structuré associé à la `single` construction, et avant que les threads de l’équipe aient quitté le cloisonnement à la fin de la construction. Ensuite, dans tous les autres threads de l’équipe, pour chaque variable de la *liste variable*, cette variable devient définie (comme dans le cas d’une assignation) avec la valeur de la variable correspondante dans le thread qui a exécuté le bloc structuré de la construction.

Les restrictions à la `copyprivate` clause sont les suivantes :

- Une variable spécifiée dans la `copyprivate` clause ne doit pas apparaître dans une `private` clause ou `firstprivate` pour la même `single` directive.

- Si une `single` directive avec une `copyprivate` clause est rencontrée dans l’étendue dynamique d’une région parallèle, toutes les variables spécifiées dans la `copyprivate` clause doivent être privées dans le contexte englobant.

- Une variable spécifiée dans la `copyprivate` clause doit avoir un opérateur d’assignation de copie non ambigu accessible.

## <a name="28-directive-binding"></a>2,8 liaison de directive

La liaison dynamique des directives doit respecter les règles suivantes :

- Les `for` directives,, `sections` `single` , et sont `master` `barrier` liées à la liaison dynamique, le `parallel` cas échéant, indépendamment de la valeur de toute `if` clause qui peut être présente dans cette directive. Si aucune région parallèle n’est en cours d’exécution, les directives sont exécutées par une équipe composée uniquement du thread principal.

- La `ordered` directive est liée à l’englobement dynamique `for` .

- La `atomic` directive applique un accès exclusif en ce qui concerne `atomic` les directives dans tous les threads, pas seulement l’équipe actuelle.

- La `critical` directive applique un accès exclusif en ce qui concerne `critical` les directives dans tous les threads, pas seulement l’équipe actuelle.

- Une directive ne peut jamais être liée à une directive à l’extérieur du englobant dynamique le plus proche `parallel` .

## <a name="29-directive-nesting"></a>2,9 imbrication de directives

L’imbrication dynamique de directives doit respecter les règles suivantes :

- Une `parallel` directive dynamiquement à l’intérieur d’une autre `parallel` définit logiquement une nouvelle équipe, composée uniquement du thread actuel, à moins que le parallélisme imbriqué soit activé.

- `for``sections` `single` les directives, et qui se lient à la même `parallel` ne peuvent pas être imbriquées les unes dans les autres.

- `critical`les directives portant le même nom ne peuvent pas être imbriquées les unes dans les autres. Notez que cette restriction n’est pas suffisante pour empêcher l’interblocage.

- `for`les `sections` directives, et `single` ne sont pas autorisées dans l’étendue dynamique des `critical` `ordered` régions, et `master` si les directives sont liées au même `parallel` que les régions.

- `barrier`les directives ne sont pas autorisées dans l’étendue dynamique des régions,,,, `for` `ordered` `sections` `single` `master` et `critical` si les directives sont liées au même `parallel` que les régions.

- `master`les directives ne sont pas autorisées dans l’étendue dynamique des `for` `sections` directives, et `single` si les `master` directives sont liées au même `parallel` que les directives de partage de travail.

- `ordered`les directives ne sont pas autorisées dans l’étendue dynamique des `critical` régions si les directives sont liées au même `parallel` que les régions.

- Toute directive autorisée lorsqu’elle est exécutée dynamiquement à l’intérieur d’une région parallèle est également autorisée lorsqu’elle est exécutée en dehors d’une région parallèle. Lorsqu’elle est exécutée dynamiquement en dehors d’une région parallèle spécifiée par l’utilisateur, la directive est exécutée par une équipe composée uniquement du thread principal.
