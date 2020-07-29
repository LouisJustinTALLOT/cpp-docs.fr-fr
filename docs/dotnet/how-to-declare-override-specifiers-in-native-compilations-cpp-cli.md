---
title: 'Comment : déclarer des spécificateurs de substitution (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: c5ed413f403fb12f116633c0e39f9e7b32b2e9f8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221326"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Comment : déclarer des spécificateurs de substitution dans les compilations natives (C++/CLI)

les compilations [sealed](../extensions/sealed-cpp-component-extensions.md), [abstract](../extensions/abstract-cpp-component-extensions.md)et [override](../extensions/override-cpp-component-extensions.md) sont disponibles dans les compilations qui n’utilisent pas **/ZW** ou [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> Le langage ISO C++ 11 standard a l’identificateur de [remplacement](../cpp/override-specifier.md) et l’identificateur [final](../cpp/final-specifier.md) , et les deux sont pris en charge dans Visual Studio use `final` au lieu de **`sealed`** dans le code qui est destiné à être compilé en mode natif uniquement.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre que **`sealed`** est valide dans les compilations natives.

### <a name="code"></a>Code

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre que `override` est valide dans les compilations natives.

### <a name="code"></a>Code

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Cet exemple montre que **`abstract`** est valide dans les compilations natives.

### <a name="code"></a>Code

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Voir aussi

[Spécificateurs de substitution](../extensions/override-specifiers-cpp-component-extensions.md)
