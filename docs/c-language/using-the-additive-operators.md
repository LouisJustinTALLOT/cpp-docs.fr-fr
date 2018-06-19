---
title: Utilisation des opérateurs additifs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44259ef77e5f09a1723064683c6900e425eb35c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385918"
---
# <a name="using-the-additive-operators"></a>Utilisation des opérateurs additifs
Les exemples suivants, qui illustrent les opérateurs d'addition et de soustraction, utilisent ces déclarations :  
  
```  
int i = 4, j;  
float x[10];  
float *px;  
```  
  
 Ces instructions sont équivalentes :  
  
```  
px = &x[4 + i];  
px = &x[4] + i;    
```  
  
 La valeur de `i` est multipliée par la longueur d’un **float** et ajoutée à `&x[4]`. La valeur de pointeur résultante est l'adresse de `x[8]`.  
  
```  
j = &x[i] - &x[i-2];  
```  
  
 Dans cet exemple, l'adresse du troisième élément de `x` (donné par `x[i-2]`) est ensuite soustraite dans l'adresse du cinquième élément de `x` (donné par `x[i]`). La différence est divisée par la longueur d’un **float** ; le résultat est la valeur entière 2.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs additifs C](../c-language/c-additive-operators.md)