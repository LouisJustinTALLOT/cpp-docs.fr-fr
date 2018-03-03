---
title: "Opérateur d'évaluation séquentielle | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6dee769d0a5bc2d0992dfb51de240bdd5e3d62d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sequential-evaluation-operator"></a>Opérateur d'évaluation séquentielle
L’opérateur d’évaluation séquentielle, appelé aussi opérateur virgule, évalue ses deux opérandes de manière séquentielle de gauche à droite.  
  
## <a name="syntax"></a>Syntaxe  
 *expression* :  
 *assignment-expression*  
  
 *expression*  **,**  *assignment-expression*  
  
 L'opérande gauche de l'opérateur d'évaluation séquentielle est évalué comme une expression `void`. Le résultat de l'opération a la même valeur et le même type que l'opérande droite. Chaque opérande peut être de tout type. L'opérateur d'évaluation séquentielle n'effectue pas de conversions de type entre ses opérandes et ne produit pas de l-value. Il existe un point de séquence après le premier opérande. Cela signifie que tous les effets secondaires de l’évaluation de l’opérande gauche sont terminés avant le début de l’évaluation de l’opérande droite. Pour plus d'informations, consultez [Points de séquence](../c-language/c-sequence-points.md).  
  
 L'opérateur d'évaluation séquentielle est généralement utilisé pour évaluer deux expressions ou plus dans les contextes où une seule expression est autorisée.  
  
 Les virgules peuvent être utilisées comme séparateurs dans certains contextes. Toutefois, vous devez faire attention à ne pas confondre l'utilisation de la virgule comme séparateur avec son utilisation comme opérateur. Ces deux utilisations sont entièrement différentes.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'opérateur d'évaluation séquentielle :  
  
```  
for ( i = j = 1; i + j < 20; i += i, j-- );  
```  
  
 Dans cet exemple, chaque opérande de la troisième expression de l’instruction **for** est évalué indépendamment. L'opérande gauche `i += i` est évalué en premier, puis l'opérande droite `j--`.  
  
```  
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 Dans l'appel de fonction à `func_one`, trois arguments, séparés par des virgules, sont passés : `x`, `y + 2` et `z`. Dans l'appel de fonction à `func_two`, les parenthèses forcent le compilateur à interpréter la première virgule comme l'opérateur d'évaluation séquentielle. Cet appel de fonction passe deux arguments à `func_two`. Le premier argument est le résultat de l'opération d'évaluation séquentielle `(x--, y + 2)`, qui a la valeur et le type de l'expression `y + 2`. Le second argument est `z`.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur virgule : ,](../cpp/comma-operator.md)