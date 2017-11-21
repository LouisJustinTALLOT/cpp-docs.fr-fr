---
title: "Expressions avec opérateurs unaires | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48ebd210b67f07847ceccec05625fe01eb15055b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="expressions-with-unary-operators"></a>Expressions avec opérateurs unaires
Les opérateurs unaires agissent sur un seul opérande dans une expression. Opérateurs unaires :  
  
-   [Opérateur d’indirection (*)](../cpp/indirection-operator-star.md)  
  
-   [Opérateur d’adresse (&)](../cpp/address-of-operator-amp.md)  
  
-   [Opérateur (+) plus unaire](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Opérateur de négation unaire (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Opérateur de négation logique ( !)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [L’opérateur de complément (~)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [Opérateur de pré-incrémentation (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Opérateur de pré-décrémentation (-)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Opérateur de cast ()](../cpp/cast-operator-parens.md)  
  
-   [opérateur sizeof](../cpp/sizeof-operator.md)  
  
-   [__uuidof, opérateur](../cpp/uuidof-operator.md)  
  
-   [__alignof, opérateur](../cpp/alignof-operator.md)  
  
-   [New, opérateur](../cpp/new-operator-cpp.md)  
  
-   [Delete (opérateur)](../cpp/delete-operator-cpp.md)  
  
 Ces opérateurs ont une associativité de droite à gauche. Les expressions unaires impliquent en général une syntaxe qui précède une expression primaire ou suffixée.  
  
 Voici les formes possibles des expressions unaires :  
  
-   *postfix-expression*  
  
-   `++`*expression unaire*  
  
-   `--`*expression unaire*  
  
-   *opérateur unaire* *expression de cast*  
  
-   `sizeof`*expression unaire*  
  
-   `sizeof(`*-nom du type*`)`  
  
-   `decltype(`*expression*`)`  
  
-   *allocation-expression*  
  
-   *expression de désallocation*  
  
 N’importe quel *postfix-expression* est considéré comme un *expression unaire*, et parce que n’importe quelle expression principale est considéré comme un *postfix-expression*, toutes les expressions primaires est considéré comme un *expression unaire* également. Pour plus d’informations, consultez [Expressions suffixées](../cpp/postfix-expressions.md) et [Expressions primaires](../cpp/primary-expressions.md).  
  
 A *-unaire* se compose d’un ou plusieurs des symboles suivants :`* & + - ! ~`  
  
 Le *cast-expression* est une expression unaire avec un transtypage facultatif pour modifier le type. Pour plus d’informations, consultez [opérateur de Cast : ()](../cpp/cast-operator-parens.md).  
  
 Un *expression* peut être toute expression. Pour plus d’informations, consultez [Expressions](../cpp/expressions-cpp.md).  
  
 Le *allocation-expression* fait référence à la `new` opérateur. Le *désallocation-expression* fait référence à la `delete` opérateur. Pour plus d'informations, reportez-vous aux liens fournis plus haut dans cette rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’expressions](../cpp/types-of-expressions.md)