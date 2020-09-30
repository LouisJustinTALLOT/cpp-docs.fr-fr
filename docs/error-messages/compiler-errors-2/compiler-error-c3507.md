---
title: Erreur du compilateur C3507
ms.date: 11/04/2016
f1_keywords:
- C3507
helpviewer_keywords:
- C3507
ms.assetid: 75f89767-f6f9-40f6-9820-81a49e09abdf
ms.openlocfilehash: a38efcc0d74bbea0e0bf767cb9e5a11561ab4fb8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507127"
---
# <a name="compiler-error-c3507"></a>Erreur du compilateur C3507

un ProgID ne peut pas comporter plus de 39 caractères’ID'; et ne contiennent pas de signes de ponctuation séparés de'. '; ni commencer par un chiffre

L’attribut [ProgID](../../windows/attributes/progid.md) a des restrictions sur les valeurs qu’il peut prendre.

L’exemple suivant génère l’C3507 :

```cpp
// C3507.cpp
[module(name="x")];
[
coclass,
progid("0123456789012345678901234567890123456789"),
uuid("00000000-0000-0000-0000-000000000001") // C3507 expected
]
struct CMyStruct {
};
int main() {
}
```
