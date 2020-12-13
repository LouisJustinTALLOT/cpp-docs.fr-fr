---
description: 'En savoir plus sur : D. La clause Schedule'
title: D. Clause schedule
ms.date: 01/22/2019
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
ms.openlocfilehash: bd1bb4f9a6c661205e2e647fc9e45d81903008c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342489"
---
# <a name="d-the-schedule-clause"></a>D. Clause schedule

Une région parallèle a au moins une barrière, à sa fin, et peut avoir des barrières supplémentaires dans celle-ci. À chaque cloisonnement, les autres membres de l’équipe doivent attendre l’arrivée du dernier thread. Pour réduire ce temps d’attente, le travail partagé doit être distribué afin que tous les threads arrivent à la barrière à la même heure. Si une partie de ce travail partagé est contenue dans des `for` constructions, la `schedule` clause peut être utilisée à cet effet.

Lorsqu’il existe des références répétées aux mêmes objets, le choix de la planification d’une `for` construction peut être déterminé principalement par les caractéristiques du système de mémoire, telles que la présence et la taille des caches et si les temps d’accès à la mémoire sont uniformes ou non uniformes. Ces considérations peuvent rendre préférable que chaque thread fasse systématiquement référence au même ensemble d’éléments d’un tableau dans une série de boucles, même si certains threads sont affectés relativement moins de travail dans certaines boucles. Cette configuration peut être effectuée à l’aide de la `static` planification avec les mêmes limites pour toutes les boucles. Dans l’exemple suivant, la valeur zéro est utilisée comme limite inférieure dans la deuxième boucle, même si `k` elle serait plus naturelle si la planification n’était pas importante.

```cpp
#pragma omp parallel
{
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    a[i] = work1(i);
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    if(i>=k) a[i] += work2(i);
}
```

Dans les exemples restants, il est supposé que l’accès à la mémoire n’est pas la préoccupation dominante. Sauf indication contraire, tous les threads reçoivent des ressources de calcul comparables. Dans ce cas, le choix de la planification d’une `for` construction dépend de l’ensemble du travail partagé qui doit être effectué entre le cloisonnement précédent le plus proche et le cloisonnement de clôture implicite ou le cloisonnement à venir le plus proche, s’il y a une `nowait` clause. Pour chaque type de planification, un exemple bref montre comment ce genre de planification est susceptible d’être le meilleur choix. Une brève discussion suit chaque exemple.

La `static` planification est également appropriée pour le cas le plus simple, une région parallèle contenant une seule `for` construction, chaque itération nécessitant la même quantité de travail.

```cpp
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

La `static` planification est caractérisée par les propriétés que chaque thread obtient approximativement le même nombre d’itérations qu’un autre thread, et chaque thread peut déterminer indépendamment les itérations qui lui sont assignées. Par conséquent, aucune synchronisation n’est requise pour distribuer le travail, et, en supposant que chaque itération requiert la même quantité de travail, tous les threads doivent se terminer à peu de temps.

Pour une équipe de threads *p* , laissez le *plafond (n/p)* être l’entier *q*, qui correspond à *n = p \* q-r* avec *0 <= r < p*. Une implémentation de la `static` planification de cet exemple assignerait des itérations *q* aux premiers threads *p-1* et des itérations *q-r* au dernier thread.  Une autre implémentation acceptable assignerait des itérations *q* aux premiers threads *p-r* , et des itérations *q-1* aux autres threads *r* . Cet exemple illustre la raison pour laquelle un programme ne doit pas reposer sur les détails d’une implémentation particulière.

La `dynamic` planification est appropriée pour le cas d’une `for` construction avec les itérations nécessitant des volumes de travail variables, voire imprévisibles.

```cpp
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

La `dynamic` planification est caractérisée par la propriété selon laquelle aucun thread n’attend au cloisonnement pendant plus longtemps qu’il n’utilise un autre thread pour exécuter sa dernière itération. Cette exigence signifie que les itérations doivent être assignées une à la fois aux threads lorsqu’elles sont disponibles, avec la synchronisation pour chaque affectation. La surcharge de synchronisation peut être réduite en spécifiant une taille de segment minimale de *k* supérieure à 1, de sorte que les threads reçoivent une *k* à la fois jusqu’à ce qu’il reste moins de *k* . Cela garantit qu’aucun thread n’attend à la barrière plus longtemps qu’il n’utilise un autre thread pour exécuter son dernier bloc de *k* itérations.

La `dynamic` planification peut être utile si les threads reçoivent des ressources de calcul variables, ce qui a pratiquement le même effet que des quantités variables de travail pour chaque itération. De même, la planification dynamique peut également être utile si les threads arrivent à la `for` construction à des moments différents, mais dans certains cas, la `guided` planification peut être préférable.

La `guided` planification est appropriée pour le cas dans lequel les threads peuvent arriver à des moments différents dans une `for` construction avec chaque itération nécessitant la même quantité de travail. Cette situation peut se produire si, par exemple, la `for` construction est précédée d’une ou de plusieurs sections ou `for` constructions avec des `nowait` clauses.

```cpp
#pragma omp parallel
{
  #pragma omp sections nowait
  {
    // ...
  }
  #pragma omp for schedule(guided)
  for(i=0; i<n; i++) {
    invariant_amount_of_work(i);
  }
}
```

À l’instar de `dynamic` , la `guided` planification garantit qu’aucun thread n’attend à la barrière plus longtemps qu’il n’utilise un autre thread pour  exécuter son itération finale, ou des itérations finales si une taille de segment de *k* est spécifiée. Parmi ces planifications, la `guided` planification est caractérisée par la propriété qui requiert le moins de synchronisations. Pour la taille de segment *k*, une implémentation classique affectera des itérations *q = Ceiling (n/p)* au premier thread disponible, définissez *n* sur la plus grande de *n-q* et *p \* k*, puis répétez l’opération jusqu’à ce que toutes les itérations soient affectées.

Lorsque le choix de la planification optimale n’est pas aussi clair que pour ces exemples, la `runtime` planification est pratique pour expérimenter différentes planifications et tailles de bloc sans avoir à modifier et recompiler le programme. Elle peut également être utile lorsque la planification optimale dépend (de façon prévisible) des données d’entrée auxquelles le programme est appliqué.

Pour voir un exemple des compromis entre les différentes planifications, envisagez de partager des itérations 1000 entre huit threads. Supposez qu’il existe une quantité indifférente de travail dans chaque itération et utilisez-la en tant qu’unité de temps.

Si tous les threads démarrent en même temps, la `static` planification entraîne l’exécution de la construction en unités 125, sans synchronisation. Mais supposons que l’un des threads est de 100 unités en retard dans l’arrivée. Ensuite, les sept threads restants attendent 100 unités au niveau du cloisonnement, et la durée d’exécution de la construction entière augmente à 225.

Étant donné que `dynamic` les `guided` planifications et s’assurent qu’aucun thread n’attend plus d’une unité au niveau du cloisonnement, le thread retardé fait en sorte que les temps d’exécution de la construction augmentent uniquement jusqu’à 138 unités, éventuellement augmentés par des retards de synchronisation. Si ces délais ne sont pas négligeables, il est important que le nombre de synchronisations soit de 1000 pour `dynamic` , mais seulement 41 pour `guided` , en supposant que la taille de segment par défaut est de 1. Avec une taille de segment de 25, `dynamic` et `guided` toutes deux se terminent en 150 unités, plus tous les retards des synchronisations requises, qui sont désormais numérotés uniquement 40 et 20, respectivement.
