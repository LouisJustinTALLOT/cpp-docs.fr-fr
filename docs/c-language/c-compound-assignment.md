---
title: "Assignation composée C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b8b9166c1beae167f6d31913c3df10a8f57bbef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="c-compound-assignment"></a>Assignation composée C
Les opérateurs d'assignation composée combinent l'opérateur d'assignation simple à un autre opérateur binaire. Ils exécutent l'opération spécifiée par l'opérateur supplémentaire, puis assignent le résultat à l'opérande gauche. Par exemple, une expression d'assignation composée telle que  
  
```  
  
expression1  
+=  
expression2  
  
```  
  
 peut être comprise comme  
  
```  
  
expression1  
=  
expression1  
+  
expression2  
  
```  
  
 Toutefois, l’expression d’assignation composée n’équivaut pas à la version développée, car elle évalue *expression1* une seule fois, tandis que la version développée évalue *expression1* deux fois : dans l’opération d’addition et dans l’opération d’assignation.  
  
 Les opérandes d’un opérateur d’assignation composée doivent être de type intégral ou flottant. Chaque opérateur d’assignation composée exécute les conversions effectuées par l’opérateur binaire correspondant et restreint les types de ses opérandes en conséquence. Les opérateurs d’assignation d’addition (`+=`) et d’assignation de soustraction (**-=**) peuvent également avoir un opérande gauche de type pointeur, auquel cas l’opérande droit doit être de type intégral. Le résultat d’une opération d’assignation composée a la valeur et le type de l’opérande gauche.  
  
```  
#define MASK 0xff00  
  
n &= MASK;  
```  
  
 Dans cet exemple, une opération AND inclusive au niveau du bit est exécutée sur `n` et `MASK`, et le résultat est assigné à `n`. La constante de manifeste `MASK` est définie avec une directive de préprocesseur [#define](../preprocessor/hash-define-directive-c-cpp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs d’assignation C](../c-language/c-assignment-operators.md)