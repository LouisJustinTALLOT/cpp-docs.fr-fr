---
title: "Erreur du compilateur CS0245 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0245"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0245"
ms.assetid: 3f2beb2f-a510-4568-9d11-bb1f65066acd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0245
Impossible d’appeler directement des destructeurs et object.Finalize. Appelez IDisposable.Dispose s’il est disponible.  
  
 Pour plus d’informations, consultez [Programmation d’un garbage collection](../Topic/Garbage%20Collection.md) et [Destructeurs](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md).  
  
 L’exemple suivant génère l’erreur CS0245 :  
  
```  
// CS0245.cs using System; using System.Collections; class MyClass // : IDisposable { /* public void Dispose() { // cleanup code goes here } */ void m() { this.Finalize();   // CS0245 // this.Dispose(); } public static void Main() { } }  
```