---
title: Avertissement du compilateur (niveau 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 63150f4ca801d3c377c7bc09b58a778bebf02b46
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198677"
---
# <a name="compiler-warning-level-3-c4390"></a>Avertissement du compilateur (niveau 3) C4390

'; ' : instruction contrôlée vide trouvée ; est-ce l’intention ?

Un point-virgule a été trouvé après une instruction de contrôle qui ne contient pas d’instructions.

Si vous recevez C4390 en raison d’une macro, vous devez utiliser le pragma [Warning](../../preprocessor/warning.md) pour désactiver C4390 dans le module contenant la macro.

L’exemple suivant génère l’C4390 :

```cpp
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```
