---
title: "Erreur du compilateur CS0558 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0558"
ms.assetid: af63b9ba-2790-4362-a49d-b69a5292a555
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0558
L’opérateur défini par l’utilisateur 'opérateur' doit être déclaré static et public  
  
 Les deux [modificateurs](../Topic/Modifiers%20\(C%23%20Reference\).md) d’accès **static** et **public** doivent être spécifiés sur les opérateurs définis par l’utilisateur.  
  
 L’exemple suivant génère l’erreur CS0558 :  
  
```  
// CS0558.cs namespace x { public class ii { public class iii { static implicit operator int(iii aa)   // CS0558, add public { return 0; } } public static void Main() { } } }  
```