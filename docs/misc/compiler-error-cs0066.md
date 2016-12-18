---
title: "Erreur du compilateur CS0066 | Microsoft Docs"
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
  - "CS0066"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0066"
ms.assetid: 9b50b49b-78b8-4562-8839-d59e5edbec6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0066
'event' : l’événement doit être de type délégué  
  
 Le mot clé de l’événement nécessite un type [délégué](../Topic/delegate%20\(C%23%20Reference\).md). Pour plus d’informations, consultez [Événements](../Topic/Events%20\(C%23%20Programming%20Guide\).md) et [Délégués](../Topic/Delegates%20\(C%23%20Programming%20Guide\).md).  
  
 L’exemple suivant génère l’erreur CS0066 :  
  
```  
// CS0066.cs using System; public class EventHandler { } // to fix the error, remove the event declaration and the // EventHandler class declaration, and uncomment the following line // public delegate void EventHandler(); public class a { public event EventHandler Click;   // CS0066 private void TestMethod() { if (Click != null) Click(); } public static void Main() { } }  
```