---
title: Erreur du compilateur C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 0dfe9f88fcdfda1325150d480670777a4d42d896
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758630"
---
# <a name="compiler-error-c2537"></a>Erreur du compilateur C2537

'specifier' : spécification de liaison non conforme

Causes possibles :

1. Le spécificateur de liaison n’est pas pris en charge. Seul le spécificateur de liaison « C » est pris en charge.

1. La liaison « C » est spécifiée pour plusieurs fonctions dans un ensemble de fonctions surchargées. Cela n'est pas autorisé.

L’exemple suivant génère l’C2537 :

```cpp
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```
