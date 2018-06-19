---
title: Erreur du compilateur C3230 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3230
dev_langs:
- C++
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 494aa6a04b1ec4844e243807e103d4d106380739
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252409"
---
# <a name="compiler-error-c3230"></a>Erreur du compilateur C3230
'fonction' : l’argument de type de modèle de 'modèle' ne peut pas contenir de paramètre de type générique : 'paramètre'  
  
 Les modèles sont instanciés au moment de la compilation, mais les génériques sont instanciés au moment de l’exécution. Ainsi, il n’est pas possible de générer du code générique pouvant appeler le modèle, car celui-ci ne peut pas être instancié au moment de l’exécution quand le type générique est enfin connu.  
  
 L’exemple suivant génère l’erreur C3230 :  
  
```  
// C3230.cpp  
// compile with: /clr /LD  
template <class S>   
void f(S t);  
  
generic <class U>  
ref class C {  
   void f1(U x) {  
      f(x);   // C3230  
   }  
};  
```