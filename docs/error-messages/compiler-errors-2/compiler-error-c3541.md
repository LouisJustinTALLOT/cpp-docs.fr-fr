---
title: Erreur du compilateur C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 2d6179657462325a30de0c4548becff4b4cf86c9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508067"
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

[Auto, mot clé](../../cpp/auto-cpp.md)<br/>
[/Zc : auto (déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[TypeId](../../extensions/typeid-cpp-component-extensions.md)
