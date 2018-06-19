---
title: Erreur du compilateur C2561 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8ece9a3d9347a5179844cbfca3425870c25e2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230901"
---
# <a name="compiler-error-c2561"></a>Erreur du compilateur C2561
'identificateur' : fonction doit retourner une valeur  
  
 La fonction a été déclarée comme retournant une valeur, mais la définition de fonction ne contient-elle pas un `return` instruction.  
  
 Cette erreur peut résulter d’un prototype de fonction incorrect :  
  
1.  Si la fonction ne retourne pas de valeur, déclarez la fonction avec le type de retour [void](../../cpp/void-cpp.md).  
  
2.  Vérifiez que toutes les branches possibles de la fonction retournent une valeur du type déclaré dans le prototype.  
  
3.  Les fonctions C++ contenant des routines d’assembly inline qui stockent la valeur de retour dans le `AX` register peut-être demander une instruction return. Copiez la valeur dans `AX` dans une variable temporaire et retournez cette variable à partir de la fonction.  
  
 L’exemple suivant génère l’erreur C2561 :  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```