---
title: Erreur du compilateur C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: d0c4f1b71ccd12ad39fb25ef3411d2fb46b89da7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665814"
---
# <a name="compiler-error-c3540"></a>Erreur du compilateur C3540

'type' : Impossible d’appliquer sizeof à un type contenant 'auto'

Le [sizeof](../../cpp/sizeof-operator.md) opérateur ne peut pas être appliqué au type indiqué, car elle contient le `auto` spécificateur.

## <a name="example"></a>Exemple

L’exemple suivant donne C3540.

```
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

[auto, mot clé](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof, opérateur](../../cpp/sizeof-operator.md)