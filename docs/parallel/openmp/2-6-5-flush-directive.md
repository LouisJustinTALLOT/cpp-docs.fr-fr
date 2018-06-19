---
title: 2.6.5 Directive flush | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad3b34195015f57955c5be685807ec43f0a8f8c6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692335"
---
# <a name="265-flush-directive"></a>2.6.5 Directive flush
Le **vider** directive, explicite ou implicite, spécifie un point de séquence de « inter-threads » à laquelle l’implémentation est requise pour garantir que tous les threads dans une équipe ont une vue cohérente de certains objets (indiqué ci-dessous) dans mémoire. Cela signifie que des évaluations précédentes des expressions qui font référence à ces objets sont terminées et que les évaluations suivantes n’ont pas encore commencé. Par exemple, compilateurs doivent restaurer les valeurs des objets à partir de registres à la mémoire et matériel devrez peut-être vider les mémoires tampons d’écriture dans la mémoire et de recharger les valeurs des objets de la mémoire.  
  
 La syntaxe de la **vider** la directive est la suivante :  
  
```  
#pragma omp flush [(variable-list)]  new-line  
```  
  
 Si les objets qui nécessitent une synchronisation peuvent désignées par des variables, ces variables peuvent être spécifiées dans le paramètre facultatif *variable-list*. Si un pointeur est présent dans le *liste de la variable*, le pointeur lui-même est vidé, pas l’objet le pointeur fait référence à.  
  
 A **vider** directive sans un *variable-list* synchronise des objets partagés à l’exception des objets inaccessibles avec une durée de stockage automatique. (Il s’agit probablement d’une charge plus importante qu’un **vider** avec un *variable-list*.) A **vider** directive sans un *liste de la variable* est implicite pour les directives suivantes :  
  
-   `barrier`  
  
-   À l’entrée et la sortie à partir de **critiques**  
  
-   À l’entrée et la sortie à partir de `ordered`  
  
-   À l’entrée et la sortie à partir de **parallèle**  
  
-   Quitter at **pour**  
  
-   Quitter at **sections**  
  
-   Quitter at **unique**  
  
-   À l’entrée et la sortie à partir de **parallèle pour**  
  
-   À l’entrée et la sortie à partir de **de sections parallèles**  
  
 La directive n’est pas impliquée si un `nowait` clause n’est présente. Il convient de noter que la **vider** directive n’est pas impliquée pour les éléments suivants :  
  
-   Lors de l’entrée à **pour**  
  
-   À l’entrée ou sortie de **master**  
  
-   Lors de l’entrée à **sections**  
  
-   Lors de l’entrée à **unique**  
  
 Une référence qui accède à la valeur d’un objet avec un type qualifié volatile se comporte comme s’il existait un **vider** directive spécifiant le point de séquence précédent de cet objet. Une référence qui modifie la valeur d’un objet avec un type qualifié volatile se comporte comme s’il existait un **vider** directive spécifiant le point de séquence suivante de cet objet.  
  
 Étant donné que la **vider** directive n’a pas d’une instruction de langage C dans le cadre de sa syntaxe, il existe certaines restrictions sur son positionnement dans un programme. Consultez [annexe C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) pour la grammaire formelle. L’exemple ci-dessous illustre ces restrictions.  
  
```  
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
  
 Restrictions à le **vider** directive sont les suivantes :  
  
-   Une variable spécifiée dans un **vider** directive ne doit pas avoir un type référence.