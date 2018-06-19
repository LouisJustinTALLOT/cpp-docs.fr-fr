---
title: Erreur du compilateur C2362 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2362
dev_langs:
- C++
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53b0b77930acba6ecf2d0f3c6748ba52e9b28e0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222174"
---
# <a name="compiler-error-c2362"></a>Erreur du compilateur C2362
l’initialisation de 'identificateur' est ignorée par 'étiquette goto'  
  
 Lors de la compilation avec [/Za](../../build/reference/za-ze-disable-language-extensions.md), l’accès à l’étiquette empêche l’identificateur en cours d’initialisation.  
  
 Impossible d’aller au-delà d’une déclaration avec un initialiseur, sauf si la déclaration est englobée dans un bloc qui n’est pas entré ou la variable a déjà été initialisée.  
  
 L’exemple suivant génère l’erreur C2326 :  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 Solution possible :  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```