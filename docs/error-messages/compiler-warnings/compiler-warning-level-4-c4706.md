---
title: Compilateur avertissement (niveau 4) C4706 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1131147a9600525746cb3e89119189ed9e5026a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296967"
---
# <a name="compiler-warning-level-4-c4706"></a>Avertissement du compilateur (niveau 4) C4706
affectation dans une expression conditionnelle  
  
 La valeur de test dans une expression conditionnelle était le résultat d’une assignation.  
  
 Une affectation a la valeur (la valeur sur le côté gauche de l’assignation) qui peut être légalement utilisée dans une autre expression, y compris une expression de test.  
  
 L’exemple suivant génère l’erreur C4706 :  
  
```  
// C4706a.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a  = b ) // C4706  
   {  
   }  
}  
```  
  
 L’avertissement se produit même si vous doublez les parenthèses autour de la condition de test :  
  
```  
// C4706b.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a  =  b ) ) // C4706  
   {  
   }  
}  
```  
  
 Si votre intention est de tester une relation et non ne pas d’effectuer une assignation, utilisez le `==` opérateur. Par exemple, la ligne suivante tests si un et b sont égaux :  
  
```  
// C4706c.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a == b )  
   {  
   }  
}  
```  
  
 Si vous souhaitez que votre test de valeur au résultat d’une assignation, tester pour vous assurer que l’affectation est différente de zéro ou non null. Par exemple, le code suivant génère pas cet avertissement :  
  
```  
// C4706d.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a = b ) != 0 )  
   {  
   }  
}  
```