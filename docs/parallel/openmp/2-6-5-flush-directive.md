---
title: 2.6.5 Directive flush | Microsoft Docs
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
ms.openlocfilehash: d67453b636d50fcb78092318ebb76f5192817548
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442732"
---
# <a name="265-flush-directive"></a>2.6.5 Directive flush

Le **vider** directive, explicite ou implicite, spécifie un point de séquence de « inter-threads » au niveau duquel l’implémentation est requise pour garantir que tous les threads dans une équipe ont une vue cohérente de certains objets (indiqué ci-dessous) dans mémoire. Cela signifie que les précédentes versions d’évaluation des expressions qui font référence à ces objets sont terminées et les évaluations suivantes n’ont pas encore commencé. Par exemple, compilateurs doivent restaurer les valeurs des objets à partir des registres vers la mémoire et matériel a peut-être besoin vider les mémoires tampons d’écriture vers la mémoire et recharger les valeurs des objets de la mémoire.

La syntaxe de la **vider** directive se présente comme suit :

```
#pragma omp flush [(variable-list)]  new-line
```

Si les objets qui nécessitent une synchronisation peuvent désignées par des variables, ces variables peuvent être spécifiées dans le paramètre facultatif *variable-list*. Si un pointeur est présent dans le *variable-list*, le pointeur lui-même est vidé, pas l’objet le pointeur fait référence à.

Un **vider** directive sans un *variable-list* synchronise les objets partagés à l’exception des objets inaccessibles avec une durée de stockage automatique. (Cela est susceptible d’avoir plus de frais qu’un **vider** avec un *variable-list*.) Un **vider** directive sans un *variable-list* est implicite pour les directives suivantes :

- `barrier`

- À l’entrée et la sortie à partir de **critiques**

- À l’entrée et la sortie à partir de `ordered`

- À l’entrée et la sortie à partir de **parallèles**

- Quitter at **pour**

- Quitter at **sections**

- Quitter at **unique**

- À l’entrée et la sortie à partir de **parallèles pour**

- À l’entrée et la sortie à partir de **de sections parallèles**

La directive n’est pas INDUITE si un `nowait` clause est spécifiée. Il convient de noter que le **vider** directive n’est pas impliquée pour les éléments suivants :

- Lors de l’entrée à **pour**

- Entrée ou sortie à partir de **maître**

- Lors de l’entrée à **sections**

- Lors de l’entrée à **unique**

Une référence qui accède à la valeur d’un objet avec un type qualifié volatile se comporte comme s’il existait un **vider** directive en spécifiant le point de séquence précédent de cet objet. Une référence qui modifie la valeur d’un objet avec un type qualifié volatile se comporte comme s’il existait un **vider** directive en spécifiant le point de séquence suivante de cet objet.

Notez que, comme le **vider** directive n’a pas d’une instruction de langage C dans le cadre de sa syntaxe, il existe certaines restrictions sur son positionnement dans un programme. Consultez [annexe C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) pour la grammaire formelle. L’exemple ci-dessous illustre ces restrictions.

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

Restrictions pour le **vider** directive sont les suivantes :

- Une variable spécifiée dans un **vider** directive ne doit pas avoir un type référence.