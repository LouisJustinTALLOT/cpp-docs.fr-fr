---
title: 'Comment : intercepter des exceptions en code natif levées à partir de MSIL'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: c3afa29d8c9bee1c1f1cc2fd1869d108c08a249b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246687"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Comment : intercepter des exceptions en code natif levées à partir de MSIL

En code natif, vous pouvez intercepter C++ l’exception native à partir de MSIL.  Vous pouvez intercepter les exceptions CLR avec `__try` et `__except`.

Pour plus d’informations, consultez [gestion structurée des exceptionsC++(C/)](../cpp/structured-exception-handling-c-cpp.md) et [meilleures pratiques modernes C++ pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant définit un module avec deux fonctions, une qui lève une exception native et une autre qui lève une exception MSIL.

```
// catch_MSIL_in_native.cpp
// compile with: /clr /c
void Test() {
   throw ("error");
}

void Test2() {
   throw (gcnew System::Exception("error2"));
}
```

## <a name="example"></a>Exemple

L’exemple suivant définit un module qui intercepte une exception native et MSIL.

```
// catch_MSIL_in_native_2.cpp
// compile with: /clr catch_MSIL_in_native.obj
#include <iostream>
using namespace std;
void Test();
void Test2();

void Func() {
   // catch any exception from MSIL
   // should not catch Visual C++ exceptions like this
   // runtime may not destroy the object thrown
   __try {
      Test2();
   }
   __except(1) {
      cout << "caught an exception" << endl;
   }

}

int main() {
   // catch native C++ exception from MSIL
   try {
      Test();
   }
   catch(char * S) {
      cout << S << endl;
   }
   Func();
}
```

```Output
error
caught an exception
```

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../extensions/exception-handling-cpp-component-extensions.md)
