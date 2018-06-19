---
title: D. À l’aide de la Clause de planification | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8987c4505adfde8534d57346cd6725231efa022f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694938"
---
# <a name="d-using-the-schedule-clause"></a>D. À l’aide de la Clause de planification
Une région parallèle a au moins un cloisonnement, de son côté et peut avoir des obstacles supplémentaires qu’il contient. À chaque barrière, les autres membres de l’équipe doivent attendre pour le dernier thread arrivée. Pour réduire ce délai d’attente, le travail doit être distribué afin que tous les threads arrivent à la barrière en même temps. Si certains des partageant le travail est contenu dans **pour** construit, le `schedule` clause peut être utilisée à cet effet.  
  
 Lorsqu’il existe des répété références vers les objets de mêmes, le choix de la planification pour un **pour** construction peut être déterminée principalement par les caractéristiques du système de mémoire, telles que la présence et la taille des mémoires caches et si l’accès mémoire temps de sont uniforme ou non. Ces considérations, il peut être préférable de disposer de chaque thread régulièrement le même jeu d’éléments d’un tableau dans une série de boucles, même si certains threads assignés relativement moins de travail dans des boucles. Cela est possible à l’aide de la **statique** calendrier avec les mêmes limites pour toutes les boucles. Dans l’exemple suivant, notez que zéro est utilisée comme limite inférieure dans la seconde boucle, même si **k** serait plus naturel si la planification n’est pas importante.  
  
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
  
 Dans les autres exemples, il est supposé que la mémoire accès n’est pas le compte principal et, sauf indication contraire, que tous les threads reçoivent des ressources de calcul comparables. Dans ces cas, le choix de la planification pour un **pour** construction dépend de tout le travail partagé doit être effectuée entre la précédente la plus proche barrière et soit la barrière de fermeture implicite ou le plus proche de la barrière suivante, si elle existe un `nowait` clause. Pour chaque type de planification, un bref exemple montre comment ce type de planification est susceptible d’être le meilleur choix. Obtenir une brève présentation suit chaque exemple.  
  
 Le **statique** planification est également appropriée pour le cas le plus simple, une région parallèle contenant un seul **pour** construire, chaque nouvelle itération nécessitant la même quantité de travail.  
  
```  
#pragma omp parallel for schedule(static)  
for(i=0; i<n; i++) {  
  invariant_amount_of_work(i);  
}  
```  
  
 Le **statique** planification se caractérise par les propriétés que chaque thread obtient environ le même nombre d’itérations que tout autre thread, et chaque thread peut déterminer indépendamment les itérations qui lui est affectées. Par conséquent, aucune synchronisation n’est requise pour distribuer le travail et, en supposant que chaque itération nécessite la même quantité de travail, tous les threads doivent terminer à près en même temps.  
  
 Pour une équipe de `p` permettent de threads, *ceiling(n/p)* être l’entier *q*, qui répondent aux *n = p\*q - r* avec *0 < = r < p* . Une implémentation de la **statique** planifier pour cet exemple affecterait *q* itérations pour la première *p-1* threads, et *q-r* itérations pour le dernier thread.  Une autre implémentation acceptable affecterait *q* itérations pour la première *p-r* threads, et *q-1* itérations pour les autres *r*threads. Cet exemple illustre les raisons pour lesquelles un programme ne doit pas dépendre les détails d’une implémentation particulière.  
  
 Le **dynamique** planification est appropriée pour le cas d’un **pour** construire avec les itérations nécessitant des montants différents, ou même imprévisibles, de travail.  
  
```  
#pragma omp parallel for schedule(dynamic)  
  for(i=0; i<n; i++) {  
    unpredictable_amount_of_work(i);  
}  
```  
  
 Le **dynamique** planification se caractérise par la propriété aucun thread n’attend au cloisonnement plus long que celui qu’elle utilise un autre thread pour exécuter sa dernière itération. Cela nécessite que les itérations soit affecté à la fois à des threads dès qu’elles sont disponibles, avec la synchronisation pour chaque affectation. La surcharge de synchronisation peut être réduite en spécifiant une taille de segment minimum *k* supérieur à 1, afin que les threads sont affectés *k* à la fois tant que moins de *k* restent. Cela garantit qu’aucun thread n’attend au cloisonnement plus longtemps que nécessaire à un autre thread à exécuter (au plus) de son bloc final de *k* itérations.  
  
 Le **dynamique** planification peut être utile si les threads de réception différentes ressources de calcul, qui a beaucoup le même effet que des quantités variables de travail pour chaque itération. De même, la planification dynamique peut également être utile si les threads arrivent à la **pour** construire à des moments différents, bien que dans certains cas le **guidée** planification peut être préférable.  
  
 Le **guidée** planification est appropriée pour le cas dans lequel les threads peuvent arriver à des moments différents à une **pour** construire avec chaque itération nécessitant environ la même quantité de travail. Cela peut se produire si, par exemple, le **pour** construction est précédée d’une ou plusieurs sections ou **pour** construit avec `nowait` clauses.  
  
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
  
 Comme **dynamique**, le **guidée** planifier la garantie qu’aucun thread n’attend au cloisonnement plus longtemps que nécessaire à un autre thread pour exécuter sa dernière itération ou final *k* itérations si une taille de segment de *k* est spécifié. Parmi ces planifications, les **guidée** planification est caractérisée par la propriété qu’elle requiert les synchronisations moins élevé. Pour la taille de segment *k*, une implémentation classique attribuera *q = ceiling(n/p)* définir des itérations pour le premier thread disponible, *n* à la plus grande de *n-q* et *p\*k*, jusqu'à ce que toutes les itérations sont affectées.  
  
 Lorsque le choix de la planification n’est pas aussi clairement que c’est pour ces exemples, le **runtime** planification est pratique pour tester différentes planifications et les tailles de segment sans avoir à modifier et recompilez le programme. Il peut également être utile lors de la planification dépend (d’une certaine façon prévisible) des données d’entrée à laquelle le programme est appliqué.  
  
 Pour obtenir un exemple de compromis entre les différentes planifications, envisagez de partage 1000 itérations entre 8 threads. Supposez qu’il existe une invariante quantité de travail dans chaque itération et l’utiliser comme unité de temps.  
  
 Si tous les threads démarrent en même temps, le **statique** planification entraîne la construction à s’exécuter dans des unités de 125, sans synchronisation. Mais supposons qu’un seul thread est de 100 unités vers la fin de l’arrivée. Les autres sept threads attendent 100 unités à la barrière et la durée d’exécution pour la construction entière à 225.  
  
 Étant donné qu’à la fois le **dynamique** et **guidée** planifications s’assurer qu’aucun thread n’attend plus d’une unité au cloisonnement, le thread retardé provoque leurs temps d’exécution de la construction d’augmenter uniquement à 138 unités, éventuellement augmentées des délais de synchronisation. Si ces délais ne sont pas négligeables, il est important que le nombre de synchronisations est 1000 pour **dynamique** mais 41 uniquement pour **guidée**, en supposant que la taille de segment par défaut d’un. Avec une taille de segment de 25, **dynamique** et **guidée** deux terminer 150 unités, ainsi que les délais des synchronisations requises, le numéro du présent uniquement 40 et 20, respectivement.