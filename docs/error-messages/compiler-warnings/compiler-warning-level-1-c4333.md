---
title: Avertissement du compilateur (niveau 1) C4333
ms.date: 11/04/2016
f1_keywords:
- C4333
helpviewer_keywords:
- C4333
ms.assetid: d3763c52-6110-4da0-84db-5264e3f3f166
ms.openlocfilehash: b0f87b5d839dcfbb577af567a1a51a95daf716f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406598"
---
# <a name="compiler-warning-level-1-c4333"></a>Avertissement du compilateur (niveau 1) C4333

'opérateur' : décalage vers la droite trop important, perte de données

Une opération de décalage vers la droite était trop important.  Tous les bits significatifs sont éliminés et le résultat sera toujours égal à zéro.

## <a name="example"></a>Exemple

L’exemple suivant génère C4333.

```
// C4333.cpp
// compile with: /c /W1
unsigned shift8 (unsigned char c) {
   return c >> 8;   // C4333

   // try the following line instead
   // return c >> 4;   // OK
}
```