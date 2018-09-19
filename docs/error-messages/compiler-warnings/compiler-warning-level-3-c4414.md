---
title: Compilateur avertissement (niveau 3) C4414 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd0868fea89cd868178956c0aba171ce6525bd75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043207"
---
# <a name="compiler-warning-level-3-c4414"></a>Avertissement du compilateur (niveau 3) C4414

'fonction' : saut de type short vers la fonction converti en near

Sauts courts génèrent une instruction compacte qui effectue un branchement vers une adresse dans une plage limitée à partir de l’instruction. L’instruction inclut un court offset qui représente la distance entre le saut et l’adresse cible, la définition de fonction. Lors de la liaison, une fonction peut être déplacées ou soumises aux optimisations au moment de lien qui amène la fonction à être déplacé hors de la plage est accessible à partir d’un offset court. Le compilateur doit générer un enregistrement spécial pour le saut, ce qui requiert une instruction jump NEAR ou bien. Le compilateur a effectué la conversion.

Par exemple, le code suivant génère l’erreur C4414 :

```
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```