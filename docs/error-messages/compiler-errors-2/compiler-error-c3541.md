---
description: 'En savoir plus sur : erreur du compilateur C3541'
title: Erreur du compilateur C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: b579697de98556aa99077e43d28e6de828741fb5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315164"
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
