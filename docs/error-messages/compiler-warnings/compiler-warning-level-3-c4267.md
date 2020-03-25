---
title: Avertissement du compilateur (niveau 3) C4267
ms.date: 11/04/2016
f1_keywords:
- C4267
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
ms.openlocfilehash: 2ae4b53dfa5050e178bf5ddd366e97c4ff773dd0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161514"
---
# <a name="compiler-warning-level-3-c4267"></a>Avertissement du compilateur (niveau 3) C4267

'var' : conversion de 'size_t' en 'type', perte possible de données

Le compilateur a détecté une conversion de `size_t` en un type plus petit.

Pour résoudre cet avertissement, utilisez `size_t` à la place de `type`. Vous pouvez également utiliser un type intégral au moins aussi grand que `size_t`.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C4267.

```cpp
// C4267.cpp
// compile by using: cl /W4 C4267.cpp
void Func1(short) {}
void Func2(int) {}
void Func3(long) {}
void Func4(size_t) {}

int main() {
   size_t bufferSize = 10;
   Func1(bufferSize);   // C4267 for all platforms
   Func2(bufferSize);   // C4267 only for 64-bit platforms
   Func3(bufferSize);   // C4267 only for 64-bit platforms
   Func4(bufferSize);   // OK for all platforms
}
```
