---
title: Erreur du compilateur C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 2b76fa91d739e9cc89251aaf56aa9b196e62a68d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777127"
---
# <a name="compiler-error-c3072"></a>Erreur du compilateur C3072

l’opérateur 'opérateur' ne peut pas être appliqué à une instance d’une classe ref

Utilisez l’unaire '`operator` ' opérateur pour convertir une instance d’une classe ref en un type de handle

Un type CLR exige des opérateurs CLR, pas les opérateurs natives (ou standards).  Pour plus d’informations, consultez [opérateur de référence de suivi](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3072.

```
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```