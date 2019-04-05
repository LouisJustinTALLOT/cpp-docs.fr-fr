---
title: Avertissement du compilateur (niveau 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: e32509e4d32eef4f53b8d43a7db769844f1182c7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781547"
---
# <a name="compiler-warning-level-1-c4572"></a>Avertissement du compilateur (niveau 1) C4572

L’attribut [ParamArray] est déconseillé sous/CLR, utilisez '...' à la place

Un style pour la spécification d’une liste d’arguments variable obsolète a été utilisé. Lors de la compilation pour le CLR, utilisez la syntaxe de points de suspension à la place de <xref:System.ParamArrayAttribute>. Pour plus d’informations, consultez [listes d’arguments variables (...) (C + C++ / CLI) ](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4572.

```
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```