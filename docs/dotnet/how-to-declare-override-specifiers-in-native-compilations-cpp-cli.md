---
title: 'Procédure : Déclarer des spécificateurs de substitution (C++ / c++ / CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: db74ef226242ec8f4f70f2769fbc8ba102a808c8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777179"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Procédure : Déclarer des spécificateurs de substitution dans les Compilations natives (C++ / c++ / CLI)

[sealed](../extensions/sealed-cpp-component-extensions.md), [abstraite](../extensions/abstract-cpp-component-extensions.md), et [remplacer](../extensions/override-cpp-component-extensions.md) sont disponibles dans les compilations qui n’utilisent pas **/ZW** ou [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
>  La norme ISO C ++ 11 Standard langue a la [remplacer](../cpp/override-specifier.md) identificateur et le [finale](../cpp/final-specifier.md) identificateur et les deux sont pris en charge dans Visual Studio, cliquez `final` au lieu de `sealed` dans le code est destiné à être compilé en tant que natif uniquement.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre que `sealed` est valide dans les compilations natives.

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

Cet exemple montre que `abstract` est valide dans les compilations natives.

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
