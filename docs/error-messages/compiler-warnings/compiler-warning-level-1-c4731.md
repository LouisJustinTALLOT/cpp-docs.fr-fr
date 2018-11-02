---
title: Avertissement du compilateur (niveau 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: af091d1d35fff955afcc5af3da48b80416e79f36
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485630"
---
# <a name="compiler-warning-level-1-c4731"></a>Avertissement du compilateur (niveau 1) C4731

'pointeur' : Registre de pointeur 'Registre' modifié par le code assembleur inline frame

Un Registre de pointeur de frame a été modifié. Vous devez enregistrer et restaurer le Registre dans votre assembly bloc ou frame variable inline (locale ou un paramètre, selon le Registre modifié), ou votre code peut ne pas fonctionne correctement.

L’exemple suivant génère l’erreur C4731 :

```
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

EBP est le pointeur de frame (FPO n’est pas autorisée) et il est en cours de modification. Lorsque `p` est ultérieur référencé, il est référencé relatif à `EBP`. Mais `EBP` a été remplacé par le code, afin que le programme ne fonctionnera pas correctement et peut même subir une défaillance.