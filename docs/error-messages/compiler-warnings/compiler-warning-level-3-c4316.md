---
title: Avertissement du compilateur (niveau 3) C4316
description: Description de l’avertissement du compilateur C++ C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 3cb512aa9b851f3b3b26f7a50854a4d887087e81
ms.sourcegitcommit: 8caaf5e00aeb727741a273aecafa15de293426cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91806553"
---
# <a name="compiler-warning-level-3-c4316"></a>Avertissement du compilateur (niveau 3) C4316

L’objet alloué sur le tas n’est peut-être pas aligné pour ce type.

Un objet sur-aligné alloué à l’aide de `operator new` peut ne pas avoir l’alignement spécifié. Substituez [operator new](../../c-runtime-library/new-operator-crt.md) et l' [opérateur delete](../../c-runtime-library/delete-operator-crt.md) pour les types sur-alignés afin qu’ils utilisent les routines d’allocation alignées, par exemple [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) et [_aligned_free](../../c-runtime-library/reference/aligned-free.md). L’exemple suivant génère l’C4316 :

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```
