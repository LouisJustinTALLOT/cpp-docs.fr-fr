---
title: Erreur du compilateur C3488 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3488
dev_langs:
- C++
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
caps.latest.revision: 8
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
ms.openlocfilehash: 6c7f36a63d5922672e89faf0c7d73c95100b256d
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3488"></a>Erreur du compilateur C3488
'var' n’est pas autorisé quand le mode de capture par défaut est par référence  
  
 Quand vous spécifiez que le mode de capture par défaut d’une expression lambda est par référence, vous ne pouvez pas passer une variable par référence à la clause de capture de cette expression.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ne passez pas explicitement la variable à la clause de capture.  
  
-   Ne spécifiez pas le mode de capture par défaut par référence.  
  
-   Spécifiez le mode de capture par défaut par valeur.  
  
-   Passez la variable par valeur à la clause de capture. (Cela peut modifier le comportement de l’expression lambda.)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3488, car une référence à la variable `n` apparaît dans la clause de capture d’une expression lambda dont le mode par défaut est par référence :  
  
```  
// C3488a.cpp  
  
int main()  
{  
   int n = 5;  
   [&, &n]() { return n; } (); // C3488  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre quatre résolutions possibles de l’erreur C3488 :  
  
```  
// C3488b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass &n to the capture clause.  
   [&]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-reference as the default capture mode.  
   [&n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-value as the default capture mode.  
   [=, &n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by value to the capture clause.  
   [n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
