---
title: "Erreur du compilateur C2805 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2805"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2805"
ms.assetid: c997dc56-e199-442f-b94e-ac551ec9b015
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C2805
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

nombre de paramètres insuffisant pour l'opérateur binaire 'operator opérateur'  
  
 L'opérateur binaire n'a pas de paramètre.  
  
 L'exemple suivant génère l'erreur C2805 :  
  
```  
// C2805.cpp  
// compile with: /c  
class X {  
public:  
   X operator< ( void );   // C2805 must take one parameter  
   X operator< ( X );   // OK  
};  
```