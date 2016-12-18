---
title: "Erreur du compilateur&#160;C2046 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2046"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2046"
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur&#160;C2046
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

instruction case non conforme  
  
 Le mot clé `case` ne peut être spécifié que dans une instruction `switch`.  
  
 L’exemple suivant génère l’erreur C2046 :  
  
```  
// C2046.cpp int main() { case 0:   // C2046 }  
```  
  
 Solution possible :  
  
```  
// C2046b.cpp int main() { int i = 0; switch(i) { case 0: break; default: break; } }  
```