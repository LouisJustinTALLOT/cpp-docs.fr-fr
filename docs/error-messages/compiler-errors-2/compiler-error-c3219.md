---
title: "Erreur du compilateur C3219 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3219"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3219"
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Erreur du compilateur C3219
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'param' : le paramètre générique ne peut pas être limité par plusieurs non\-interfaces : 'class'  
  
 Il n’est pas correct de contraindre un paramètre générique par deux classes managées ou plus.  
  
 L’exemple suivant génère l’erreur C3219 :  
  
```  
// C3219.cpp // compile with: /clr ref class A {}; ref class B {}; generic <class T> where T : A, B ref class E {};   // C3219  
```  
  
 L’exemple suivant illustre une résolution possible :  
  
```  
// C3219b.cpp // compile with: /clr /c ref class A {}; interface struct C {}; generic <class T> where T : A ref class E {};  
```