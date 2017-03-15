---
title: "Erreur du compilateur C2053 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2053"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2053"
ms.assetid: 13324c85-13a8-4996-bd42-a31bfe7ff80f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Erreur du compilateur C2053
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificateur' : incompatibilité de chaînes étendues  
  
 La chaîne étendue est assignée à un type incompatible.  
  
 L'exemple suivant génère l'erreur C2053 :  
  
```  
// C2053.c  
int main() {  
   char array[] = L"Rika";   // C2053  
}  
```