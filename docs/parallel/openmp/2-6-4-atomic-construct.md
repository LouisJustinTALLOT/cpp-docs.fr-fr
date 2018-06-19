---
title: 2.6.4 construction atomic | Documents Microsoft
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
ms.openlocfilehash: 66f0dc8469d1d70b2697df1fe120f10142d90dbe
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688126"
---
# <a name="264-atomic-construct"></a>2.6.4 Construction atomic
Le `atomic` directive garantit qu’un emplacement de mémoire spécifique est mise à jour atomiquement, plutôt que d’exposer la possibilité de plusieurs simultanées de l’écriture de threads. La syntaxe de la `atomic` la directive est la suivante :  
  
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
  
-   `binop` n’est pas un opérateur surchargé et fait partie de +, *, -, /, &, ^, &#124;, <\<, ou >>.  
  
 Bien qu’il soit défini par l’implémentation indique si une implémentation remplace toutes les `atomic` directives avec **critique** directives qui ont le même unique *nom*, le `atomic` (directive) autorise une meilleure optimisation. Fréquence à laquelle les instructions de matériel sont disponibles qui peut effectuer la mise à jour atomique avec le moins de surcharge.  
  
 Uniquement la charge et le magasin de l’objet désigné par *x* sont atomique ; de l’évaluation de *expr* n’est pas atomique. Pour éviter des conditions de concurrence, toutes les mises à jour de l’emplacement en parallèle doivent être protégés avec le `atomic` directive, sauf ceux qui sont connus comme étant libre des conditions de concurrence.  
  
 Restrictions à le `atomic` directive sont les suivantes :  
  
-   Toutes les références atomiques à l’emplacement de stockage x partout dans le programme doit être un type compatible.  
  
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