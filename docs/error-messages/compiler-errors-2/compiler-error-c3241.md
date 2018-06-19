---
title: Erreur du compilateur C3241 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3241
dev_langs:
- C++
helpviewer_keywords:
- C3241
ms.assetid: 2ca14879-bba0-4a23-b22a-72cfff92d6a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1a3849dd404c82811eee9176fe87861cfd4a435
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250308"
---
# <a name="compiler-error-c3241"></a>Erreur du compilateur C3241
'méthode' : cette méthode n’a pas été introduite par 'interface'  
  
 Lorsque vous substituez explicitement une fonction, la signature de fonction doit correspondre exactement à la déclaration de la fonction que vous substituez.  
  
 L’exemple suivant génère l’erreur C3241 :  
  
```  
// C3241.cpp  
#pragma warning(disable:4199)  
  
__interface IX12A {  
   void mf();  
};  
  
__interface IX12B {  
   void mf(int);  
};  
  
class CX12 : public IX12A, public IX12B { // C3241  
   void IX12A::mf(int);  
};  
```