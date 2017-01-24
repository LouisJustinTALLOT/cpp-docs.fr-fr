---
title: "Avertissement du compilateur (niveau 1) C4624 | Microsoft Docs"
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
  - "C4624"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4624"
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Avertissement du compilateur (niveau 1) C4624
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'classe dérivée' : le destructeur a été défini de manière implicite comme supprimé car un destructeur de la classe de base est inaccessible ou supprimé  
  
 Un destructeur n'était pas accessible ou était supprimé dans une classe de base et n'a donc pas été généré pour une classe dérivée.  Toute tentative pour créer un objet de ce type dans la pile provoquera une erreur du compilateur.  
  
 L'exemple suivant génère l'erreur C4624 et montre comment la corriger :  
  
```  
// C4624.cpp  
// compile with: /W1 /c  
class B {  
// Uncomment the following line to fix.  
// public:  
   ~B();  
};  
  
class D : public B {};   // C4624 B's destructor not public  
```