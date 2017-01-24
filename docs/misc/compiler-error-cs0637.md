---
title: "Erreur du compilateur CS0637 | Microsoft Docs"
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
  - "CS0637"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0637"
ms.assetid: 02f6964c-0fcc-4f81-8ebb-0330aecdde19
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0637
L'attribut FieldOffset n'est pas autorisé sur des champs static ou const  
  
 L’attribut [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic) ne peut pas être utilisé sur les champs marqués avec [static](../Topic/static%20\(C%23%20Reference\).md) ou [const](../Topic/const%20\(C%23%20Reference\).md).  
  
 L’exemple suivant génère l’erreur CS0637 :  
  
```  
// CS0637.cs using System; using System.Runtime.InteropServices; [StructLayout(LayoutKind.Explicit)] public class MainClass { [FieldOffset(3)]   // CS0637 public static int i; public static void Main () { } }  
```