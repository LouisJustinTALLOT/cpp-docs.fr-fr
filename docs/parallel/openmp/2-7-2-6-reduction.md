---
title: 2.7.2.6 reduction
ms.date: 11/04/2016
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
ms.openlocfilehash: 54b326feb4e4ccf1f1da5c8152ffc8d1e4bd13b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456015"
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

Cette clause effectue une réduction sur les variables scalaires qui s’affichent dans *variable-list*, avec l’opérateur *op*. La syntaxe de la `reduction` clause se présente comme suit :

> réduction (*op*: *variable-list*)

Une réduction est généralement spécifiée pour une instruction avec l’une des formes suivantes :

> *x* = *x* *op* *expr*
> *x* *binop* = *expr*
> *x* = *expr* *op* *x* (sauf pour une soustraction) *x*++
> ++*x*
> *x*--
> --*x*

où :

*x*<br/>
Une des variables de réduction spécifiés dans le `list`.

*liste de variable*<br/>
Une liste séparée par des virgules des variables de réduction scalaire.

*expr*<br/>
Une expression avec un type scalaire qui ne référence pas *x*.

*Op*<br/>
Pas un opérateur surchargé, mais un des +, &#42;, -, &amp;, ^, &#124;, &amp; &amp;, ou &#124; &#124;.

*binop*<br/>
Pas un opérateur surchargé, mais un des +, &#42;, -, &amp;, ^, ou &#124;.

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

Bien que l’opérande de droite de la &#124; &#124; opérateur n’a pas d’effets dans cet exemple, ils sont autorisés, mais doivent être utilisées avec précaution. Dans ce contexte, un effet secondaire qui ne peut ne pas se produisent pendant l’exécution séquentielle de la boucle peut se produire pendant l’exécution en parallèle. Cette différence peut se produire, car l’ordre d’exécution des itérations est indéterminé.

L’opérateur est utilisé pour déterminer la valeur initiale de toutes les variables privées utilisé par le compilateur pour réduire et pour déterminer l’opérateur de la finalisation. Spécification explicite de l’opérateur permet de se trouver en dehors de l’étendue lexicale de la construction de l’instruction de réduction. Un nombre quelconque de `reduction` clauses peuvent être spécifiés dans la directive, mais une variable peut apparaître dans un `reduction` clause pour cette directive.

Une copie privée de chaque variable dans *variable-list* est créé, un pour chaque thread, comme si le `private` clause avait été utilisée. La copie privée est initialisée en fonction de l’opérateur (voir le tableau suivant).

À la fin de la région pour laquelle le `reduction` clause a été spécifiée, l’objet d’origine est mis à jour pour refléter le résultat de la combinaison de sa valeur d’origine avec la valeur finale de chacun des copies privées à l’aide de l’opérateur spécifié. Les opérateurs de réduction sont associatifs tout (à l’exception de la soustraction), et le compilateur peut réassocier librement le calcul de la valeur finale. (Les résultats partiels d’une réduction de la soustraction sont ajoutés pour former la valeur finale).

La valeur de l’objet d’origine devient indéterminée lorsque le premier thread atteint la clause de conteneur et qu’il reste ainsi jusqu'à ce que le calcul de réduction est terminé.  En règle générale, le calcul se termine à la fin de la construction ; Toutefois, si le `reduction` clause est utilisée dans une construction à laquelle `nowait` est également appliqué, la valeur de l’objet d’origine reste indéterminée jusqu'à ce qu’une synchronisation de la barrière a été effectuée pour vous assurer que tous les threads ont terminé la `reduction`clause.

Le tableau suivant répertorie les opérateurs qui ne sont valides et leurs valeurs d’initialisation canonique. La valeur de l’initialisation réelle sera cohérente avec le type de données de la variable de réduction.

|Opérateur|Initialisation|
|--------------|--------------------|
|+|0|
|&#42;|1|
|-|0|
|&amp;|~0|
|&#124;|0|
|^|0|
|&amp;&amp;|1|
|&#124;&#124;|0|

Les restrictions à le `reduction` clause sont les suivantes :

- Le type des variables dans le `reduction` clause doit être valide pour l’opérateur de réduction, à ceci près que les types pointeur et les types référence ne sont jamais autorisées.

- Une variable qui est spécifiée dans le `reduction` clause ne doit pas être **const**-qualifié.

- Variables qui sont privés au sein d’une région parallèle ou qui apparaissent dans le `reduction` clause d’une **parallèles** directive ne peut pas être spécifiée dans un `reduction` clause sur une directive de partage de travail qui est liée à la construction parallèle.

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
