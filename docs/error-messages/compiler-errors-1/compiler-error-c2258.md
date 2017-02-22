---
title: "Erreur du compilateur C2258 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2258"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2258"
ms.assetid: 105eaa87-befb-4ecb-9a3f-e09e14d2f5bf
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C2258
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

syntaxe pure non conforme, doit être '\= 0'  
  
 Une fonction virtuelle pure est déclarée avec une syntaxe incorrecte.  
  
 L’exemple suivant génère l’erreur C2258 :  
  
```  
// C2258.cpp // compile with: /c class A { public: void virtual func1() = 1; // C2258 void virtual func2() = 0;   // OK };  
```