---
title: Erreur du compilateur C2496
ms.date: 11/04/2016
f1_keywords:
- C2496
helpviewer_keywords:
- C2496
ms.assetid: 9a25237d-5bbb-4112-98f3-29cd99d3f89f
ms.openlocfilehash: 9236876e636e88f193d32ef2e33a817fa52e1bd2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757005"
---
# <a name="compiler-error-c2496"></a>Erreur du compilateur C2496

'identificateur' : 'selectany’ne peut s’appliquer qu’aux éléments de données avec une liaison externe

L’attribut [selectany](../../cpp/selectany.md) peut être appliqué uniquement aux éléments de données globaux et visibles en externe.

L’exemple suivant génère l’C2496 :

```cpp
// C2496.cpp
// compile with: /c
__declspec(selectany) int x1 = 1;
const __declspec(selectany) int x2 = 2;   // C2496
static __declspec(selectany) int x6 = 6;   // C2496

extern const __declspec(selectany) int x3 = 3;

__declspec(selectany) int x4;

// dynamic initialization of x5
int f();
__declspec(selectany) int x5 = f();

extern const int x7;
// OK - redeclaration of x7 that is extern
const __declspec(selectany) int x7 = 7;
```
