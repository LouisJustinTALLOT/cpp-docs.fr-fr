---
title: "Erreur du compilateur C3363 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3363"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3363"
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C3363
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 'typeid' applicable seulement à un type  
  
 L’opérateur [typeid](../../windows/typeid-cpp-component-extensions.md) a été utilisé incorrectement.  
  
## Exemple  
 L’exemple suivant génère l’erreur C3363.  
  
```  
// C3363.cpp // compile with: /clr int main() { System::typeid;   // C3363 }  
```