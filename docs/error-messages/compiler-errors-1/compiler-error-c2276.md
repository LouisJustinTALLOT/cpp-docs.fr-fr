---
title: Erreur du compilateur C2276 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2276
dev_langs:
- C++
helpviewer_keywords:
- C2276
ms.assetid: 62005ad9-6cb9-4b1f-965d-b875adaf695e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb5d0b8b533567884d574cc81ef74010beeacf55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172623"
---
# <a name="compiler-error-c2276"></a>Erreur du compilateur C2276
'opérateur' : opération non conforme sur l’expression de fonction membre liée  
  
 Le compilateur a détecté un problème avec la syntaxe pour créer un pointeur vers membre.  
  
 L’exemple suivant génère l’erreur C2276 :  
  
```  
// C2276.cpp  
class A {  
public:  
   int func(){return 0;}  
} a;  
  
int (*pf)() = &a.func;   // C2276  
// try the following line instead  
// int (A::*pf3)() = &A::func;  
  
class B {  
public:  
   void mf() {  
      &this -> mf;   // C2276  
      // try the following line instead  
      // &B::mf;  
   }  
};  
  
int main() {  
   A a;  
   &a.func;   // C2276  
   // try the following line instead  
   // &A::func;  
}  
```