---
title: Erreur du compilateur C2689 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2689
dev_langs:
- C++
helpviewer_keywords:
- C2689
ms.assetid: b5216fba-524d-4194-9168-26e9dc5210ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 973f8a007080d728a07afae8818ffa2c7bd8ed4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231635"
---
# <a name="compiler-error-c2689"></a>Erreur du compilateur C2689
'fonction' : une fonction friend ne peut pas être définie dans une classe locale  
  
 Vous pouvez déclarer mais pas définir une fonction friend dans une classe locale.  
  
 L’exemple suivant génère l’erreur C2689 :  
  
```  
// C2689.cpp  
// compile with: /c  
void g() {  
   void f2();  
   class X {  
      friend void f2(){}   // C2689  
      friend void f2();   // OK  
   };  
}  
```