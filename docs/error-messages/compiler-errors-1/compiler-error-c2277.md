---
title: "Erreur du compilateur C2277 | Microsoft Docs"
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
  - "C2277"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2277"
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C2277
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificateur' : impossible de récupérer l'adresse de cette fonction membre  
  
 Vous ne pouvez pas prendre l'adresse d'une fonction membre.  
  
 L'exemple suivant génère l'erreur C2277 :  
  
```  
// C2277.cpp  
class A {  
public:  
   A();  
};  
(*pctor)() = &A::A;   // C2277   
```