---
title: Erreur du compilateur C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498187"
---
# <a name="compiler-error-c2464"></a>Erreur du compilateur C2464

'identificateur' : Impossible d’utiliser 'new' pour allouer une référence

Un identificateur de référence a été alloué avec le `new` opérateur. Références ne sont pas des objets de mémoire, par conséquent, `new` ne peut pas retourner un pointeur vers les. Utilisez la syntaxe de déclaration de variable standard pour déclarer une référence.

L’exemple suivant génère l’erreur C2464 :

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```