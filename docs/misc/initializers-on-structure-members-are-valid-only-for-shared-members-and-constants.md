---
title: "Les initialiseurs pour les membres de structure ne sont valides que pour les membres et constantes &#39;Shared&#39; | Microsoft Docs"
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
  - "bc31049"
  - "vbc31049"
helpviewer_keywords: 
  - "BC31049"
ms.assetid: 8356978e-7f84-4932-be0f-dda005c9f8ca
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les initialiseurs pour les membres de structure ne sont valides que pour les membres et constantes &#39;Shared&#39;
Une variable de membre de structure a été initialisée dans le cadre de sa déclaration.  
  
 **ID d’erreur :** BC31049  
  
### Pour corriger cette erreur  
  
-   Utilisez une constante plutôt qu’une variable.  
  
-   Ajoutez un constructeur paramétrable à la structure. Exemple :  
  
    ```  
    Structure TestStruct Public t As Integer Sub New(ByVal Tval As Integer) t = Tval End Sub End Structure  
    ```  
  
## Voir aussi  
 [How to: Declare a Structure](../Topic/How%20to:%20Declare%20a%20Structure%20\(Visual%20Basic\).md)   
 [Constants and Enumerations](../Topic/Constants%20and%20Enumerations%20in%20Visual%20Basic.md)