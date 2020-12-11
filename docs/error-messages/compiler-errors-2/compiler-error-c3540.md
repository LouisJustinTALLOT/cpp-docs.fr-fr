---
description: 'En savoir plus sur : erreur du compilateur C3540'
title: Erreur du compilateur C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 85106061b2631d3a392b05a50c49f24566cdd4cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112451"
---
# <a name="compiler-error-c3540"></a>Erreur du compilateur C3540

'type' : sizeof ne peut pas être appliqué à un type contenant’auto'

L’opérateur [sizeof](../../cpp/sizeof-operator.md) ne peut pas être appliqué au type indiqué, car il contient le **`auto`** spécificateur.

## <a name="example"></a>Exemple

L’exemple suivant génère C3540.

```cpp
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Auto, mot clé](../../cpp/auto-cpp.md)<br/>
[/Zc : auto (déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof (opérateur)](../../cpp/sizeof-operator.md)
