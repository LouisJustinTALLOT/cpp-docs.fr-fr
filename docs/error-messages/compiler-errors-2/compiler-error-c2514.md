---
title: Erreur du compilateur C2514 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2514
dev_langs:
- C++
helpviewer_keywords:
- C2514
ms.assetid: 4b7085e5-6714-4261-80b7-bc72e64ab3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 255459a7ba9829b3db817662e2fc1139191b6385
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227973"
---
# <a name="compiler-error-c2514"></a>Erreur du compilateur C2514
'classe' : classe n’a aucun constructeur  
  
 La classe, structure ou union n’a aucun constructeur avec une liste de paramètres qui correspond aux paramètres utilisés pour l’instancier.  
  
 Une classe doit être complètement déclarée avant de pouvoir être instancié.  
  
 L’exemple suivant génère l’erreur C2514 :  
  
```  
// C2514.cpp  
// compile with: /c  
class f;  
  
class g {  
public:  
    g (int x);  
};  
  
class fmaker {  
   f *func1() {  
      return new f(2);   // C2514  
   }  
  
   g *func2() {  
      return new g(2);   // OK  
   }  
};   
```