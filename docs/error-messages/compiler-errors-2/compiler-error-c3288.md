---
title: Erreur du compilateur C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: a7b87fdbd2e15906ebc0c669f0b9a74ebf97f0b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760177"
---
# <a name="compiler-error-c3288"></a>Erreur du compilateur C3288

'type' : déréférencement non conforme d’un type de handle

Le compilateur a détecté un déréférencement non conforme d’un type de handle. Vous pouvez déréférencer un type de handle et l’assigner à une référence. Pour plus d’informations, consultez [opérateur de référence de suivi](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3288.

```cpp
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
