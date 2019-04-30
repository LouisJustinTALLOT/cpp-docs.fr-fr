---
title: Compilateur avertissement (niveau 3) C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 5f895a231c8b32d76e4ccd3c15ffae5717d8017f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402045"
---
# <a name="compiler-warning-level-3-c4316"></a>Compilateur avertissement (niveau 3) C4316

Objet alloué sur le tas ne soit pas aligné pour ce type.

Un objet sur-aligné alloué à l’aide de `operator new` ne peut pas avoir l’alignement spécifié. Substituer [opérateur new](../../c-runtime-library/operator-new-crt.md) et [opérateur delete](../../c-runtime-library/operator-delete-crt.md) pour les types sur-alignés afin qu’ils utilisent les routines d’allocation alignée — par exemple, [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) et [_aligned_free](../../c-runtime-library/reference/aligned-free.md). L’exemple suivant génère C4316 :

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```