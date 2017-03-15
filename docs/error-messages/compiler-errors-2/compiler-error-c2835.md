---
title: "Erreur du compilateur C2835 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2835"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2835"
ms.assetid: 41c70630-983f-4da2-8342-513cf48b0519
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Erreur du compilateur C2835
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

une conversion définie par l'utilisateur 'type' n'accepte pas de paramètres formels  
  
 Les conversions définies par l'utilisateur ne peuvent pas accepter de paramètres formels.  
  
 L'exemple suivant génère l'erreur C2835 :  
  
```  
// C2835.cpp  
class A {  
public:  
   char v_char;  
  
   A() {   
      v_char = 'A';   
   };  
   operator char(char a) {   // C2835  
   // try the following line instead  
   // operator char() {     
      return v_char + 1;   
   };  
};  
  
int main() {  
   A a;  
}  
```