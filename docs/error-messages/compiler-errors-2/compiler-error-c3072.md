---
title: Erreur du compilateur C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 34b5cff9191814b2a16a42d9e234bab09f29c117
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490023"
---
# <a name="compiler-error-c3072"></a>Erreur du compilateur C3072

l’opérateur 'opérateur' ne peut pas être appliqué à une instance d’une classe ref

Utilisez l’unaire '`operator` ' opérateur pour convertir une instance d’une classe ref en un type de handle

Un type CLR exige des opérateurs CLR, pas les opérateurs natives (ou standards).  Pour plus d’informations, consultez [opérateur de référence de suivi](../../windows/tracking-reference-operator-cpp-component-extensions.md).

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