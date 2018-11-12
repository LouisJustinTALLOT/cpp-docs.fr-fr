---
title: Erreur du compilateur C2748
ms.date: 11/04/2016
f1_keywords:
- C2748
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
ms.openlocfilehash: a85ee151d9a4d62cc4b95248d669ff924365a95a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655635"
---
# <a name="compiler-error-c2748"></a>Erreur du compilateur C2748

La création de tableau managé ou WinRT doit posséder une taille de tableau ou un initialiseur de tableau

Un tableau managé ou WinRT était incorrect. Pour plus d'informations, consultez [tableau](../../windows/arrays-cpp-component-extensions.md).

L'exemple suivant génère l'erreur C2748 et montre comment la corriger :

```
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```