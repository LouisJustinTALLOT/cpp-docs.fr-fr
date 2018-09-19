---
title: Avertissement du compilateur C4972 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4972
dev_langs:
- C++
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e083a91397ee00d8e74b5ee4549a192bba62b643
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037773"
---
# <a name="compiler-warning-c4972"></a>Avertissement du compilateur C4972

La modification ou le traitement direct du résultat d'une conversion unboxing comme lvalue est non vérifiable

Quand vous procédez au déréférencement d’un handle en un type valeur, (également appelé « conversion unboxing »), puis effectuez une assignation à celui-ci, le résultat est non vérifiable.

Pour plus d’informations, consultez [Boxing](../../windows/boxing-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4972.

```
// C4972.cpp
// compile with: /clr:safe
using namespace System;
ref struct R {
   int ^ p;   // a value type
};

int main() {
   R ^ r = gcnew R;
   *(r->p) = 10;   // C4972

   // OK
   r->p = 10;
   Console::WriteLine( r->p );
   Console::WriteLine( *(r->p) );
}
```