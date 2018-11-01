---
title: D. À l’aide de la Clause schedule
ms.date: 11/04/2016
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
ms.openlocfilehash: 85386c913a6e447ba9e71231be8b951eef504fea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627524"
---
# <a name="d-using-the-schedule-clause"></a>D. À l’aide de la Clause schedule

Une région parallèle a au moins un des principaux obstacles, à sa fin et peut avoir des barrières supplémentaires qu’il contient. À chaque cloisonnement, les autres membres de l’équipe doivent attendre le dernier thread arrive. Pour réduire ce temps d’attente, le travail partagé doit être distribuée afin que tous les threads arrivent à la barrière à près en même temps. Si certains des partageant le travail est contenu dans **pour** construit, le `schedule` clause peut être utilisée à cet effet.

Lorsqu’il existe plusieurs fois référence aux objets de mêmes, le choix de planification pour un **pour** construction peut être déterminée principalement par les caractéristiques du système de mémoire, telles que la présence et la taille des caches et si l’accès mémoire les heures sont uniforme ou non uniforme. Ces considérations, il peut être préférable de disposer de chaque thread systématiquement le même ensemble d’éléments d’un tableau dans une série de boucles, même si certains threads sont assignés relativement moins de travail dans des boucles. Cela est possible à l’aide de la **statique** planification avec les mêmes limites pour toutes les boucles. Dans l’exemple suivant, notez que zéro est utilisée comme limite inférieure dans la seconde boucle, même si **k** serait plus naturelle, si la planification n’était pas importante.

```
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

Dans les autres exemples, il est supposé que la mémoire accès n’est pas la considération dominante et, sauf indication contraire, tous les threads de réception des ressources de calcul comparables. Dans ce cas, le choix de planification pour un **pour** construction dépend de tout le travail partagé doit être effectuée entre la précédente la plus proche cloisonnement et soit la barrière de fermeture implicite ou la plus proche de la barrière suivant, s’il existe un `nowait` clause. Pour chaque type de planification, un court exemple montre comment ce type de planification est susceptible d’être le meilleur choix. Une brève présentation suit chaque exemple.

Le **statique** planification est également appropriée pour le cas le plus simple, une région parallèle contenant un seul **pour** construire, avec chaque nouvelle itération nécessitant la même quantité de travail.

```
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

Le **statique** planification est caractérisée par les propriétés que chaque thread obtient environ le même nombre d’itérations que les autres threads, et chaque thread peut déterminer indépendamment les itérations qui lui est assignées. Par conséquent, aucune synchronisation n’est requise pour distribuer le travail et, en partant du principe que chaque itération nécessite la même quantité de travail, tous les threads doivent achèveront en même temps.

Pour une équipe de `p` permettent de threads, *ceiling(n/p)* être l’entier *q*, qui répondent aux *n = p\*q - r* avec *0 < = r < p* . Une implémentation de la **statique** planifier pour cet exemple affecteriez *q* itérations au premier *p-1* threads, et *q-r* nombre d’itérations pour le dernier thread.  Une autre implémentation acceptable affecteriez *q* itérations au premier *p-r* threads, et *q-1* itérations pour les autres *r*threads. Cela illustre la raison pour laquelle un programme ne doit pas compter sur les détails d’une implémentation particulière.

Le **dynamique** planification est appropriée dans le cas d’un **pour** construire avec les itérations nécessitant une variables, ou même imprévisibles, de gros efforts.

```
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

Le **dynamique** planification se caractérise par la propriété aucun thread n’attend à la barrière plus qu’il ne faut de temps un autre thread pour exécuter sa dernière itération. Cela nécessite que les itérations attribuées individuellement à la fois aux threads qu’elles sont disponibles, avec la synchronisation de chaque affectation. La surcharge de synchronisation peut être réduite en spécifiant une taille de segment minimale *k* supérieure à 1, afin que les threads sont assignés *k* à la fois tant que moins de *k* restent. Cela garantit qu’aucun thread n’attend à la barrière plus longtemps que nécessaire à un autre thread à exécuter (au plus) de son bloc final de *k* itérations.

Le **dynamique** planification peut être utile si les threads de réception différents des ressources de calcul, ce qui a beaucoup le même effet que différentes quantités de travail pour chaque itération. De même, la planification dynamique peut également être utile si les threads arrivent à la **pour** construire à des moments différents, bien que, dans certains cas le **guidée** planification peut être préférable.

Le **guidée** planification est appropriée pour le cas dans lequel les threads peuvent arriver à des moments différents à un **pour** construire avec chaque itération nécessitant environ la même quantité de travail. Cela peut se produire si, par exemple, le **pour** construction est précédée d’une ou plusieurs sections ou **pour** construit avec `nowait` clauses.

```
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

Comme **dynamique**, le **guidée** planifier garanties aucun thread n’attend au niveau de la barrière de plus de temps que prend un autre thread pour exécuter sa dernière itération ou finale *k* itérations si une taille de segment de *k* est spécifié. Parmi ces planifications, les **guidée** planification se caractérise par la propriété qu’il nécessite les synchronisations moins. Pour la taille de segment *k*, une implémentation classique attribuera *q = ceiling(n/p)* itérations pour le premier thread disponible, définissez *n* à la plus grande de *n-q* et *p\*k*, jusqu'à ce que toutes les itérations sont affectées.

Lorsque le choix de la planification n’est pas aussi clairement que c’est pour ces exemples, le **runtime** planification est pratique pour tester différentes planifications et des tailles de segment sans avoir à modifier et recompiler le programme. Il peut également être utile lorsque la planification (d’une certaine façon prévisible) basée sur les données d’entrée à laquelle le programme est appliqué.

Pour voir un exemple de compromis entre les différentes planifications, envisagez de partager les 1000 itérations entre 8 threads. Supposez qu’il existe une invariante quantité de travail dans chaque itération et l’utiliser comme unité de temps.

Si tous les threads démarrent en même temps, le **statique** planification entraîne la construction à exécuter en unités de 125, sans synchronisation. Mais supposons qu’un seul thread est de 100 unités vers la fin de l’arrivée. Les threads restants sept attendent ensuite à la barrière de 100 unités, et la durée d’exécution pour la construction entière à 225.

Étant donné qu’à la fois le **dynamique** et **guidée** planifications vous assurer qu’aucun thread n’attend plus d’une unité à la barrière, le thread retardée provoque leurs temps d’exécution de la construction d’augmenter uniquement à 138 unités, éventuellement augmentées des retards de synchronisation. Si ces délais ne sont pas négligeables, il est important que le nombre de synchronisations est 1000 pour **dynamique** mais 41 uniquement pour **guidée**, en supposant que la taille de segment par défaut d’un. Avec une taille de segment de 25, **dynamique** et **guidée** à la fois terminer 150 unités, ainsi que les retards des synchronisations requises, le numéro maintenant uniquement 40 et 20, respectivement.