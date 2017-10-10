---
title: Erreur du compilateur C2353 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2353
dev_langs:
- C++
helpviewer_keywords:
- C2353
ms.assetid: d57f8f77-d9b1-4bba-a940-87ec269ad183
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a2bb8210a1b0d2eb2150e9916b1230180cb72420
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2353"></a>Erreur du compilateur C2353
spécification d’exception n’est pas autorisée.  
  
 Les spécifications d’exceptions ne sont pas autorisées sur les fonctions membres de classes managées.  
  
 L’exemple suivant génère l’erreur C2353 :  
  
```  
// C2353.cpp  
// compile with: /clr /c  
ref class X {  
   void f() throw(int);   // C2353  
   void f();   // OK  
};  
```
