---
title: "Avertissement du compilateur (niveau&#160;1) CS0168 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0168"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0168"
ms.assetid: 6f5b7fe3-1e91-462f-8a73-b931327ab3f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS0168
La variable 'var' est assignée, mais sa valeur n’est jamais utilisée  
  
 Le compilateur vous avertit quand une variable est déclarée mais inutilisée.  
  
 L’exemple suivant génère deux avertissements CS0168 :  
  
```  
// CS0168.cs // compile with: /W:3 public class clx { public int i; } public class clz { public static void Main() { int j = 0;   // CS0168, uncomment the following line // j++; clx a;       // CS0168, try the following line instead // clx a = new clx(); } }  
```