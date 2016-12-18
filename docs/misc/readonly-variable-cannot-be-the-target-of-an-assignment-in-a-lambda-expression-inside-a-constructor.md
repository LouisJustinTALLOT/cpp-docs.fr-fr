---
title: "Une variable &#39;ReadOnly&#39; ne peut pas &#234;tre la cible d’une assignation dans une expression lambda au sein d’un constructeur | Microsoft Docs"
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
  - "bc36602"
  - "vbc36602"
helpviewer_keywords: 
  - "BC36602"
ms.assetid: f96f8c79-86df-4727-bc6d-f0844da21395
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une variable &#39;ReadOnly&#39; ne peut pas &#234;tre la cible d’une assignation dans une expression lambda au sein d’un constructeur
Vous avez fait référence à une variable `ReadOnly` dans une expression lambda, ce qui n’est pas autorisé. Le code suivant génère cette erreur en envoyant `m` à la variable `ReadOnly` comme argument d’un paramètre `ByRef`.  
  
```vb#  
Class Class1 ReadOnly m As Integer Sub New() ' The use of m triggers the error. Dim f = Function() Test(m) End Sub Function Test(ByRef n As Integer) As String End Function End Class  
```  
  
 **ID d’erreur :** BC36602  
  
### Pour corriger cette erreur  
  
-   Si possible, remplacez le paramètre `n` dans la fonction `Test` par un paramètre `ByVal`, comme indiqué dans le code suivant.  
  
    ```vb#  
    Class Class1Fix1 ReadOnly m As Integer Sub New() Dim f = Function() Test(m) End Sub Function Test(ByVal n As Integer) As String End Function End Class  
    ```  
  
### Pour corriger cette erreur  
  
-   Assignez la variable `ReadOnly``m` à une variable locale dans le constructeur et utilisez la variable locale à la place de `m`, comme illustré dans le code suivant.  
  
    ```vb#  
    Class Class1Fix2 ReadOnly m As Integer Sub New() Dim temp = m Dim f = Function() Test(temp) End Sub Function Test(ByRef n As Integer) As String End Function End Class  
    ```  
  
## Voir aussi  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [ReadOnly](../Topic/ReadOnly%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)