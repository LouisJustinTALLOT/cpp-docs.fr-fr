---
title: "Erreur du compilateur C2687 | Microsoft Docs"
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
  - "C2687"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2687"
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C2687
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : la déclaration d'exception ne peut pas être 'void' ou désigner un type incomplet ou un pointeur ou une référence d'un type incomplet  
  
 Pour qu'un type puisse faire partie d'une déclaration d'exception, il doit être défini et non void.  
  
 L'exemple suivant génère l'erreur C2687 :  
  
```  
// C2687.cpp  
class C;  
  
int main() {  
   try {}  
   catch (C) {}   // C2687 error  
}  
```  
  
 Résolution possible :  
  
```  
// C2687b.cpp  
// compile with: /EHsc  
class C {};  
  
int main() {  
   try {}  
   catch (C) {}  
}  
```