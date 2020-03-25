---
title: Avertissement du compilateur (niveau 1) C4293
ms.date: 11/04/2016
f1_keywords:
- C4293
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
ms.openlocfilehash: 6f224996904c583001496e04c020de97bc932738
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175686"
---
# <a name="compiler-warning-level-1-c4293"></a>Avertissement du compilateur (niveau 1) C4293

'opérateur' : nombre de décalages négatif ou trop important, comportement non défini

Si un nombre de décalages est négatif ou trop grand, le comportement de l’image résultante n’est pas défini.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4293 :

```cpp
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi) {

   return (hi << 32) | lo;   // C4293

   // try the following line instead
   // return ( (unsigned __int64)hi << 32) | lo;
}
```
