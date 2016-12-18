---
title: "Erreur du compilateur CS0101 | Microsoft Docs"
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
  - "CS0101"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0101"
ms.assetid: edb5246b-c16b-4845-bb2d-0ef769d014c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0101
L’espace de noms 'namespace' contient déjà une définition pour 'type'  
  
 Un [espace de noms](../Topic/namespace%20\(C%23%20Reference\).md) a des identificateurs en double. Renommez ou supprimez l’un des identificateurs en double. Pour plus d'informations, consultez [Espaces de noms](../Topic/Namespaces%20\(C%23%20Programming%20Guide\).md)  
  
 L’exemple suivant génère l’erreur CS0101 :  
  
```  
// CS0101.cs namespace MyNamespace { public class MyClass { static public void Main() { } } public class MyClass   // CS0101 { } }  
```