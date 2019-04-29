---
title: D. La clause schedule
ms.date: 01/22/2019
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
ms.openlocfilehash: 89e011784c5cccedc4a75f38d553458ea2e5d7e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362879"
---
# <a name="d-the-schedule-clause"></a>D. La clause schedule

Une région parallèle a au moins un des principaux obstacles, à sa fin et peut avoir des barrières supplémentaires qu’il contient. À chaque cloisonnement, les autres membres de l’équipe doivent attendre le dernier thread arrive. Pour réduire ce temps d’attente, le travail partagé doit être distribuée afin que tous les threads arrivent à la barrière à près en même temps. Si certains des partageant le travail est contenu dans `for` construit, le `schedule` clause peut être utilisée à cet effet.

Lorsqu’il existe plusieurs fois référence aux objets de mêmes, le choix de planification pour un `for` construction peut être déterminée principalement par les caractéristiques du système de mémoire, telles que la présence et la taille des caches et indique si les heures d’accès mémoire sont uniformes ou Nonuniform. Ces considérations, il peut être préférable de disposer de chaque thread systématiquement le même ensemble d’éléments d’un tableau dans une série de boucles, même si certains threads sont assignés relativement moins de travail dans des boucles. Ce programme d’installation peut être effectuée à l’aide de la `static` planification avec les mêmes limites pour toutes les boucles. Dans l’exemple suivant, zéro est utilisée comme limite inférieure dans la seconde boucle, même si `k` serait plus naturelle, si la planification n’était pas importante.

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

Dans les autres exemples, il est supposé que la mémoire accès n’est pas la considération dominante. Sauf indication contraire, tous les threads de réception des ressources de calcul comparables. Dans ce cas, le choix de planification pour un `for` construction dépend de tout le travail partagé doit être effectuée entre la précédente la plus proche cloisonnement et soit la barrière de fermeture implicite ou la plus proche de la barrière à venir, s’il existe un `nowait` clause. Pour chaque type de planification, un court exemple montre comment ce type de planification est susceptible d’être le meilleur choix. Une brève présentation suit chaque exemple.

Le `static` planification est également appropriée pour le cas le plus simple, une région parallèle contenant un seul `for` construire, avec chaque nouvelle itération nécessitant la même quantité de travail.

```cpp
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

Le `static` planification est caractérisée par les propriétés que chaque thread obtient environ le même nombre d’itérations que les autres threads, et chaque thread peut déterminer indépendamment les itérations qui lui est assignées. Par conséquent, aucune synchronisation n’est requise pour distribuer le travail et, en partant du principe que chaque itération nécessite la même quantité de travail, tous les threads doivent achèveront en même temps.

Pour une équipe de *p* permettent de threads, *ceiling(n/p)* être l’entier *q*, qui répondent aux *n = p\*q - r* avec *0 < = r < p*. Une implémentation de la `static` planifier pour cet exemple affecteriez *q* itérations au premier *p-1* threads, et *q-r* itérations pour le dernier thread.  Une autre implémentation acceptable affecteriez *q* itérations au premier *p-r* threads, et *q-1* itérations pour les autres *r*threads. Cet exemple illustre la raison pour laquelle un programme ne doit pas s’appuient sur les détails d’une implémentation particulière.

Le `dynamic` planification est appropriée dans le cas d’un `for` construire avec les itérations nécessitant une variables, ou même imprévisibles, de gros efforts.

```cpp
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

Le `dynamic` planification se caractérise par la propriété aucun thread n’attend à la barrière plus qu’il ne faut de temps un autre thread pour exécuter sa dernière itération. Cette exigence signifie itérations doivent être assignées à la fois aux threads lorsqu’elles sont disponibles, avec la synchronisation de chaque affectation. La surcharge de synchronisation peut être réduite en spécifiant une taille de segment minimale *k* supérieure à 1, afin que les threads sont assignés *k* à la fois tant que moins de *k* restent. Cela garantit qu’aucun thread n’attend à la barrière plus longtemps que nécessaire à un autre thread à exécuter (au plus) de son bloc final de *k* itérations.

Le `dynamic` planification peut être utile si les threads de réception différents des ressources de calcul, ce qui a beaucoup le même effet que différentes quantités de travail pour chaque itération. De même, la planification dynamique peut également être utile si les threads arrivent à la `for` construire à des moments différents, bien que, dans certains cas le `guided` planification peut être préférable.

Le `guided` planification est appropriée pour le cas dans lequel les threads peuvent arriver à des moments différents à un `for` construire avec chaque itération nécessitant environ la même quantité de travail. Cette situation peut se produire si, par exemple, le `for` construction est précédée d’une ou plusieurs sections ou `for` construit avec `nowait` clauses.

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

Comme `dynamic`, le `guided` planifier garanties aucun thread n’attend au niveau de la barrière de plus de temps que prend un autre thread pour exécuter sa dernière itération ou finale *k* itérations si une taille de segment de *k* est spécifié. Parmi ces planifications, les `guided` planification se caractérise par la propriété qu’il nécessite les synchronisations moins. Pour la taille de segment *k*, une implémentation classique attribuera *q = ceiling(n/p)* itérations pour le premier thread disponible, définissez *n* à la plus grande de *n-q* et *p\*k*, jusqu'à ce que toutes les itérations sont affectées.

Lorsque le choix de la planification n’est pas aussi clairement que c’est pour ces exemples, le `runtime` planification est pratique pour tester différentes planifications et des tailles de segment sans avoir à modifier et recompiler le programme. Il peut également être utile lorsque la planification (d’une certaine façon prévisible) basée sur les données d’entrée à laquelle le programme est appliqué.

Pour voir un exemple de compromis entre les différentes planifications, envisagez de partager les 1000 itérations entre huit threads. Supposez qu’il existe une invariante quantité de travail dans chaque itération et l’utiliser comme unité de temps.

Si tous les threads démarrent en même temps, le `static` planification entraîne la construction à exécuter en unités de 125, sans synchronisation. Mais supposons qu’un seul thread est de 100 unités vers la fin de l’arrivée. Les threads restants sept attendent ensuite à la barrière de 100 unités, et la durée d’exécution pour la construction entière à 225.

Étant donné que les deux le `dynamic` et `guided` planifications vous assurer qu’aucun thread n’attend plus d’une unité à la barrière, le thread retardée provoque leurs temps d’exécution de la construction d’augmenter uniquement à des 138 unités, éventuellement augmentées des retards de synchronisation. Si ces délais ne sont pas négligeables, il est important que le nombre de synchronisations est 1000 pour `dynamic` mais 41 uniquement pour `guided`, en supposant que la taille de segment par défaut d’un. Avec une taille de segment de 25, `dynamic` et `guided` à la fois terminer 150 unités, ainsi que les retards des synchronisations requises, le numéro maintenant uniquement 40 et 20, respectivement.
