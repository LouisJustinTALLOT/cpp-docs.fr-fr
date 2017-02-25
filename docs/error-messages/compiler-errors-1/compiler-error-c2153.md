---
title: "Erreur du compilateur C2153 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2153"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2153"
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C2153
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

les constantes hexadécimales doivent comporter au moins un chiffre hexadécimal  
  
 Les constantes hexadécimales 0x, 0X et \\x ne sont pas valides.  Au moins un chiffre hexa doit suivre x ou X.  
  
 L'exemple suivant génère l'erreur C2153 :  
  
```  
// C2153.cpp  
int main() {  
   int a= 0x;    // C2153  
   int b= 0xA;   // OK  
}  
```