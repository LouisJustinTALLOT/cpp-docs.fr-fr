---
title: "Erreur du compilateur CS1518 | Microsoft Docs"
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
  - "CS1518"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1518"
ms.assetid: 26e0870d-fe91-4c66-b3f8-ed2b074c964e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1518
Class, delegate, enum, interface ou struct attendu  
  
 Une déclaration qui n’est pas prise en charge dans un [espace de noms](../Topic/namespace%20\(C%23%20Reference\).md) a été trouvée. Dans un espace de noms, le compilateur accepte uniquement des classes, des structures, des enums, des interfaces, des espaces de noms et des délégués.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1518 :  
  
```  
// CS1518.cs namespace x { sealed class c1 {};      // OK namespace f2 {};         // OK sealed f3 {};            // CS1518 }  
```