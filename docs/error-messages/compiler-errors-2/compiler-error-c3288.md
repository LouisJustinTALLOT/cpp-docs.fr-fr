---
title: Erreur du compilateur C3288 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3288
dev_langs:
- C++
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36412510efcedd765ad44b4aab61e6a7d64155fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079932"
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