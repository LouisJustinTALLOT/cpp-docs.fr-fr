---
title: "Avertissement du compilateur (niveau 3) C4633 | Microsoft Docs"
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
  - "C4633"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4633"
ms.assetid: 6d76f268-ba8c-448b-8e83-b903a18b583b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Avertissement du compilateur (niveau 3) C4633
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

commentaire de document XML 'cible' : erreur : raison  
  
 Un nom passé à la balise [\<param\>](../../ide/param-visual-cpp.md) ne fut pas détecté par le compilateur.  
  
 L'exemple suivant génère l'erreur C4633 :  
  
```  
// C4633.cpp  
// compile with: /clr /doc /LD /W3  
  
/// Text for class MyClass.  
public ref class MyClass {  
   // C4633 remove line for Int3  
   /// <param name="Int1">Used to indicate status.</param>  
   /// <param name="Int3">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
      Int1 = 0;  
      Int1++;  
   }  
};  
```