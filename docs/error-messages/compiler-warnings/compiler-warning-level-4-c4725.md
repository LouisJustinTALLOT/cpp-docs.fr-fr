---
title: Avertissement du compilateur (niveau 4) C4725
ms.date: 11/04/2016
f1_keywords:
- C4725
helpviewer_keywords:
- C4725
ms.assetid: effa0335-71c3-4b3b-8618-da4b9b46a95d
ms.openlocfilehash: c86d1a5351adf5ba29752613f2301a11fb1b93ce
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989523"
---
# <a name="compiler-warning-level-4-c4725"></a>Avertissement du compilateur (niveau 4) C4725

l'instruction peut manquer de précision sur certains processeurs Pentium

Votre code contient une instruction d’assembly inline qui risque de produire des résultats imprécis sur certains microprocesseurs Pentium.

L’exemple suivant génère l’avertissement C4725 :

```cpp
// C4725.cpp
// compile with: /W4
// processor: x86
double m32fp = 2.0003e-17;

void f() {
   __asm
   {
      FDIV m32fp   // C4725
   }
}

int main() {
}
```
