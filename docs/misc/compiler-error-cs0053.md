---
title: "Erreur du compilateur CS0053 | Microsoft Docs"
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
  - "CS0053"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0053"
ms.assetid: 62a96ef4-e8d2-44d0-9d39-5cd7a38efe52
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0053
Accessibilité incohérente : le type de propriété 'type' est moins accessible que la propriété 'propriété'  
  
 Une construction publique doit retourner un objet accessible publiquement. Pour plus d'informations, consultez [Modificateurs d'accès](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md).  
  
 L’exemple suivant génère l’erreur CS0053 :  
  
```  
// CS0053.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public class MyClass2 { public MyClass myProperty   // CS0053 { get { return new MyClass(); } set { } } } public class MyClass3 { public static void Main() { } }  
```