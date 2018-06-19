---
title: Erreur du compilateur C2245 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2245
dev_langs:
- C++
helpviewer_keywords:
- C2245
ms.assetid: 08aaeadf-10ec-485a-b2a6-6e775289082b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c9328c65ce722ea8b1668235810102204ac5512
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170958"
---
# <a name="compiler-error-c2245"></a>Erreur du compilateur C2245
fonction membre 'function' inexistante spécifiée en tant que friend (la signature de la fonction membre ne correspond à aucune surcharge)  
  
 Une fonction spécifiée comme friend est introuvable par le compilateur.  
  
 L’exemple suivant génère l’erreur C2245 :  
  
```  
// C2245.cpp  
// compile with: /c  
class B {  
   void f(int i);  
};  
  
class A {  
   int m_i;  
   friend void B::f(char);   // C2245  
   // try the following line instead  
   // friend void B::f(int);  
};  
  
void B::f(int i) {  
   A a;  
   a.m_i = 0;  
}  
```