---
title: Erreur du compilateur C2748
ms.date: 11/04/2016
f1_keywords:
- C2748
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
ms.openlocfilehash: e43defbf28c76dadcc7921ca76778413c41490a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759631"
---
# <a name="compiler-error-c2748"></a>Erreur du compilateur C2748

La création de tableau managé ou WinRT doit posséder une taille de tableau ou un initialiseur de tableau

Un tableau managé ou WinRT était incorrect. Pour plus d'informations, consultez [tableau](../../extensions/arrays-cpp-component-extensions.md).

L'exemple suivant génère l'erreur C2748 et montre comment la corriger :

```cpp
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```
