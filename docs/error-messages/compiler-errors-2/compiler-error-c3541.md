---
title: Erreur du compilateur C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 1308ff91bcebabc5495b015321494f3457cf2d1e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761502"
---
# <a name="compiler-error-c3541"></a>Erreur du compilateur C3541

'type' : typeid ne peut pas être appliqué à un type contenant’auto'

Impossible d’appliquer l’opérateur [typeid](../../extensions/typeid-cpp-component-extensions.md) au type indiqué, car il contient le spécificateur `auto`.

## <a name="example"></a>Exemple

L’exemple suivant génère C3541.

```cpp
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[auto, mot clé](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)
