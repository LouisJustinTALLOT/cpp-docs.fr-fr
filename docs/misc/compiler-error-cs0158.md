---
title: "Erreur du compilateur CS0158 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0158"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0158"
ms.assetid: 88ac61a9-ce55-4272-9141-0873765a7034
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0158
L’étiquette 'étiquette' cache une autre étiquette qui porte le même nom dans une portée contenue  
  
 Une étiquette dans une portée interne cache une étiquette du même nom dans une portée externe. Pour plus d'informations, consultez [goto](../Topic/goto%20\(C%23%20Reference\).md).  
  
 L’exemple suivant génère l’erreur CS0158 :  
  
```  
// CS0158.cs namespace MyNamespace { public class MyClass { public static void Main() { goto lab1; lab1: { lab1: goto lab1;   // CS0158 } } } }  
```