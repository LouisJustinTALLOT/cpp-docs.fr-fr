---
title: Erreur du compilateur C2213
ms.date: 11/04/2016
f1_keywords:
- C2213
helpviewer_keywords:
- C2213
ms.assetid: ff012278-7f3b-4d49-aaed-2349756f6225
ms.openlocfilehash: d4511098d01ae051ec154bac47ef0b43e1ac60ac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221274"
---
# <a name="compiler-error-c2213"></a>Erreur du compilateur C2213

'modificateur' : argument non conforme pour __based

La modification de l’argument **`__based`** n’est pas valide.

L’exemple suivant génère l’C2213 :

```cpp
// C2213.cpp
// compile with: /c
int i;
int *j;
char __based(i) *p;   // C2213
char __based(j) *p2;   // OK
```
