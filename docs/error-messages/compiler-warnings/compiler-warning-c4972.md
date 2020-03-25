---
title: Avertissement du compilateur C4972
ms.date: 11/04/2016
f1_keywords:
- C4972
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
ms.openlocfilehash: ca80e847174bbe225acaf8631c646d8c6a94c50a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164831"
---
# <a name="compiler-warning-c4972"></a>Avertissement du compilateur C4972

La modification ou le traitement direct du résultat d'une conversion unboxing comme lvalue est non vérifiable

Quand vous procédez au déréférencement d’un handle en un type valeur, (également appelé « conversion unboxing »), puis effectuez une assignation à celui-ci, le résultat est non vérifiable.

Pour plus d'informations, consultez [Boxing](../../extensions/boxing-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4972.

```cpp
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
