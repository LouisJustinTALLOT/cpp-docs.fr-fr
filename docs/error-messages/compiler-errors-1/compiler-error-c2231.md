---
title: Erreur du compilateur C2231 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2231
dev_langs:
- C++
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 48aac0a2101b6c9cf02c29fe30ea12717b996087
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2231"></a>Erreur du compilateur C2231
'.' : opérande gauche pointe vers 'clé-classe', utilisez '->'  
  
 L’opérande à gauche de l’opération de sélection de membres (.) est un pointeur au lieu d’une classe, structure ou union.  
  
 L’exemple suivant génère l’erreur C2231 :  
  
```  
// C2231.c  
struct S {  
   int member;  
} s, *ps = &s;  
int main() {  
   ps.member = 0;   // C2231  
  
   // OK  
   ps->member = 0;   // crash  
   s.member = 0;  
}  
```
