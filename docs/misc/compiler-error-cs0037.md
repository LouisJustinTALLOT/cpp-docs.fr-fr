---
title: "Erreur du compilateur CS0037 | Microsoft Docs"
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
  - "CS0037"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0037"
ms.assetid: 1d34a71e-10a0-4fa8-9b94-343e69428c61
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0037
Impossible de convertir une valeur null en 'type', car il s’agit d’un type valeur qui n’autorise pas les valeurs null  
  
 Le compilateur ne peut pas assigner la valeur null à un type valeur ; la valeur null ne peut être assignée qu’à un [type référence](../Topic/Reference%20Types%20\(C%23%20Reference\).md) ou à un type Nullable.[struct](../Topic/struct%20\(C%23%20Reference\).md) est un type valeur. Pour plus d'informations, consultez [Types Nullable](../Topic/Nullable%20Types%20\(C%23%20Programming%20Guide\).md).  
  
 L’exemple suivant génère l’erreur CS0037 :  
  
```  
// CS0037.cs public struct s { } class a { public static void Main() { int i = null;   // CS0037 s ss = null;    // CS0037 } }  
```