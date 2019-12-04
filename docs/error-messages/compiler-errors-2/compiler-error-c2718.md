---
title: Erreur du compilateur C2718
ms.date: 11/04/2016
f1_keywords:
- C2718
helpviewer_keywords:
- C2718
ms.assetid: 78cc71f8-c142-46fc-9aed-970635d74f0c
ms.openlocfilehash: ecfb68856e63eaf3f60e93a79bac17c66d1af1fc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760515"
---
# <a name="compiler-error-c2718"></a>Erreur du compilateur C2718

'paramètre' : le paramètre réel avec __declspec (align (' # ')) ne sera pas aligné

Le modificateur [align](../../cpp/align-cpp.md) `__declspec` n’est pas autorisé sur les paramètres de fonction.

L’exemple suivant génère l’C2718 :

```cpp
// C2718.cpp
typedef struct __declspec(align(32)) AlignedStruct  {
   int i;
} AlignedStruct;

void f2(int i, ...);

void f4() {
   AlignedStruct as;

   f2(0, as);   // C2718, actual parameter is aligned
}
```
