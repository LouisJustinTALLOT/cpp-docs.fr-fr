---
title: Tableaux multidimensionnels (C) | Microsoft Docs
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
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 21a234fc128b745116b27265cc060b9513bef36b
ms.contentlocale: fr-fr
ms.lasthandoff: 05/18/2017

---
# <a name="multidimensional-arrays-c"></a>Tableaux multidimensionnels (C)
Une expression d'indice peut également avoir plusieurs indices, comme suit :  
  
```  
  
expression1  
[  
expression2  
] [  
expression3  
]...  
```  
  
 Les expressions d'indice s'associent de gauche à droite. L'expression d'indice extrême gauche, *expression1***[***expression2***]**, est évaluée en premier. L'adresse qui résulte de l'ajout *d'expression1* et *expression2* forme une expression de pointeur. Ensuite, *expression3* est ajouté à cette expression de pointeur pour former une nouvelle expression de pointeur, et ainsi de suite jusqu'à ce que la dernière expression d'indice ait été ajoutée. L'opérateur d'indirection (**\***) est appliqué après l'évaluation de la dernière expression d'indice, sauf si la valeur de pointeur finale traite un type tableau (voir les exemples ci-dessous).  
  
 Les expressions à indices multiples font référence à des éléments de tableaux multidimensionnels. Un tableau multidimensionnel est un tableau dont les éléments sont des tableaux. Par exemple, le premier élément d'un tableau tridimensionnel est un tableau à deux dimensions.  
  
## <a name="examples"></a>Exemples  
 Pour les exemples suivants, un tableau nommé `prop` est déclaré avec trois éléments, dont chacun est un tableau 4-par-6 de valeurs `int`.  
  
```  
int prop[3][4][6];  
int i, *ip, (*ipp)[6];  
```  
  
 Une référence au tableau `prop` ressemble à ceci :  
  
```  
i = prop[0][0][1];  
```  
  
 L'exemple ci-dessus montre comment faire référence au deuxième élément `int` individuel de `prop`. Les tableaux sont stockés par ligne, le dernier indice variant ainsi plus rapidement. L'expression `prop[0][0][2]` fait référence à l'élément suivant (le troisième), et ainsi de suite.  
  
```  
i = prop[2][1][3];  
```  
  
 Cette instruction est une référence plus complexe à un élément de `prop` individuel. L'expression est évaluée de la manière suivante :  
  
1.  Le premier indice, `2`, est multiplié par la taille d'un tableau de 4 par 6 `int` et ajouté à la valeur de pointeur `prop`. Le résultat pointe vers le tableau de 4 par 6 de `prop`.  
  
2.  Le deuxième indice, `1`, est multiplié par la taille du tableau `int` de 6 éléments et ajouté à l'adresse représentée par `prop[2]`.  
  
3.  Chaque élément du tableau de 6 éléments est une valeur `int`. Donc, l'indice final, `3`, est multiplié par la taille d'un `int` avant d'être ajouté à `prop[2][1]`. Le pointeur résultant traite le quatrième élément du tableau de 6 éléments.  
  
4.  L'opérateur d'indirection est appliqué à la valeur du pointeur. Le résultat est l'élément `int` à cette adresse.  
  
 Les deux exemples suivants présentent des cas où l'opérateur d'indirection n'est pas appliqué.  
  
```  
ip = prop[2][1];  
  
ipp = prop[2];  
```  
  
 Dans la première de ces instructions, l'expression `prop[2][1]` est une référence valide au tableau tridimensionnel `prop`. Elle fait référence à un tableau de 6 éléments (déclaré ci-dessus). La valeur de pointeur adressant un tableau, l'opérateur d'indirection n'est pas appliqué.  
  
 De même, le résultat de l'expression `prop[2]` dans la deuxième instruction `ipp = prop[2];` est une valeur de pointeur adressant un tableau à deux dimensions.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur d’indice](../cpp/subscript-operator.md)
