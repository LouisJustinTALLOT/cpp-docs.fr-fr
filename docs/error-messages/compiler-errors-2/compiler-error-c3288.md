---
title: Erreur du compilateur C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: 30a88d1047f8395fc8e3042cf2a1da88e6e5c2d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608414"
---
# <a name="compiler-error-c3288"></a>Erreur du compilateur C3288

'type' : déréférencement non conforme d’un type de handle

Le compilateur a détecté un déréférencement non conforme d’un type de handle. Vous pouvez déréférencer un type de handle et l’assigner à une référence. Pour plus d’informations, consultez [opérateur de référence de suivi](../../windows/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3288.

```
// C3288.cpp
// compile with: /clr
ref class R {};
int main() {
   *(System::Object^) nullptr;   // C3288

// OK
   (System::Object^) nullptr;   // OK
   R^ r;
   R% pr = *r;
}
```