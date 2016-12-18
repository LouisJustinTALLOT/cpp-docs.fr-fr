---
title: "Erreur du compilateur CS0073 | Microsoft Docs"
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
  - "CS0073"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0073"
ms.assetid: 579ae534-59ab-4fc5-ad7e-f87639f3f9cd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0073
Un accesseur add ou remove doit avoir un corps  
  
 Un mot clé **add** ou **remove** dans une définition d’[événement](../Topic/event%20\(C%23%20Reference\).md) doit avoir un corps. Pour plus d'informations, consultez [Événements](../Topic/Events%20\(C%23%20Programming%20Guide\).md).  
  
 L’exemple suivant génère l’erreur CS0073 :  
  
```  
// CS0073.cs delegate void del(); class Test { public event del MyEvent { add;   // CS0073 // try the following lines instead // add // { //    MyEvent += value; // } remove { MyEvent -= value; } } public static void Main() { } }  
```