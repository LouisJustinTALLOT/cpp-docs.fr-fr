---
title: "Avertissement du compilateur (niveau 4) C4245 | Microsoft Docs"
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
  - "C4245"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4245"
ms.assetid: 85083d53-9cc2-4d12-b58c-6dad28f15cbe
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Avertissement du compilateur (niveau 4) C4245
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'conversion' : conversion de 'type1 en 'type2', incompatibilité signed\/unsigned  
  
 Vous avez tenté de convertir une constante de type **const** signée de valeur négative en un type `unsigned`.  
  
 L'exemple suivant génère l'erreur C4245 :  
  
```  
// C4245.cpp  
// compile with: /W4 /c  
const int i = -1;  
unsigned int j = i; // C4245  
  
const int k = 1;  
unsigned int l = k; // okay  
  
int m = -1;  
unsigned int n = m; // okay  
  
void Test(size_t i) {}  
  
int main() {  
   Test( -19 );   // C4245  
}  
```