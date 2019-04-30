---
title: Avertissement du compilateur (niveau 3) C4267
ms.date: 11/04/2016
f1_keywords:
- C4267
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
ms.openlocfilehash: 31e5b9a9b8e7b25a0d54648ce808ff6266a27321
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402175"
---
# <a name="compiler-warning-level-3-c4267"></a>Avertissement du compilateur (niveau 3) C4267

'var' : conversion de 'size_t' en 'type', perte possible de données

Le compilateur a détecté une conversion de `size_t` en un type plus petit.

Pour résoudre cet avertissement, utilisez `size_t` à la place de `type`. Vous pouvez également utiliser un type intégral au moins aussi grand que `size_t`.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C4267.

```
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