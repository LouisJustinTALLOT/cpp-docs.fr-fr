---
title: Erreur du compilateur C2197 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2197
dev_langs:
- C++
helpviewer_keywords:
- C2197
ms.assetid: 6dd5a6ec-bc80-41b9-a4ac-46f80eaca42d
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: aefc6ca5d7cc5fc15cd7c6c4996be2a4979f6bd7
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2197"></a>Erreur du compilateur C2197
'function' : trop d’arguments pour un appel  
  
 Le compilateur a détecté un nombre trop élevé de paramètres pour un appel à la fonction ou une déclaration de fonction incorrecte.  
  
 L’exemple suivant génère l’erreur C2197 :  
  
```  
// C2197.c  
// compile with: /Za /c  
void func( int );  
int main() {  
   func( 1, 2 );   // C2197 two actual parameters  
   func( 2 );   // OK  
}  
```
