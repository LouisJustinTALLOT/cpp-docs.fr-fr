---
title: Erreur du compilateur C2400 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2400
dev_langs:
- C++
helpviewer_keywords:
- C2400
ms.assetid: 1ba441ee-73f9-42a5-bfe9-fbeab93808eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b6eb9ea25428138297cf85fe71e9c84b2364199
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225474"
---
# <a name="compiler-error-c2400"></a>Erreur du compilateur C2400
Erreur de syntaxe d’assembleur inline dans 'contexte' ; 'jeton' rencontré  
  
 Le jeton a provoqué une erreur de syntaxe dans le contexte spécifié.  
  
 L’exemple suivant génère C2400 :  
  
```  
// C2400.cpp  
// processor: x86  
int main() {  
   __asm {  
      heh ax,bx;   // C2400, heh is not a valid x86 instruction  
      mov ax,bx;   // OK  
   }  
}  
```