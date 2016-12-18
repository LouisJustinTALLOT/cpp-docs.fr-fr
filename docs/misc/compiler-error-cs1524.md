---
title: "Erreur du compilateur CS1524 | Microsoft Docs"
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
  - "CS1524"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1524"
ms.assetid: a7b80bbc-a2de-4718-b0f0-4c9526726525
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1524
Catch ou finally attendu  
  
 Un bloc `try` doit être suivi d’un bloc `catch` ou d’un bloc `finally`.  
  
 Pour plus d’informations sur les exceptions, consultez [Instructions de gestion des exceptions](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1524 :  
  
```  
// CS1524.cs class x { public static void Main() { try { // Code here } catch { } try { // Code here } finally { } try { // Code here } }     // CS1524, missing catch or finally }  
```