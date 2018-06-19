---
title: Erreur du compilateur C3866 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3866
dev_langs:
- C++
helpviewer_keywords:
- C3866
ms.assetid: 685870af-2440-4cdf-a6cb-284a5b96ef9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da9109e35f3c79d33a4c3439aa58befdbe91068c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273710"
---
# <a name="compiler-error-c3866"></a>Erreur du compilateur C3866
liste d’arguments de fonction appel manquant  
  
 À l’intérieur d’une fonction membre non statique, un appel destructeur ou un finaliseur n’avait pas une liste d’arguments.  
  
 L’exemple suivant génère l’erreur C3866 :  
  
```  
// C3866.cpp  
// compile with: /c  
class C {  
   ~C();  
   void f() {  
      this->~C;   // C3866  
      this->~C();   // OK  
   }  
};  
```