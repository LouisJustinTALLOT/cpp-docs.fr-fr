---
title: Avertissement du compilateur (niveau 4) C4365
ms.date: 11/04/2016
f1_keywords:
- C4365
helpviewer_keywords:
- C4365
ms.assetid: af4b4191-bdfd-4dbb-8229-3ba4405df257
ms.openlocfilehash: a9be67c8148b85167d10cd53318f5ef3b41b1340
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990921"
---
# <a name="compiler-warning-level-4-c4365"></a>Avertissement du compilateur (niveau 4) C4365

'action' : conversion de’type_1 'en’type_2 ', incompatibilité signed/unsigned

Par exemple, vous avez essayé de convertir une valeur non signée en valeur signée.

C4365 est désactivé par défaut.  Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4365.

```cpp
// C4365.cpp
// compile with: /W4
#pragma warning(default:4365)

int f(int) { return 0; }
void Test(size_t i) {}

int main() {
   unsigned int n = 10;
   int o = 10;
   n++;
   f(n);   // C4365
   f(o);   // OK

   Test( -19 );   // C4365
}
```
