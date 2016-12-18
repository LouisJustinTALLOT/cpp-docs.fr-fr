---
title: "Erreur du compilateur CS0548 | Microsoft Docs"
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
  - "CS0548"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0548"
ms.assetid: c4d34da7-0b4a-4312-ac7f-46db100e43c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0548
'property' : la propriété ou l’indexeur doit posséder au moins un accesseur  
  
 Une propriété doit avoir au moins une méthode d’accesseur \(get ou set\).  
  
 Pour plus d’informations, consultez [Utilisation de propriétés](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0548.  
  
```  
// CS0548.cs // compile with: /target:library public class b { public int MyProp {}   // CS0548 public int MyProp2   // OK { get { return 0; } set {} } }  
```