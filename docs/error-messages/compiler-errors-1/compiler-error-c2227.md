---
title: Erreur du compilateur C2227 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2227
dev_langs:
- C++
helpviewer_keywords:
- C2227
ms.assetid: d470e8b8-7e15-468b-84fa-37d1a0132271
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a23d055dec45693f292978039c5c5108e34e7a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169086"
---
# <a name="compiler-error-c2227"></a>Erreur du compilateur C2227
la partie gauche de '->membre' doit pointer vers un type class/struct/union/générique  
  
 L’opérande à gauche de `->` n’est pas un pointeur vers une classe, structure ou union.  
  
 L’exemple suivant génère l’erreur C2227 :  
  
```  
// C2227.cpp  
int *pInt;  
struct S {  
public:  
    int member;  
} s, *pS = &s;  
  
int main() {  
   pInt->member = 0;   // C2227 pInt points to an int  
   pS->member = 0;   // OK  
}  
```