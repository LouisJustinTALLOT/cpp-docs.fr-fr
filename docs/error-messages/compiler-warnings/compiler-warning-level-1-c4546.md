---
title: Compilateur avertissement (niveau 1) C4546 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4546
dev_langs:
- C++
helpviewer_keywords:
- C4546
ms.assetid: 071e1709-3841-46c1-8e71-96109cd22041
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a9feb3a63c6aab12a7c3afdbaa5166c0926672b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278299"
---
# <a name="compiler-warning-level-1-c4546"></a>Avertissement du compilateur (niveau 1) C4546
l’appel de fonction avant la virgule n’a pas de liste d’arguments  
  
 Le compilateur a détecté une expression avec virgules incorrecte.  
  
 Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4546 :  
  
```  
// C4546.cpp  
// compile with: /W1  
#pragma warning (default : 4546)  
void f(int i) {  
   i++;  
}  
  
int main() {  
   int i = 0, k = 0;  
  
   if ( f, k )   // C4546  
   // try the following line instead  
   // if ( f(i), k )  
      i++;  
}  
```