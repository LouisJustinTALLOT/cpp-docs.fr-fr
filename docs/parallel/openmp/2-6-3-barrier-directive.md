---
title: 2.6.3 Directive barrier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8654534143e6feed06e93406c8fe03983ee9c2fc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429147"
---
# <a name="263-barrier-directive"></a>2.6.3 Directive barrier

Le **barrière** directive synchronise tous les threads dans une équipe. Dans ce cas, chaque thread dans l’équipe attend jusqu'à ce que toutes les autres ont atteint ce point. La syntaxe de la **barrière** directive se présente comme suit :

```
#pragma omp barrier new-line
```

Une fois que tous les threads de l’équipe ont rencontré le cloisonnement, chaque thread dans l’équipe commence l’exécution des instructions après la directive de cloisonnement en parallèle. Notez que, comme le **barrière** directive n’a pas d’une instruction de langage C dans le cadre de sa syntaxe, il existe certaines restrictions sur son positionnement dans un programme. Consultez [annexe C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) pour la grammaire formelle. L’exemple ci-dessous illustre ces restrictions.

```
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