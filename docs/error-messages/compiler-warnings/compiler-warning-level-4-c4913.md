---
title: Compilateur avertissement (niveau 4) C4913 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4913
dev_langs:
- C++
helpviewer_keywords:
- C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: a452937a9ba1999083ba3c980b0e74943f4cd9e5
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4913"></a>Avertissement du compilateur (niveau 4) C4913
**utilisateur opérateur binaire défini par ',' à existe mais aucune surcharge n’a pu convertir tous les opérandes, opérateur binaire intégré de valeur par défaut ',' utilisé**  
  
 Un appel à l’opérateur virgule intégré s’est produit dans un programme où figure également un opérateur virgule surchargé. Une conversion censée être terminée n’a pas été effectuée.  
  
 Le code suivant génère l’avertissement C4913 :  
  
```  
// C4913.cpp  
// compile with: /W4  
struct A  
{  
};  
  
struct S  
{  
};  
  
struct B  
{  
   // B() { }  
   // B(S &s) { s; }  
};  
  
B operator , (A a, B b)     
{  
   a;  
   return b;  
}  
  
int main()  
{  
   A a;  
   B b;  
   S s;  
  
   a, b;   // OK calls user defined operator  
   a, s;   // C4913 uses builtin comma operator  
           // uncomment the conversion code in B to resolve.  
}  
```
