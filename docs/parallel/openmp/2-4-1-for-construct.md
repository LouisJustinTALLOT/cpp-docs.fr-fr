---
title: 2.4.1 construction for | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 27d2cbce-786b-4819-91d3-d55b2cc57a5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac142c628f3c2bef0bc29a2ffd50df8a9efda400
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216535"
---
# <a name="241-for-construct"></a>2.4.1 Construction for

Le **pour** directive identifie une construction de partage de travail itérative qui spécifie que les itérations de la boucle associée seront exécutées en parallèle. Les itérations de la **pour** boucle sont réparties entre les threads qui existent déjà dans l’équipe de l’exécution de la construction parallèle auquel elle est liée. La syntaxe de la **pour** construction se présente comme suit :

```
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

La clause est une des opérations suivantes :

**privé (** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**lastprivate (** *variable-list* **)**

**réduction (** *opérateur* **:** *variable-list* **)**

**Commandée**

**planification (** *type* [**,** *chunk_size*] **)**

**nowait**

Le **pour** directive impose des restrictions sur la structure correspondante **pour** boucle. Plus précisément, correspondants **pour** boucle doit avoir la forme canonique :

**pour (** *init-expr* **;** *var logique op b*; *incr-expr* **)**

*Init-expr*<br/>
Une des valeurs suivantes :

*var* = *lb*

*type entier var* = *lb*

*incr-expr*<br/>
Une des valeurs suivantes :

++ *var*

*var* ++

-- *var*

*var* --

*var* += *incr*

*var* -= *incr*

*var* = *var* + *incr*

*var* = *incr* + *var*

*var* = *var* - *incr*

*var*<br/>
Une variable d’entier signé. Si cette variable serait partagée dans le cas contraire, il est implicitement rendu privé pour la durée de la **pour**.   Cette variable ne doit pas être modifiée dans le corps de la **pour** instruction. Sauf si la variable est spécifiée **lastprivate**, sa valeur après la boucle est indéterminée.

*opération logique*<br/>
Une des valeurs suivantes :

<

\<=

>

\>=

*lb*, *b*, et *incr*<br>
Expressions d’entier invariant une boucle. Il n’existe aucune synchronisation lors de l’évaluation de ces expressions. Par conséquent, tous les effets évaluées produire des résultats indéterminés.

Notez que la forme canonique permet le nombre d’itérations de boucle à calculer sur ENTRÉE pour la boucle. Ce calcul est effectué avec des valeurs dans le type de *var*, après les promotions intégrales. En particulier, si la valeur de *b* - *lb* + *incr* ne peut pas être représentée dans la mesure où le type, le résultat est indéterminé. Plus, si *logique op* est < ou \<= puis *incr-expr* doit entraîner la production *var* à augmenter à chaque itération de la boucle.   Si *logique op* est > ou > = puis *incr-expr* doit entraîner la production *var* à diminuer à chaque itération de la boucle.

Le **planification** clause spécifie comment les itérations de la **pour** boucle sont réparties entre les threads de l’équipe. L’exactitude d’un programme ne doit pas dépendre de thread qui exécute une itération particulière. La valeur de *chunk_size*, si spécifiée, doit être une expression d’entier invariant boucle avec une valeur positive. Il n’existe aucune synchronisation lors de l’évaluation de cette expression. Par conséquent, tous les effets évaluées produire des résultats indéterminés. La planification *type* peut prendre l’une des opérations suivantes :

TABLEAU 2-1 **planification** clause *type* valeurs

|||
|-|-|
|statique|Lorsque **planification (statique,** *chunk_size* **)** est spécifié, les itérations sont divisées en segments d’une taille spécifiée par *chunk_size*. Les segments sont affectées de manière statique les threads dans l’équipe de manière tourniquet (round-robin) dans l’ordre le numéro de thread. En cas de non *chunk_size* est spécifié, l’espace d’itération est divisé en blocs qui sont approximativement égales en taille, avec un segment unique attribué à chaque thread.|
|dynamic|Lorsque **planification (dynamique,** *chunk_size* **)** est spécifié, les itérations sont divisées en une série de blocs, chacun contenant *chunk_size* itérations. Chaque segment est affecté à un thread est en attente d’une affectation. Le thread s’exécute le bloc d’itérations et puis attend son affectation suivante, jusqu'à ce qu’aucun bloc ne reste à affecter. Notez que le dernier segment doit être assignée peut-être avoir un plus petit nombre d’itérations. En cas de non *chunk_size* est spécifié, la valeur par défaut est 1.|
|guidée|Lorsque **planification (guidée,** *chunk_size* **)** est spécifié, les itérations sont associées aux threads en blocs avec la réduction des tailles. Lorsqu’un thread termine son segment attribué d’itérations, elle est affectée dynamiquement un autre segment, jusqu'à ce que ne reste aucun. Pour un *chunk_size* 1, la taille de chaque segment est approximativement le nombre d’itérations non attribués divisé par le nombre de threads. Ces tailles diminuent environ exponentielle à 1. Pour un *chunk_size* avec la valeur *k* supérieure à 1, les tailles de diminuer environ exponentielle à *k*, sauf que le dernier segment peut avoir moins de  *k* itérations. En cas de non *chunk_size* est spécifié, la valeur par défaut est 1.|
|runtime|Lorsque **Schedule (Runtime)** est spécifié, la décision en matière de planification est différée jusqu'à l’exécution. La planification *type* et taille des segments peut être choisi au moment de l’exécution en définissant la variable d’environnement **OMP_SCHEDULE**. Si cette variable d’environnement n’est pas définie, la planification qui en résulte est défini par l’implémentation. Lorsque **Schedule (Runtime)** est spécifié, *chunk_size* ne doit pas être spécifié.|

En l’absence de défini explicitement **planification** clause, la valeur par défaut **planification** est défini par l’implémentation.

Un programme OpenMP conformes ne doit pas dépendre d’une planification particulière pour l’exécution correcte. Un programme ne doit pas compter sur une planification *type* correspondant précisément à la description ci-dessus, car il est possible d’avoir des variations dans les implémentations de la même planification *type* sur différents compilateurs. Les descriptions peuvent être utilisées pour sélectionner la planification qui convient à une situation particulière.

Le **classés** clause doit être présent lorsque **classés** directives lier à la **pour** construire.

Il existe une barrière implicite à la fin d’un **pour** construire, sauf si un **nowait** clause est spécifiée.

Restrictions pour le **pour** directive sont les suivantes :

-   Le **pour** boucle doit être un bloc structuré et, en outre, son exécution ne doit pas se terminer par un **saut** instruction.

-   Les valeurs de la boucle contrôlent les expressions de la **pour** boucle associé à un **pour** directive doit être le même pour tous les threads dans l’équipe.

-   Le **pour** variable d’itération de boucle doit avoir un type entier signé.

-   Un seul **planification** clause peut apparaître sur un **pour** la directive.

-   Un seul **classés** clause peut apparaître sur un **pour** la directive.

-   Un seul **nowait** clause peut apparaître sur un **pour** la directive.

-   Il s’agit if non spécifiée ou la fréquence à laquelle des effets dans n’importe quel côté le *chunk_size*, *lb*, *b*, ou *incr* expressions se produisent.

-   La valeur de la *chunk_size* expression doit être identiques pour tous les threads dans l’équipe.

## <a name="cross-references"></a>Références externes :

-   **privé**, **firstprivate**, **lastprivate**, et **réduction** clauses, consultez [Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.

-   **OMP_SCHEDULE** voir variable d’environnement [Section 4.1](../../parallel/openmp/4-1-omp-schedule.md) page 48.

-   **classés** construire, consultez [Section 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) à la page 22.

-   [Annexe D](../../parallel/openmp/d-using-the-schedule-clause.md), page 93, donne plus d’informations sur l’utilisation de la clause schedule.