---
title: 'Comment : intercepter des Exceptions en Code natif levées à partir de MSIL | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f7022bffa7dd5a8524c614760fa2a36b2884b973
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379461"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Comment : intercepter des exceptions en code natif levées à partir de MSIL

En code natif, vous pouvez intercepter des exceptions C++ native à partir de MSIL.  Vous pouvez intercepter des exceptions CLR avec `__try` et `__except`.

Pour plus d’informations, consultez [structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md) et [gestion des exceptions C++](../cpp/cpp-exception-handling.md).

## <a name="example"></a>Exemple

L’exemple suivant définit un module avec deux fonctions, qui lève une exception native et l’autre qui lève une exception de MSIL.

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

L’exemple suivant définit un module qui intercepte une exception de MSIL et les natif.

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

[Gestion des exceptions](../windows/exception-handling-cpp-component-extensions.md)