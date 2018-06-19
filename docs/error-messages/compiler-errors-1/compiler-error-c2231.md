---
title: Erreur du compilateur C2231 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2231
dev_langs:
- C++
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 775d559c332e37e91be2b89b10e046e0f8c1abd7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168553"
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