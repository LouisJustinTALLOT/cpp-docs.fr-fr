---
title: Compilateur avertissement (niveau 1) C4731 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75117b34e63694cfa6aeec97abf178ff8e61a7da
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086481"
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