---
title: "Erreur du compilateur C2246 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2246"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2246"
ms.assetid: 4f3e4f83-21f3-4256-af96-43e0bb060311
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Erreur du compilateur C2246
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificateur' : données membres static non conformes dans une classe définie localement  
  
 Un membre d’une classe, d’une structure ou d’une union avec une portée locale est déclaré `static`.  
  
 L’exemple suivant génère l’erreur C2246 :  
  
```  
// C2246.cpp // compile with: /c void func( void ) { class A { static int i; };   // C2246  i is local to func static int j;   // OK };  
```