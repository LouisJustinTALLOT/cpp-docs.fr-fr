---
title: Erreur du compilateur C2635 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2635
dev_langs:
- C++
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30916834b8adee0d1a80625624e80c5a860e57ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233988"
---
# <a name="compiler-error-c2635"></a>Erreur du compilateur C2635
Impossible de convertir un 'identificateur1 *' un ' identificateur2\*' ; conversion à partir de la classe de base virtuelle implicite  
  
 La conversion requiert un cast d’un `virtual` classe de base pour une classe dérivée, ce qui n’est pas autorisée.  
  
 L’exemple suivant génère C2635 :  
  
```  
// C2635.cpp  
class B {};  
class D : virtual public B {};  
class E : public B {};  
  
int main() {  
   B b;  
   D d;  
   E e;  
  
   D * pD = &d;  
   E * pE = &e;  
   pD = (D*)&b;   // C2635  
   pE = (E*)&b;   // OK  
}  
```