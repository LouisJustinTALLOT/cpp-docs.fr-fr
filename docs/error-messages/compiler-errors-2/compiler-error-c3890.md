---
title: Erreur du compilateur C3890 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3890
dev_langs:
- C++
helpviewer_keywords:
- C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3f98846bc8a361bd03d453f2115e2063f37423f0
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3890"></a>Erreur du compilateur C3890
'var' : vous ne pouvez pas prendre l’adresse d’une donnée membre littérale  
  
 Une donnée membre littérale existe sur le tas de garbage collection.  Un objet sur le tas de garbage collection peut être déplacé, afin de prendre l’adresse n’est pas utile.  
  
 L’exemple suivant génère l’erreur C3890 :  
  
```  
// C3890.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   int p = &Y1::staticConst;   // C3890  
   int p2 = Y1::staticConst;   // OK  
}  
```
