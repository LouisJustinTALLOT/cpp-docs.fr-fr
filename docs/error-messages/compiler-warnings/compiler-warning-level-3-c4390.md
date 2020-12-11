---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4390'
title: Avertissement du compilateur (niveau 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 8067d4beae44e098085122968a227f6ff8bc8b4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160439"
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
