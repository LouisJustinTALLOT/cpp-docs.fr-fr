---
title: Erreur du compilateur C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: d076dabe0df91cefb90be5ec9e90f371331a51f1
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771005"
---
# <a name="compiler-error-c3288"></a>Erreur du compilateur C3288

'type' : déréférencement non conforme d’un type de handle

Le compilateur a détecté un déréférencement non conforme d’un type de handle. Vous pouvez déréférencer un type de handle et l’assigner à une référence. Pour plus d’informations, consultez [opérateur de référence de suivi](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

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