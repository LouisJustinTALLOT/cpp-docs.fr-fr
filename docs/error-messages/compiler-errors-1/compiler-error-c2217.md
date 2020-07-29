---
title: Erreur du compilateur C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: b033d95b127a45451a776cdc336ea7d2649d3716
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209745"
---
# <a name="compiler-error-c2217"></a>Erreur du compilateur C2217

'attribute1 'requiert’attribute2 '

Le premier attribut de fonction requiert le deuxième attribut.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Fonction Interrupt ( `__interrupt` ) déclarée comme `near` . Les fonctions d’interruption doivent être `far` .

1. Fonction d’interruption déclarée avec **`__stdcall`** , ou **`__fastcall`** . Les fonctions d’interruption doivent utiliser des conventions d’appel C.

## <a name="example"></a>Exemple

C2217 peut également se produire si vous tentez de lier un délégué à une fonction CLR qui accepte un nombre variable d’arguments. Si la fonction a également une surcharge de tableau param, utilisez-la à la place. L’exemple suivant génère l’C2217.

```cpp
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```
