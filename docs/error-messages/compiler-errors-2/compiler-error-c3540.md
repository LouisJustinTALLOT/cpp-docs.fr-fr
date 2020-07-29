---
title: Erreur du compilateur C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: a041961e8a91832be67d8def8f2a6a3ef70906d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223393"
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

[Auto, mot clé](../../cpp/auto-keyword.md)<br/>
[/Zc : auto (déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof (opérateur)](../../cpp/sizeof-operator.md)
