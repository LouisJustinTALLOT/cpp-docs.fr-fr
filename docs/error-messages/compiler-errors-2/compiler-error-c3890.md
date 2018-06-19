---
title: Erreur du compilateur C3890 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3890
dev_langs:
- C++
helpviewer_keywords:
- C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc1bfbba9cfb8991491bcbb42d2e13c586c7fc26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273989"
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