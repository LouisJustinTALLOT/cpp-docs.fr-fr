---
title: "Erreur du compilateur C2645 | Microsoft Docs"
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
  - "C2645"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2645"
ms.assetid: 6609c2fa-c3b2-4a6b-8e8d-58fb52f67175
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C2645
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

aucun nom qualifié pour un pointeur vers un membre \(trouvé ':: \*'\)  
  
 La déclaration d'un pointeur vers un membre ne spécifie pas de classe.  
  
 L'exemple suivant génère l'erreur C2645 :  
  
```  
// C2645.cpp  
class A {};  
int main() {  
   int B::* bp;   // C2645 B not defined  
   int A::* ap;   // OK  
}  
```