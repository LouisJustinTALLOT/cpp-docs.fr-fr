---
title: "Erreur du compilateur C2786 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2786"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2786"
ms.assetid: 6676d8c0-86dd-4a39-bdda-b75a35f4d137
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Erreur du compilateur C2786
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : opérande non valide pour \_\_uuidof  
  
 L'opérateur [\_\_uuidof](../../cpp/uuidof-operator.md) accepte un type défini par l'utilisateur avec un GUID associé ou un objet d'un type défini par l'utilisateur.  Causes possibles :  
  
1.  L'argument n'est pas défini par l'utilisateur.  
  
2.  `__uuidof` ne peut extraire le GUID de l'argument.  
  
 L'exemple suivant génère l'erreur C2786 :  
  
```  
// C2786.cpp  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
  
int main() {  
   __uuidof(int);   // C2786  
   __uuidof(int *);   // C2786  
   __uuidof(A **);   // C2786  
  
   // no error  
   __uuidof(A);  
   __uuidof(A *);  
   __uuidof(A &);  
   __uuidof(A[]);  
  
   int i;  
   int *pi;  
   A **ppa;  
  
   __uuidof(i);      // C2786  
   __uuidof(pi);     // C2786  
   __uuidof(ppa);    // C2786  
}  
```