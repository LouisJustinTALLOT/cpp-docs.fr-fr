---
title: Erreur du compilateur C2135 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2135
dev_langs:
- C++
helpviewer_keywords:
- C2135
ms.assetid: aa360d22-4f79-4de1-b384-93cadd10975f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d76a388ad34eb44d8c4bba0d0663115048ad41f4
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2135"></a>Erreur du compilateur C2135
'opérateur de bits' : opération sur les champs de bits non conforme  
  
 L’opérateur address-of (`&`) ne peut pas être appliqué à un champ de bits.  
  
 L’exemple suivant génère l’erreur C2135 :  
  
```  
// C2135.cpp  
struct S {  
   int i : 1;  
};  
  
struct T {  
   int j;  
};  
int main() {  
   &S::i;   // C2135 address of a bit field  
   &T::j;   // OK  
}  
```
