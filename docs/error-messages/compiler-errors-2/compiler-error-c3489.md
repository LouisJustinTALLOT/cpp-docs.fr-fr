---
title: Erreur du compilateur C3489 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3489
dev_langs:
- C++
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd620c969f89b1889384fe3f4d7f899957ae620b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253316"
---
# <a name="compiler-error-c3489"></a>Erreur du compilateur C3489
'var' est obligatoire lorsque le mode de capture par défaut est le mode par valeur  
  
 Quand vous spécifiez que le mode de capture par défaut d’une expression lambda est par valeur, vous ne pouvez pas passer une variable par valeur à la clause de capture de cette expression.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ne passez pas explicitement la variable à la clause de capture.  
  
-   Ne spécifiez pas le mode de capture par valeur comme mode par défaut.  
  
-   Spécifiez le mode de capture par référence comme mode par défaut.  
  
-   Passez la variable par référence à la clause de capture. (Cela peut modifier le comportement de l’expression lambda.)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3489 car la variable `n` apparaît par valeur dans la clause de capture d’une expression lambda dont le mode par défaut est par valeur :  
  
```  
// C3489a.cpp  
  
int main()  
{  
   int n = 5;  
   [=, n]() { return n; } (); // C3489  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre quatre résolutions possibles de l’erreur C3489 :  
  
```  
// C3489b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass n to the capture clause.  
   [=]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-value as the default capture mode.  
   [n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-reference as the default capture mode.  
   [&, n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by reference to the capture clause.  
   [&n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)