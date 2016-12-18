---
title: "Erreur du compilateur CS1015 | Microsoft Docs"
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
  - "CS1015"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1015"
ms.assetid: 53179feb-e8be-41e0-bb0b-f7879e9fa613
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1015
Type objet, chaîne ou classe attendu  
  
 L’utilisateur a tenté de passer un type de données prédéfini dans un bloc [catch](../Topic/try-catch%20\(C%23%20Reference\).md). Seuls les types de données qui dérivent de <xref:System.Exception?displayProperty=fullName> peuvent être passés dans un bloc `catch`. Pour plus d’informations sur les exceptions, consultez [Instructions de gestion des exceptions](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1015 :  
  
```  
// CS1015.cs class Sample { static void Main() { try { } catch(int)   // CS1015, int is not derived from System.Exception { } } }  
```