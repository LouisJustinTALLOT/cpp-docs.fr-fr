---
title: Erreur du compilateur C2319 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2319
dev_langs:
- C++
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fa9d2c0aeae56ea678a9f2aa2cbfabfc43e71c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222392"
---
# <a name="compiler-error-c2319"></a>Erreur du compilateur C2319
'try/catch' doit être suivi(e) d’une instruction composée. Accolade '{' manquante  
  
 Un bloc `try` ou `catch` est introuvable après l’instruction `try` ou `catch` . Le bloc doit être entre accolades.  
  
 L’exemple suivant génère l’erreur C2319 :  
  
```  
// C2319.cpp  
// compile with: /EHsc  
#include <eh.h>  
class C {};  
int main() {  
   try {  
      throw "ooops!";  
   }  
   catch( C ) ;    // C2319  
   // try the following line instead  
   // catch( C ) {}  
}  
```