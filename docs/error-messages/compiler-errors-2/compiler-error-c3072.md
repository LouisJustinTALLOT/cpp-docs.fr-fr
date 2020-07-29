---
title: Erreur du compilateur C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: bcf2548fbe1182f7f6c4bd966ca6aa9ef9f10089
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212603"
---
# <a name="compiler-error-c3072"></a>Erreur du compilateur C3072

> l’opérateur'*Operator-Name*'ne peut pas être appliqué à une instance d’une classe ref

Utilisez l’opérateur unaire *-Name* pour convertir une instance d’une classe ref en type handle

Un type CLR requiert des opérateurs CLR, et non des opérateurs natifs (ou standard).  Pour plus d’informations, consultez [opérateur de référence de suivi](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3072.

```cpp
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
