---
title: "&#39;&lt;nom_m&#233;thode&gt;&#39; n’est pas accessible dans ce contexte, car le type de retour n’est pas accessible | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36665"
  - "vbc36666"
  - "bc36666"
  - "vbc36665"
helpviewer_keywords: 
  - "BC36666"
  - "BC36665"
ms.assetid: 8f29eb7e-351f-486c-9d1f-3556cc11b7c5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_m&#233;thode&gt;&#39; n’est pas accessible dans ce contexte, car le type de retour n’est pas accessible
Vous avez appelé une fonction dont le type de retour n’est pas accessible à partir de l’instruction appelante. Par exemple, dans le code suivant, l’appel de `Main` à `PublicMethod` échoue car le type de retour, `PrivateType`, est déclaré avec le modificateur d’accès `Private` dans la classe `TestClass`. Ainsi, le contexte dans lequel `PrivateType` est accessible est limité à `TestClass`.  
  
```vb#  
Class TestClass  
  
    Dim pT As New PrivateType  
  
    Private Class PrivateType  
    End Class  
  
    '' A corresponding error is returned in this line: 'PublicMethod   
    '' cannot expose 'PrivateType' in namespace 'ConsoleApplication1'   
    '' through class 'TestClass'.  
    'Public Function PublicMethod() As PrivateType  
    '    Return Nothing  
    'End Function  
  
End Class  
  
Module Module1  
  
    Sub Main()  
  
        Dim tc As TestClass  
        '' This error occurs here, because the data type returned by   
        '' PublicMethod()is declared Private in class TestClass and   
        '' cannot be accessed from here.  
        'Console.WriteLine(tc.PublicMethod())  
  
    End Sub  
  
End Module  
```  
  
 **ID d’erreur :** BC36665 et BC36666  
  
### Pour corriger cette erreur  
  
-   Si la définition de type est accessible, remplacez le modificateur d’accès `Private` par `Public`.  
  
-   Modifiez le type de retour de la fonction si vous y avez accès.  
  
-   Écrivez une méthode ou une méthode d’extension qui retourne un type accessible.  
  
## Voir aussi  
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)