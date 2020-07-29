---
title: Erreur du compilateur C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 32926d0ef9343bad9ed73458e4d52d317b628109
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221040"
---
# <a name="compiler-error-c3541"></a>Erreur du compilateur C3541

'type' : typeid ne peut pas être appliqué à un type contenant’auto'

Impossible d’appliquer l’opérateur [typeid](../../extensions/typeid-cpp-component-extensions.md) au type indiqué, car il contient le **`auto`** spécificateur.

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

[Auto, mot clé](../../cpp/auto-keyword.md)<br/>
[/Zc : auto (déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[TypeId](../../extensions/typeid-cpp-component-extensions.md)
