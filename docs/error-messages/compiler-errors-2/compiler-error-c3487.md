---
title: Erreur du compilateur C3487 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3487
dev_langs:
- C++
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb30b9a2cb0b77eff0888da6c387bd3b06182721
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256335"
---
# <a name="compiler-error-c3487"></a>Erreur du compilateur C3487
’type de retour’ : toutes les expressions de retour doivent déduire le même type : il s’agissait auparavant de ’type de retour’  
  
 Une expression lambda doit spécifier son type de retour, sauf si elle contient une seule instruction return. Si une expression lambda contient plusieurs instructions return, elles doivent toutes avoir le même type.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Spécifiez un type de retour de fin pour l'expression lambda. Vérifiez que tous les retours à partir de l’expression lambda sont du même type ou peuvent être convertis implicitement en type de retour.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3487 car les types de retour de l’expression lambda ne correspondent pas :  
  
```  
// C3487.cpp  
// Compile by using: cl /c /W4 C3487.cpp  
  
int* test(int* pi) {  
   // To fix the error, uncomment the trailing return type below  
   auto odd_pointer = [=]() /* -> int* */ {  
      if (*pi % 2)   
         return pi;  
      return nullptr; // C3487 - nullptr is not an int* type  
   };  
   return odd_pointer();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)