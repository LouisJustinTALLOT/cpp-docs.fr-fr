---
title: Avertissement du compilateur (niveau 1) C4817
ms.date: 11/04/2016
f1_keywords:
- C4817
helpviewer_keywords:
- C4817
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
ms.openlocfilehash: d729bdbf0f8379b2ffde80567ae4307d0a8dacd7
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052323"
---
# <a name="compiler-warning-level-1-c4817"></a>Avertissement du compilateur (niveau 1) C4817

'membre' : utilisation non conforme de '.' pour accéder à ce membre ; compilateur remplacé par '->'

Le mauvais opérateur d’accès aux membres a été utilisé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4817 :

```cpp
// C4817.cpp
// compile with: /clr /W1
using namespace System;
int main() {
   array<Int32> ^ a = gcnew array<Int32>(100);
   Console::WriteLine( a.Length );   // C4817
   Console::WriteLine( a->Length );   // OK
}
```
