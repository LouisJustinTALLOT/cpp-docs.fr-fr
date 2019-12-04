---
title: Erreur du compilateur C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 18cece8d9630aa93e867329acc7cefea30da3286
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759657"
---
# <a name="compiler-error-c2739"></a>Erreur du compilateur C2739

'nombre' : les dimensions de tableau managé ou WinRT explicites doivent être comprises entre 1 et 32

Une dimension de tableau n'était pas comprise entre 1 et 32.

L'exemple suivant génère l'erreur C2739 et montre comment la corriger :

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
