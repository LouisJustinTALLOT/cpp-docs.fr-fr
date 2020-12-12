---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4731'
title: Avertissement du compilateur (niveau 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: d2041936d7d3c4b7189f57d57ffb1c9f226ea933
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228649"
---
# <a name="compiler-warning-level-1-c4731"></a>Avertissement du compilateur (niveau 1) C4731

'pointeur' : Registre de pointeur de frame’Register’modifié par le code assembleur inline

Un registre de pointeur de frame a été modifié. Vous devez enregistrer et restaurer le registre dans votre variable frame ou bloc d’assembly inline (local ou paramètre, selon le registre modifié) ou votre code risque de ne pas fonctionner correctement.

L’exemple suivant génère l’C4731 :

```cpp
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

EBP est le pointeur de frame (FPO n’est pas autorisé) et il est en cours de modification. Lorsque `p` est référencé ultérieurement, il est référencé par rapport à `EBP` . Mais `EBP` a été remplacé par le code, de sorte que le programme ne fonctionnera pas correctement et peut même être défaillant.
