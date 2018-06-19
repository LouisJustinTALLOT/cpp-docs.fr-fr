---
title: Compilateur avertissement (niveau 1) C4177 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4177
dev_langs:
- C++
helpviewer_keywords:
- C4177
ms.assetid: 2b05a5b3-696e-4f21-818e-227b9335e748
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae001b593d965ead0c834793dbbeee3972a5b0bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278605"
---
# <a name="compiler-warning-level-1-c4177"></a>Avertissement du compilateur (niveau 1) C4177
\#pragma pragma doit être dans une portée globale  
  
 Le pragma [pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) ne doit pas être utilisé dans une portée locale. Le **pragma** n’est pas valide si une portée globale est rencontrée après la portée actuelle.  
  
 L’exemple suivant génère l’avertissement C4177 :  
  
```  
// C4177.cpp  
// compile with: /W1  
// #pragma bss_seg("global")   // OK  
  
int main() {  
   #pragma bss_seg("local")    // C4177  
}  
```