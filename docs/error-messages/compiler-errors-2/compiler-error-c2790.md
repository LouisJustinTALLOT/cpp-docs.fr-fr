---
title: Erreur du compilateur C2790 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2790
dev_langs:
- C++
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 11ea7285d20808f16f2588d50caebe99429c8da0
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2790"></a>Erreur du compilateur C2790
'super' : ce mot clé peut être utilisé uniquement dans le corps de la fonction membre de classe  
  
 Ce message d’erreur apparaît si l’utilisateur tente utilise le mot clé [super](../../cpp/super.md) en dehors du contexte d’une fonction membre.  
  
 L’exemple suivant génère l’erreur C2790 :  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```
