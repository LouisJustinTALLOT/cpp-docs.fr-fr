---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4572'
title: Avertissement du compilateur (niveau 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: ab447bc7ef5d702599b1583ae94ac0fa94d29a14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332232"
---
# <a name="compiler-warning-level-1-c4572"></a>Avertissement du compilateur (niveau 1) C4572

L’attribut [ParamArray] est déconseillé sous/CLR, utilisez'... ' qu'

Un style obsolète pour spécifier une liste d’arguments variable a été utilisé. Lors de la compilation pour le CLR, utilisez la syntaxe des points de suspension au lieu de <xref:System.ParamArrayAttribute> . Pour plus d’informations, consultez [listes d’arguments de variables (...) (C++/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4572.

```cpp
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```
