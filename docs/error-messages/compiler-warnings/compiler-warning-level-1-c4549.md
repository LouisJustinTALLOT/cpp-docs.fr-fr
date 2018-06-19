---
title: Compilateur avertissement (niveau 1) C4549 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4549
dev_langs:
- C++
helpviewer_keywords:
- C4549
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a31a2aec4753cf0cd800ca22ea1e997a5929bf3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284327"
---
# <a name="compiler-warning-level-1-c4549"></a>Avertissement du compilateur (niveau 1) C4549
'opérateur' : opérateur avant la virgule n’a pas d’effet ; souhaitiez-vous 'opérateur' ?  
  
 Le compilateur a détecté une expression avec virgules incorrecte.  
  
 Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 L’exemple suivant génère l’erreur C4549 :  
  
```  
// C4549.cpp  
// compile with: /W1  
#pragma warning (default : 4549)  
  
int main() {  
   int i = 0, k = 0;  
  
   if ( i == 0, k )   // C4549  
   // try the following line instead  
   // if ( i == 0 )  
      i++;  
}  
```