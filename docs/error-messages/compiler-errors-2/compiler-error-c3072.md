---
description: 'En savoir plus sur : erreur du compilateur C3072'
title: Erreur du compilateur C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 02876a6983a47ce76f6e089bafde68af41034131
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320277"
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
