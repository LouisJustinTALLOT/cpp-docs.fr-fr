---
title: "Erreur du compilateur CS0549 | Microsoft Docs"
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
  - "CS0549"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0549"
ms.assetid: ae965019-9dee-4f28-9e9a-6f379bd0d757
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0549
'fonction' est un nouveau membre virtuel dans une classe sealed 'classe'  
  
 Une [classe](../Topic/class%20\(C%23%20Reference\).md)[sealed](../Topic/sealed%20\(C%23%20Reference\).md) ne peut pas être utilisée comme classe de base.  Par conséquent, il est inutile d’avoir une méthode virtuelle dans une classe sealed.  
  
 L’exemple suivant génère l’erreur CS0549 :  
  
```  
// CS0549.cs // compile with: /target:library sealed public class MyClass { virtual public void TestMethod() {}   // CS0549 public void TestMethod2() {}   // OK }  
```