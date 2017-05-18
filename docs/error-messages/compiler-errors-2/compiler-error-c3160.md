---
title: Erreur du compilateur C3160 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3160
dev_langs:
- C++
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: a0e92dc32d7d71d8e544a2877760727160494592
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3160"></a>Erreur du compilateur C3160
'pointeur' :  les données membres d'une classe managée ou WinRT ne peuvent pas avoir ce type  
  
 Les pointeurs intérieurs de garbage collection peuvent pointer vers l’intérieur d’une classe managée ou WinRT. Comme ils sont plus lents que les pointeurs d'objet entier et nécessitent un traitement spécial par le récupérateur de mémoire, vous ne pouvez pas déclarer les pointeurs managés intérieurs en tant que membres d'une classe.  
  
 L'exemple suivant génère l'erreur C3160 :  
  
```  
// C3160.cpp  
// compile with: /clr  
ref struct A {  
   // cannot create interior pointers inside a class  
   interior_ptr<int> pg;   // C3160  
   int g;   // OK  
   int* pg2;   // OK  
};  
  
int main() {  
   interior_ptr<int> pg2;   // OK  
}  
```  

