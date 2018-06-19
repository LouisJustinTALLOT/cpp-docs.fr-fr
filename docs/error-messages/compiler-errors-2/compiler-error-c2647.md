---
title: Erreur du compilateur C2647 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2647
dev_langs:
- C++
helpviewer_keywords:
- C2647
ms.assetid: 1034589e-bc3e-41a6-831f-2a1a4b8a2500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca5de79746876a60cc9a64c4bf8f91e468b4d379
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232618"
---
# <a name="compiler-error-c2647"></a>Erreur du compilateur C2647
'opérateur' : Impossible de déréférencer un 'type1' sur un 'type2'  
  
 L’opérande de gauche d’un opérateur pointeur vers membre ( `->*` ou `.*` ) ne peut pas être converti en un type se rapportant à l’opérateur de droite.  
  
 L’exemple suivant génère C2647 :  
  
```  
// C2647.cpp  
class C {};  
class D {};  
  
int main() {  
   D d, *pd;  
   C c, *pc = 0;  
   int C::*pmc = 0;  
   pd->*pmc = 0;   // C2647  
   d.*pmc = 0;   // C2647  
  
   // OK  
   pc->*pmc = 0;  
   c.*pmc = 0;  
}  
```