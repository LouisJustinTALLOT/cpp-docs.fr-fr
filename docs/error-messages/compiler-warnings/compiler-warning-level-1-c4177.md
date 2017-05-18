---
title: Compilateur avertissement (niveau 1) C4177 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4177
dev_langs:
- C++
helpviewer_keywords:
- C4177
ms.assetid: 2b05a5b3-696e-4f21-818e-227b9335e748
caps.latest.revision: 7
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
ms.openlocfilehash: 2ec8666514f1118a5d14d74d42f76df033a6b65f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4177"></a>Avertissement du compilateur (niveau 1) C4177
\#pragma pragma doit être dans une portée globale  
  
 Le [pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) pragma ne doit pas être utilisé dans une portée locale. Le **pragma** n’est pas valide si une portée globale est rencontrée après la portée actuelle.  
  
 L’exemple suivant génère l’avertissement C4177 :  
  
```  
// C4177.cpp  
// compile with: /W1  
// #pragma bss_seg("global")   // OK  
  
int main() {  
   #pragma bss_seg("local")    // C4177  
}  
```
