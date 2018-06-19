---
title: Erreur du compilateur C2272 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2272
dev_langs:
- C++
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e969e7cadadf1102dadfb8089a847046731b568f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171765"
---
# <a name="compiler-error-c2272"></a>Erreur du compilateur C2272
'fonction' : modificateurs non autorisés sur les fonctions membres static  
  
 A `static` fonction membre est déclarée avec un spécificateur de modèle de mémoire, tel que [const](../../cpp/const-cpp.md) ou [volatile](../../cpp/volatile-cpp.md), et ces modificateurs ne sont pas autorisés sur `static` fonctions membres.  
  
 L’exemple suivant génère l’erreur C2272 :  
  
```  
// C2272.cpp  
// compile with: /c  
class CMyClass {  
public:  
   static void func1() const volatile;   // C2272  func1 is static  
   void func2() const volatile;   // OK  
};  
```