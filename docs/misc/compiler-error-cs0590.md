---
title: "Erreur du compilateur CS0590 | Microsoft Docs"
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
  - "CS0590"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0590"
ms.assetid: 6df9461f-2de6-4032-b18f-96121db1e4af
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0590
Les opérateurs définis par l'utilisateur ne peuvent pas retourner void  
  
 L’objectif d’un opérateur défini par l’utilisateur est de retourner un objet.  
  
 L’exemple suivant génère l’erreur CS0590 :  
  
```  
// CS0590.cs namespace x { public class a { public static void operator+(a A1, a A2)   // CS0590 { } // try the following user-defined operator /* public static a operator+(a A1, a A2) { return A2; } */ public static int Main() { return 1; } } }  
```