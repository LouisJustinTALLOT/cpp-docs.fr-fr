---
title: Erreur du compilateur C2638 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2638
dev_langs:
- C++
helpviewer_keywords:
- C2638
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2917b1a947925b8bbd01f366f9540184b839a41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229994"
---
# <a name="compiler-error-c2638"></a>Erreur du compilateur C2638
'identificateur' : modificateur __based non conforme sur pointeur vers membre  
  
 Le `__based` modificateur ne peut pas être utilisé pour les pointeurs vers des membres.  
  
 L’exemple suivant génère l’erreur C2638 :  
  
```  
// C2638.cpp  
void *a;  
  
class C {  
public:  
   int i;  
   int j;  
   int func();  
};  
int __based (a) C::* cpi = &C::i;  // C2638  
int (__based (a) C::* cpf)() = &C::func; // c2638  
```