---
title: "Avertissement du compilateur (niveau 1) C4047 | Microsoft Docs"
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
  - "C4047"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4047"
ms.assetid: b75ad6fb-5c93-4434-a85f-c4083051a5de
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Avertissement du compilateur (niveau 1) C4047
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'opérateur' : les niveaux d'indirection de 'identificateur1' et de 'identificateur2' sont différents  
  
 Un pointeur peut pointer vers une variable \(un niveau d'indirection\), vers un autre pointeur qui pointe vers une variable \(deux niveaux d'indirection\), et ainsi de suite.  
  
## Exemple  
 L'exemple suivant génère l'erreur C4047 :  
  
```  
// C4047.c  
// compile with: /W1  
  
int main() {  
   char **p = 0;   // two levels of indirection  
   char *q = 0;   // one level of indirection  
  
   char *p2 = 0;   // one level of indirection  
   char *q2 = 0;   // one level of indirection  
  
   p = q;   // C4047  
   p2 = q2;  
}  
```  
  
## Exemple  
 L'exemple suivant génère l'erreur C4047 :  
  
```  
// C4047b.c  
// compile with: /W1  
#include <stdio.h>  
  
int main() {  
   int i;  
   FILE *myFile = NULL;  
   errno_t  err = 0;  
   char file_name[256];  
   char *cs = 0;  
  
   err = fopen_s(&myFile, "C4047.txt", "r");  
   if ((err != 0) || (myFile)) {  
      printf_s("fopen_s failed!\n");  
      exit(-1);  
    }  
   i = fgets(file_name, 256, myFile);   // C4047  
   cs = fgets(file_name, 256, myFile);   // OK  
}  
```