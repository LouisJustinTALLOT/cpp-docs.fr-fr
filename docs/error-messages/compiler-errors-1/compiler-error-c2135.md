---
title: Erreur du compilateur C2135 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2135
dev_langs:
- C++
helpviewer_keywords:
- C2135
ms.assetid: aa360d22-4f79-4de1-b384-93cadd10975f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 068dd861aed4a743ecf2b643b7722d4b35b929fc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2135"></a>Erreur du compilateur C2135
'opérateur de bits' : opération sur les champs de bits non conforme  
  
 L’opérateur address-of (`&`) ne peut pas être appliqué à un champ de bits.  
  
 L’exemple suivant génère l’erreur C2135 :  
  
```  
// C2135.cpp  
struct S {  
   int i : 1;  
};  
  
struct T {  
   int j;  
};  
int main() {  
   &S::i;   // C2135 address of a bit field  
   &T::j;   // OK  
}  
```
