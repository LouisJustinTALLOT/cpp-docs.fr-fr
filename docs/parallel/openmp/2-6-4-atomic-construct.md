---
title: 2.6.4 construction atomic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c906a9a9b781f742f525688b77d5f58da16bb10
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208131"
---
# <a name="264-atomic-construct"></a>2.6.4 Construction atomic
Le `atomic` directive garantit qu’un emplacement de mémoire spécifique est mis à jour atomiquement, au lieu d’exposer à la possibilité de multiples, simultanées d’écriture de threads. La syntaxe de la `atomic` directive se présente comme suit :  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 L’instruction d’expression doit avoir la valeur de l’une des formes suivantes :  
  
 *x binop*= *expr*  
  
 x ++  
  
 ++ x  
  
 x--  
  
 --x  
  
 Dans les expressions précédentes :  
  
-   *x* est une expression lvalue avec type scalaire.  
  
-   *Expr* est une expression avec un type scalaire, et il ne fait pas référence à l’objet désigné par *x*.  
  
-   `binop` n’est pas un opérateur surchargé et fait partie de +, \*, -, /, &, ^, &#124;, <\<, ou >>.  
  
 Bien qu’il soit défini par l’implémentation si une implémentation remplace tous les `atomic` directives avec **critique** directives qui ont le même unique *nom*, le `atomic` (directive) autorise une meilleure optimisation. Souvent les instructions de matériel sont disponibles pouvant effectuer la mise à jour atomique avec le moins de surcharge.  
  
 Uniquement la charge et le magasin de l’objet désigné par *x* sont atomique ; la version d’évaluation de *expr* n’est pas atomique. Pour éviter des conditions de concurrence, toutes les mises à jour de l’emplacement en parallèle doivent être protégés avec le `atomic` directive, sauf ceux qui sont connus comme étant libre des conditions de concurrence.  
  
 Restrictions à le `atomic` directive sont les suivantes :  
  
-   Toutes les références atomiques à l’emplacement de stockage x tout au long du programme doivent avoir un type compatible.  
  
## <a name="examples"></a>Exemples :  
  
```  
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