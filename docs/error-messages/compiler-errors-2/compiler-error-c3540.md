---
title: Erreur du compilateur C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 57e4145557272f76a890a356c79982346cd74d7e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345479"
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