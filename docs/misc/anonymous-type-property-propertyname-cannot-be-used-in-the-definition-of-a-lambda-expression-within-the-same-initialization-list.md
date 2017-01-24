---
title: "La propri&#233;t&#233; de type anonyme &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre utilis&#233;e dans la d&#233;finition d’une expression lambda au sein de la m&#234;me liste d’initialisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36549"
  - "bc36549"
helpviewer_keywords: 
  - "BC36549"
ms.assetid: 6d04692a-957a-41ce-a19c-fcb06a186d1a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propri&#233;t&#233; de type anonyme &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre utilis&#233;e dans la d&#233;finition d’une expression lambda au sein de la m&#234;me liste d’initialisation
Les propriétés définies dans la liste d’initialisation d’un type anonyme ne peuvent pas faire partie d’une définition d’expression lambda dans la même liste. Par exemple, dans le code suivant, la propriété `Num` ne peut pas être incluse dans la définition de `LambdaFun`.  
  
```vb#  
' Not valid.  
'Dim anon = New With {.Num = 4, .LambdaFun = Function() .Num > 0}  
```  
  
 **ID d’erreur :** BC36549  
  
### Pour corriger cette erreur  
  
1.  Pensez à fractionner le type anonyme en deux parties :  
  
    ```vb#  
    Dim anon1 = New With {.Num = 4}  
    Dim anon2 = New With {.LambdaFun = Function() anon1.Num > 0}  
    ' - or -  
    Dim anon3 = New With {.lambdaFun = Function(n As Integer) n > 0}  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    anon1.Num = -5  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    ```  
  
     Notez que si vous déclarez `anon1.Num` en tant que propriété `Key`, sa valeur ne peut pas être modifiée.  
  
2.  L’alternative consiste à utiliser une instruction de fonction normale pour accéder à la propriété de type anonyme :  
  
    ```vb#  
    Function testNum(ByVal n As Integer) As Boolean  
        Return n > 0  
    End Function  
    Console.WriteLine(testNum(anon1.Num))  
    ```  
  
3.  De même, vous pouvez utiliser une fonction lambda qui est définie en dehors du type anonyme :  
  
    ```vb#  
    Dim lambdaFun1 = Function() anon1.Num > 0  
    Dim lambdaFun2 = Function(n As Integer) n > 0  
    ```  
  
## Voir aussi  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)