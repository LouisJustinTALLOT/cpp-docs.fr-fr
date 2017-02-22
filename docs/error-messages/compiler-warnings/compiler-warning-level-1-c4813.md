---
title: "Avertissement du compilateur (niveau&#160;1) C4813 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4813"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4813"
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Avertissement du compilateur (niveau&#160;1) C4813
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : une fonction friend d’une classe locale doit avoir été précédemment déclarée  
  
 Une fonction friend dans une classe interne n’a pas été déclarée dans la classe externe.  
  
 L’exemple suivant génère l’avertissement C4813 :  
  
```  
// C4813.cpp // compile with: /W1 /LD void MyClass() { // void func(); class InnerClass { friend void func();   // C4813 uncomment declaration above }; }  
```