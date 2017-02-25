---
title: "Erreur du compilateur C2718 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2718"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2718"
ms.assetid: 78cc71f8-c142-46fc-9aed-970635d74f0c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C2718
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'paramètre' : le paramètre actuel avec \_\_declspec\(align\('nombre'\)\) ne sera pas aligné  
  
 Le modificateur [align](../../cpp/align-cpp.md) `__declspec` n'est pas autorisé dans les paramètres de fonction.  
  
 L'exemple suivant génère l'erreur C2718 :  
  
```  
// C2718.cpp  
typedef struct __declspec(align(32)) AlignedStruct  {   
   int i;   
} AlignedStruct;  
  
void f2(int i, ...);  
  
void f4() {  
   AlignedStruct as;  
  
   f2(0, as);   // C2718, actual parameter is aligned  
}  
```