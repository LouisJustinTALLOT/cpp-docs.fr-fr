---
title: "Erreur du compilateur CS0531 | Microsoft Docs"
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
  - "CS0531"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0531"
ms.assetid: 54c2a98b-84e3-481a-a934-7cd6dffa7677
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0531
'membre' : les membres d’interface ne peuvent pas avoir de définition  
  
 Les méthodes déclarées dans une [interface](../Topic/interface%20\(C%23%20Reference\).md) doivent être implémentées dans une classe qui en hérite et non dans l’interface elle\-même.  
  
 L’exemple suivant génère l’erreur CS0531 :  
  
```  
// CS0531.cs namespace x { public interface clx { int xclx()   // CS0531, cannot define xclx // Try the following declaration instead: // int xclx(); { return 0; } } public class cly { public static void Main() { } } }  
```