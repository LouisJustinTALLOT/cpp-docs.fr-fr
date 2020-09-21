---
title: Erreur du compilateur C2725
ms.date: 11/04/2016
f1_keywords:
- C2725
helpviewer_keywords:
- C2725
ms.assetid: 13cd5b1b-e906-4cd8-9b2b-510d587c665a
ms.openlocfilehash: b2e8c6a2d3368e2f7fc1277e3bf727848da50881
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741395"
---
# <a name="compiler-error-c2725"></a>Erreur du compilateur C2725

'exception' : impossible de lever ou d'intercepter un objet managé ou WinRT par valeur ou référence

Le type d'une exception managée ou WinRT était incorrect.

## <a name="examples"></a>Exemples

L'exemple suivant génère l'erreur C2725 et montre comment la corriger :

```cpp
// C2725.cpp
// compile with: /clr
ref class R {
public:
   int i;
};

int main() {
   R % r1 = *gcnew R;
   throw r1;   // C2725

   R ^ r2 = gcnew R;
   throw r2;   // OK
}
```

L'exemple suivant génère l'erreur C2725 et montre comment la corriger :

```cpp
// C2725b.cpp
// compile with: /clr
using namespace System;
int main() {
   try {}
   catch( System::Exception%) {}   // C2725
   // try the following line instead
   // catch( System::Exception ^e) {}
}
```
