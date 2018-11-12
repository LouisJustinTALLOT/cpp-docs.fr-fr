---
title: 'Comment : définir un constructeur d’interface statique (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 0617454e0957dccc7e28a5172a40273b5d93bede
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566385"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>Comment : définir un constructeur d’interface statique (C++/CLI)

Une interface peut avoir un constructeur statique, ce qui peut être utilisé pour initialiser les données membres statiques.  Un constructeur statique sera appelé au maximum une fois et est appelé avant la première fois qu’un membre d’interface statique est accessible.

## <a name="example"></a>Exemple

```
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>Voir aussi

[classe d’interface](../windows/interface-class-cpp-component-extensions.md)